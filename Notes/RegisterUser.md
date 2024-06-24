# Express.js API Server with TypeScript and Mongoose 🚀

## Introduction

This guide will walk you through setting up and using an API server using Express.js with TypeScript and MongoDB using Mongoose.

## Objectives 🎯
When a user fills out the form and submits it, the frontend sends a POST request to the backend API (/api/users), which then creates a new user document in MongoDB. If successful, the backend responds with the created user object, which is then displayed as a success message on the frontend. If there's an error during user creation, an appropriate error message is shown.

## Getting Started - Backend Setup 🛠️

### Step 1 - Project Setup

Create a new directory for your project and set it up by running these commands in your terminal:

```
cd server
npm init -y
npm install express mongoose cors dotenv
npm install --save-dev typescript ts-node @types/node @types/express @types/mongoose @types/cors
```
### Step 2 - Project Structure
Ensure your project directory is structured as follows:

mkdir -p src/{controllers,models,routes} will create. folder for the basic sctructure needed below

```
server/
├── src/
│   ├── controllers/
│   │   └── userController.ts
│   ├── models/
│   │   └── User.ts
│   ├── routes/
│   │   └── userRoutes.ts
│   └── server.ts
├── .env
├── package.json
└── tsconfig.json
```

### Step 3 - .env File Setup
Create a .env file in your backend directory and add the following configuration:

```
MONGODB_URL=mongodb+srv://<username>:<password>@cluster0.mlbzwi4.mongodb.net/
PORT=5005
```

### Step 4 - Server Setup
Create a server.ts file and set up your Express.js server with Mongoose:

```
import express, { Express } from 'express'
import mongoose from 'mongoose'
import cors from 'cors'
import dotenv from 'dotenv'
import userRoutes from './routes/userRoutes'

// Load environment variables
dotenv.config()

const app: Express = express()
const port = process.env.PORT || 5005

app.use(express.json())
app.use(cors())

const mongoURI: string = process.env.MONGODB_URL || ''

// Check if MongoDB URL is defined
if (!mongoURI) {
  throw new Error('MONGODB_URL is not defined in .env file')
}

// Connect to MongoDB
mongoose
  .connect(mongoURI)
  .then(() => console.log('Connected to MongoDB 🌍'))
  .catch((err) => console.error('Failed to connect to MongoDB:', err))

// Setup routes
app.use('/api/users', userRoutes)

// Start the server
app.listen(port, () => {
  console.log(`Server Running on Port ${port} 🚀`)
})
```

### Step 5 - User Routes and Controllers
Create user routes (userRoutes.ts), controllers (userController.ts) and models (User.ts):

userRoutes.ts

```
import express from 'express';
import { createUser, getUsers } from '../controllers/userController';

const router = express.Router();

router.post('/', createUser);
router.get('/', getUsers);

export default router;
```

userController.ts

```
import { Request, Response } from 'express'
import User from '../models/User'

// Function to create a new user
export const createUser = async (req: Request, res: Response) => {
  const { username, email, password } = req.body

  try {
       // Create a new user instance
    const newUser = new User({ username, email, password })
        // Save the user to MongoDB
    await newUser.save()
     // Respond with the created user object
    res.status(201).json(newUser)
    // Handle errors
  } catch (error) {
    const errorMessage = (error as Error).message
    res.status(400).json({ message: errorMessage })
  }
}

// Function to retrieve all users
export const getUsers = async (req: Request, res: Response) => {
  try {
     // Fetch all users from MongoDB
    const users = await User.find()
    // Respond with the array of users
    res.status(200).json(users)
  } catch (error) {
    const errorMessage = (error as Error).message
    res.status(500).json({ message: errorMessage })
  }
}
```

User.ts
```
import { Schema, model } from 'mongoose'

// Interface for User document
interface IUser {
  username: string
  email: string
  password: string
}

// Define User schema
const userSchema = new Schema<IUser>({
  username: { type: String, required: true },
  email: { type: String, required: true, unique: true },
  password: { type: String, required: true }
})

// Create User model
const User = model<IUser>('User', userSchema)

export default User
```

### Step 6 - Running the Server
Run your server by executing:

```
npm run dev
```

### API Endpoints
- POST /api/users: Create a new user.
- GET /api/users: Retrieve all users.

## Getting Started - Frontend Setup with Vite  🖥️

### Step 1 - Create React App with Vite
Create a new React frontend using Vite:

```
npm create vite@latest client
cd client
```

### Step 2 - Install Additional Dependencies
Install the required additional dependencies in your frontend project:

```
npm install @emotion/react @emotion/styled @mui/material axios
```

### Step 3 - Implement User Form Component
Create a User Form component (UserForm.tsx) for adding users - src/components/UserForm.tsx:

```
import React, { useState } from 'react';
import { TextField, Button, Box } from '@mui/material';
import axios from 'axios';

const UserForm: React.FC = () => {
  const [username, setUsername] = useState('');
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  const handleSubmit = async (event: React.FormEvent) => {
    event.preventDefault();
    try {
      const response = await axios.post('http://localhost:5005/api/users', {
        username,
        email,
        password
      });
      window.alert('User added successfully!');
      console.log(response.data);
      setUsername('');
      setEmail('');
      setPassword('');
    } catch (error) {
      window.alert('Failed to add user. Please try again.');
      console.error(error);
    }
  };

  return (
    <Box
      component="form"
      onSubmit={handleSubmit}
      sx={{
        display: 'flex',
        flexDirection: 'column',
        width: '300px',
        margin: '0 auto'
      }}
    >
      <TextField
        label="Username"
        value={username}
        onChange={(e) => setUsername(e.target.value)}
        margin="normal"
        required
      />
      <TextField
        label="Email"
        value={email}
        onChange={(e) => setEmail(e.target.value)}
        margin="normal"
        required
      />
      <TextField
        label="Password"
        type="password"
        value={password}
        onChange={(e) => setPassword(e.target.value)}
        margin="normal"
        required
      />
      <Button type="submit" variant="contained" color="primary" sx={{ mt: 2 }}>
        Create User
      </Button>
    </Box>
  );
};

export default UserForm;
```

### Step 4 - Integrate User Form Component in App
Integrate the UserForm component in your App.tsx:

```
import React from 'react';
import UserForm from './components/UserForm';

const App: React.FC = () => {
  return (
    <div className="App">
      <header className="App-header">
        <UserForm />
      </header>
    </div>
  );
};

export default App;
```

### Step 5 - Running the Frontend
Start your frontend development server:

```
import React from 'react';
import UserForm from './components/UserForm';

const App: React.FC = () => {
  return (
    <div className="App">
      <header className="App-header">
        <UserForm />
      </header>
    </div>
  );
};

export default App;
```
## Conclusion
You've set up a complete project with an Express.js API server using TypeScript and Mongoose, integrated with a React frontend built with Vite.  🎉

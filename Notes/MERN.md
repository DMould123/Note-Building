# MERN Stack Installation 🛠️

## What is MERN?

MERN is a full-stack JavaScript framework, comprising four main technologies: MongoDB, Express.js, React.js, and Node.js. It allows developers to build powerful, dynamic web applications using JavaScript throughout the entire development stack.

## Getting Started! 🚀

### Step 1 - Project Setup & Structure 🏗️

####  Client Setup - Using Vite

1. Create a new directory for your MERN project:

```
mkdir my-new-app
```
2. Navigate to the directory:

```
cd my-new-app
```
3. Run the following command to initialize a new Node.js project:

```
npm init -y
```
4. Create a Vite application in a directory named client:

```
npx create-vite@latest client
```

5. Once it finishes, navigate to the client directory:

```
cd client
```
6. Install dependencies


```
npm install
```

#### Server Setup

1. On your root directory, create the server directory:
```
mkdir server
```
2. Navigate to the server directory:

```
cd server 
```
3. Run the following command to initialize a new Node.js project:

```
npm init -y
```
4. Install necessary dependencies:

```
npm install cors dotenv express mongoose
npm install -D typescript @types/express @types/cors @types/node nodemon ts-node
```

5. Create a .gitignore file and add the following lines to it:

```
node_modules
.env
dist/
```
6. Create a tsconfig.json file with the following configurations:

```
{
    "compilerOptions": {
        "target": "es2016",
        "jsx": "preserve",
        "module": "commonjs",
        "allowJs": true,
        "outDir": "./dist",
        "esModuleInterop": true,
        "forceConsistentCasingInFileNames": true,
        "strict": true,
        "skipLibCheck": true
    },
    "exclude": ["node_modules", "dist", "client"]
}
```
7. Create a directory named src inside your server directory:

```
mkdir src
```
8. Create a file called server.ts inside the src directory:

```
import express, { Express, Request, Response } from 'express';
import cors from 'cors';
import mongoose from 'mongoose';
import dotenv from 'dotenv';

dotenv.config();

const app: Express = express();

app.use(cors());
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

const uri: string =
    process.env.MONGODB_URI || 'mongodb://localhost:27017/your-app';

(async () => {
    try {
        await mongoose.connect(uri);
        console.log('Connected to the database');
    } catch {
        console.log('Error connecting to the database');
    }
})();

app.get('/health', (_req: Request, res: Response) => {
    res.status(200).send('Server is running');
});

const PORT: string | number = process.env.PORT || 3000;

app.listen(PORT, () => {
    console.log(`Server is running on PORT: ${PORT}`);
});

```
9. Add the following command to the scripts section of your package.json file:

```
"scripts": {
    "start": "ts-node src/server.ts",
    "build": "tsc",
    "dev": "nodemon src/server.ts"
},
```


### Step 2 - Running the Project ▶️

1. Run the following command to install the development dependency concurrently:

```
npm install --save-dev concurrently
```

2. Navigate to the package.json file in the root directory and copy the corresponding code block and paste it into the scripts section of your package.json file.
```
"scripts": {
    "client": "cd client && npm run dev",
    "server": "cd server && npm run dev",
    "dev": "concurrently \"npm run server\" \"npm run client\""
}
```
3. Run the project:
```
npm run dev
```

4. Both the client and server should be running concurrently. You should see the following output in your terminal:
```
[0] [nodemon] starting `ts-node src/server.ts`
[1]
[1]   VITE v5.1.3  ready in 248 ms
[1]
[1]   ➜  Local:   http://localhost:5173/
[1]   ➜  Network: use --host to expose
[0] Server is running on PORT: 3000
[0] Connected to the database
```
## Credits 🌟

This setup guide is based on the article by Braily Guzman, ["MERN TypeScript Setup Guide"](https://medium.com/@brailyguzman/mern-typescript-setup-guide-af1500100d4b). I've adapted and expanded upon the steps outlined in the article for this README. Special thanks to Braily Guzman for the detailed explanation and guidance.

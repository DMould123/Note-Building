# Firebase Installation 🔥

## What is Firebase?

Firebase is a comprehensive platform developed by Google, offering various tools and services for mobile and web app development, including features like real-time database, authentication, hosting, and analytics.

## Getting Started!

### Step 1 - Project Setup in VSC

Create a React.js project with Vite, by simply running this command in your terminal on VSC.

```
npm create vite@latest dm-job-tracker-app -- --template react
```

Follow the commands given

```
cd dm-job-tracker-app
npm install
npm run dev
```

This may take time some time depending on the time of your computer!

### Step 2 - Firebase Setup

Install Firebase as an NPM dependancy for the project by running the following command in the terminal:

```
npm i firebase
```

Now set up your file structure, as follows:

/firebase.js
/src/context/AuthContext.jsx
/.env
/src/components/Login.jsx
/src/components/Dashboard.jsx

#### Firebase.js

The firebase.js file contain the following code:

```
import {initializeApp} from 'firebase/app'
import {getAuth} from 'firebase/auth'
import {getFirestore} from 'firebase/firestore'

// Your web app's Firebase configuration
const firebaseConfig = {
  apiKey: import.meta.env.VITE_APIKEY,
  authDomain: import.meta.env.VITE_AUTHDOMAIN,
  projectId: import.meta.env.VITE_PROJECTID,
  storageBucket: import.meta.env.VITE_STORAGEBUCKET,
  messagingSenderId: import.meta.env.VITE_MESSAGINGSENDERID,
  appId: import.meta.env.VITE_APPID
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);

export const auth = getAuth(app)
export const db = getFirestore(app)
```

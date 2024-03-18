# Tailwind CSS Installation 🔥

## What is Tailwind CSS?

Tailwind CSS is a utility-first CSS framework for rapidly building custom designs. It provides low-level utility classes that let you build completely custom designs without ever leaving your HTML.

## Getting Started!

### Step 1 - Project Setup in VSC

Create a React.js project with Vite, by simply running this command in your terminal on VSC.

```
npm create vite@latest my-tailwind-firebase-app  -- --template react
```

Follow the commands given

```
cd my-tailwind-firebase-app
npm install
npm run dev
```

This may take time some time depending on the time of your computer!

### Step 2 - Install Tailwind CSS

```
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```
This will generate a tailwind.config.js and postcss.config.js file.

### Step 3 - Configure template paths

Add this in your tailwind.config.js file.

```
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```
### Step 4 - Add Tailwind to CSS

Add the following @tailwind directives for each of Tailwind’s layers to your index.css file.

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Step 4 - Start using Tailwind in your project

```
export default function App() {
  return (
    <h1 className="text-3xl font-bold underline">
      Hello world!
    </h1>
  )
}
```

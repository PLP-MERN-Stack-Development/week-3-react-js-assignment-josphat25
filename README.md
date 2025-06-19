[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19817929&assignment_repo_type=AssignmentRepo)
# React.js and Tailwind CSS Assignment

This assignment focuses on building a responsive React application using JSX and Tailwind CSS, implementing component architecture, state management, hooks, and API integration.

## Assignment Overview

You will:
1. Set up a React project with Vite and Tailwind CSS
2. Create reusable UI components
3. Implement state management using React hooks
4. Integrate with external APIs
5. Style your application using Tailwind CSS

## Getting Started

1. Accept the GitHub Classroom assignment invitation
2. Clone your personal repository that was created by GitHub Classroom
3. Install dependencies:
   ```
   npm install
   ```
4. Start the development server:
   ```
   npm run dev
   ```

## Files Included

- `Week3-Assignment.md`: Detailed assignment instructions
- Starter files for your React application:
  - Basic project structure
  - Pre-configured Tailwind CSS
  - Sample component templates

## Requirements

- Node.js (v18 or higher)
- npm or yarn
- Modern web browser
- Code editor (VS Code recommended)

## Project Structure

```
src/
├── components/       # Reusable UI components
├── pages/           # Page components
├── hooks/           # Custom React hooks
├── context/         # React context providers
├── api/             # API integration functions
├── utils/           # Utility functions
└── App.jsx          # Main application component
```

## Submission

Your work will be automatically submitted when you push to your GitHub Classroom repository. Make sure to:

1. Complete all required components and features
2. Implement proper state management with hooks
3. Integrate with at least one external API
4. Style your application with Tailwind CSS
5. Deploy your application and add the URL to your README.md

## answers 
git clone <your-repo-url>

cd <your-project-folder>

npm install

npm run dev

Confirm that Tailwind CSS is working by editing index.css or a component and using a Tailwind class
# Create reusable UI components 
In src/components/:
button.jsx
export default function Button({ children, onClick }) {

  return (
  
    <button
    
      onClick={onClick}
      
      className="px-4 py-2 bg-blue-600 text-white rounded hover:bg-blue-700"
      
    >
    
      {children}
      
    </button>
    
  );
}

#  Implement state management using React hooks
In src/pages/ or src/App.jsx:
Use useState and useEffect

import { useState, useEffect } from 'react';

export default function App() {

  const [count, setCount] = useState(0);

  return (
  
    <div className="p-4">
    
      <button onClick={() => setCount(count + 1)} className="px-4 py-2 bg-green-500 text-white rounded">
      
        Count: {count}
        
      </button>
      
    </div>
    
  );
}

# Integrate with an external API
In src/api/:

 Create a function,
 
 export async function fetchUsers() {
 
  const res = await fetch('https://jsonplaceholder.typicode.com/users');
  
  return res.json();
}

In a component:

import { useState, useEffect } from 'react';

import { fetchUsers } from '../api/fetchUsers';

export default function Users() {

  const [users, setUsers] = useState([]);

  useEffect(() => {
  
    fetchUsers().then(data => setUsers(data));
    
  }, []);

  return (
  
    <div>
    
      {users.map(user => (
      
        <div key={user.id} className="p-4 mb-2 bg-gray-100 rounded">
        
          {user.name}
          
        </div>
        
      ))}
      
    </div>
    
  );
}

# Style with Tailwind CSS

Use Tailwind utility classes for all layout and design.

Keep styles responsive with sm:, md:, lg: breakpoints.

# src/App.jsx
import { useState, useEffect } from "react";

import Button from "./components/Button";

import Card from "./components/Card";

import { fetchUsers } from "./api/fetchUsers";

export default function App() {

  const [count, setCount] = useState(0);
  
  const [users, setUsers] = useState([]);

  useEffect(() => {
  
    fetchUsers().then((data) => setUsers(data));
  }, []);
  

  return (
  
    <main className="p-6"> 
    
      <h1 className="text-3xl font-bold mb-4 text-blue-700">React + Tailwind Scaffold</h1>

      <Button onClick={() => setCount(count + 1)}>
      
        Click Count: {count}
        
      </Button>

      <h2 className="text-2xl font-semibold mt-8 mb-4">Users:</h2>
      
      <div className="grid gap-4">
      
        {users.map((user) => (
        
          <Card key={user.id} title={user.name}>
          
            <p>Email: {user.email}</p>
            
            <p>Phone: {user.phone}</p>
            
          </Card>
          
        ))}
        
      </div>
      
    </main>
    
  );
  
}

# src/components/Button.jsx

export default function Button({ children, onClick }) {

  return (
  
    <button
    
      onClick={onClick}
      
      className="px-4 py-2 bg-blue-600 text-white rounded hover:bg-blue-700 transition-colors"
      
    >
      {children}
      
    </button>
    
  );
}

# src/components/Card.jsx

export default function Card({ title, children }) {

  return (
  
    <div className="p-4 border border-gray-300 rounded shadow-sm bg-white">
    
      <h3 className="text-lg font-bold mb-2">{title}</h3>
      
      {children}
      
    </div>
    
  );
}

# src/api/fetchUsers.js

export async function fetchUsers() {

  const response = await fetch("https://jsonplaceholder.typicode.com/users");
  
  if (!response.ok) {
  
    throw new Error("Failed to fetch users");
    
  }
  
  return response.json();
  
}

# src/index.css

@tailwind base;

@tailwind components;

@tailwind utilities;

# src/main.jsx

import React from "react";

import ReactDOM from "react-dom/client";

import App from "./App";

import "./index.css";

ReactDOM.createRoot(document.getElementById("root")).render(

  <React.StrictMode>
  
    <App />
    
  </React.StrictMode>
  
);



## Resources

- [React Documentation](https://react.dev/)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [Vite Documentation](https://vitejs.dev/guide/)
- [React Router Documentation](https://reactrouter.com/) 

# Digital Bank of Credentials
The Digital Credentials Bank is a secure, single-page web app for centralized credential management. It uses customizable categories and an NLP Suggestion Engine (keyword matching) to instantly recommend the best category for storage, ensuring quick organization. Built on HTML/Tailwind/JS, Firebase Auth , and Firestore for real-time storage. 
Digital Credentials Bank
🎓 Project Overview
The Digital Credentials Bank is a secure, single-page web application for centralized credential management (certificates, licenses, awards). Users store items in customizable categories and define their own organizational structure for professional achievements. Its core is an NLP Suggestion Engine (keyword matching) that instantly recommends the best storage category based on the credential's description, ensuring quick and accurate organization and reducing manual effort. The application provides a clear dashboard to view all items and assigned categories. The robust stack uses HTML/Tailwind/JS, Firebase Auth for secure login (Email/Password & Google Sign-In), and Firestore for real-time, scalable data storage. Fully responsive and ideal for easy GitHub Pages deployment.

✨ Key Features
Secure Authentication: Sign Up and Log In using Email/Password or Google Sign-In (Firebase Auth).

Real-time Storage: Credentials and custom categories are persisted using Google Firestore.

Dynamic Categories: Default categories (Academics, Sports, Cooking) plus user-defined custom categories.

Intelligent Organization: NLP simulation suggests the correct category based on content keywords.

Fully Responsive: Built with Tailwind CSS for optimal viewing on desktop and mobile devices.

🛠️ Setup and Configuration (CRITICAL STEP)
This application requires a Firebase Project to handle authentication and database storage. The person cloning this repository must perform the following steps:

Step 1: Create a Firebase Project
Go to the Firebase Console.

Create a new Firebase Project (e.g., digital-credentials-bank-prod).

Step 2: Configure Authentication Providers
You must explicitly enable the sign-in methods used in the application:

In the Firebase Console, navigate to Build > Authentication.

Click the "Sign-in method" tab.

Enable "Email/Password" and Save.

Enable "Google" and follow the prompts to configure it (usually just enabling and saving is sufficient).

Step 3: Register a Web App and Get Config Keys
In the Firebase Console, go to Project settings (gear icon next to "Project Overview").

Scroll down to the "Your apps" section and click the Web icon (</>) to add a new Web App.

Copy the resulting firebaseConfig object (it's a JavaScript object starting with {}).

Step 4: Add Configuration to the Project
To run this project, you must inject your configuration keys. You have two primary options:

Option A: Local Development (Recommended)
Create a new file named firebase_config.js in the root directory (next to index.html).

Paste your copied configuration inside, defining the firebaseConfig variable, like this:

// firebase_config.js
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_AUTH_DOMAIN",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_STORAGE_BUCKET",
    messagingSenderId: "YOUR_MESSAGING_ID",
    appId: "YOUR_APP_ID"
};




In index.html, uncomment the section that imports and uses this local config.

Option B: Environment Variables (For Managed Hosting)
If you are deploying to a platform that uses environment variables (like a custom Canvas environment), ensure the platform loads your keys into the global variable __firebase_config as a JSON string.

🚀 Deployment
The entire application is self-contained in index.html.


**⚙️ Local Development Setup (VS Code) :**


This application relies on environment variables (__firebase_config, __app_id, __initial_auth_token) that are automatically provided in the Canvas environment but do not exist in VS Code.

To run the project locally, you must perform the following steps to inject your Firebase API keys and properly launch the file.

Step 1: Secure Your Firebase Configuration
You need to hardcode your project's configuration into the index.html file.

Get Your Config: Retrieve your firebaseConfig object from the Firebase Console (Settings > Web App).

Create firebase_config.js: Create a new file named firebase_config.js in the root of your project directory (the same folder as index.html). This file holds your secrets and is ignored by Git.

Content of firebase_config.js:
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID",
};

Step 2: Update index.html
Modify the <script type="module"> block in index.html to load your new configuration file instead of relying on environment variables.

A. Remove Canvas Variables: Locate lines 426-427 (or near the start of the <script type="module"> block):

// Default to an empty object if variables aren't defined, which prevents crashes
const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
const firebaseConfig = JSON.parse(typeof __firebase_config !== 'undefined' ? __firebase_config : '{}');
**B. Replace with Local Import:** **Replace** those lines with a dynamic import for your new local file:
```javascript
// --- LOCAL VS CODE SETUP ---
import { firebaseConfig } from './firebase_config.js'; // Import your local config file
const appId = firebaseConfig.appId; // Use the appId from the local config
// --- END LOCAL SETUP ---
*(Note: You do not need to worry about `__initial_auth_token` as this new setup naturally bypasses it and goes to the login screen.)*

### Step 3: Run the Application Locally

Due to the use of JavaScript modules (`import/export`), you cannot simply double-click `index.html`. You need a local server.

1.  **Install Live Server:** In VS Code, install the **Live Server** extension (by Ritwick Dey).
2.  **Launch:** Right-click on `index.html` and select **"Open with Live Server"**.

The application will open in your browser, connect to your Firebase project, and prompt you to Sign Up or Log In.

I've updated the `README.md` to be extremely clear about the steps required for a user running the code locally in VS Code. It explains why the Canvas variables don't work and provides the specific code and file structure required to load the secret Firebase API keys safely and correctly.

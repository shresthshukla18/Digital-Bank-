# Digital-Bank-
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

Commit all files to a new GitHub repository.

Enable GitHub Pages for the repository, selecting the main branch (or whichever branch holds your index.html).

The application will be live at https://[your-username].github.io/[repository-name].

# **FireNext: Host Your Next.js App on Firebase**

This comprehensive guide will walk you through the process of setting up and hosting a **Next.js** application on **Firebase**. In just a few steps, you’ll have your app live and running!

---

## 🚀 **Prerequisites**

Before we begin, please ensure you have the following:

- A **Firebase account**: [Sign up here](https://firebase.google.com)
- **Node.js** (LTS version): [Download Node.js](https://nodejs.org/en/download)
- **VS Code** (or any code editor of your choice)

---

## 🛠️ **Step 1: Install Node.js**

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/1.PNG)

1. Visit the [Node.js download page](https://nodejs.org/en/download) and grab the **LTS version**.
2. Run the installer and follow the on-screen instructions.

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/2.PNG)

3. Ensure you enable the option to **automatically install the required tools**.

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/3.PNG)

4. After installation is complete, click **Finish**.

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/4.PNG)   

5. A terminal window will appear, installing additional tools. Once finished, press any key to continue, and close the terminal window.
---

## 🔥 **Step 2: Create a Firebase Project**

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/CreateFirebaseProject1.PNG)

1. Head to the [Firebase Console](https://console.firebase.google.com) and create a new project.

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/CreateFirebaseProject2.PNG)

2. Name your project and **disable Google Analytics**.

3. Click **Create Project** to finalize.
![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/CreateFirebaseProject3.PNG)

---

## ⚡ **Step 3: Set Up Your Next.js App**

1. Create a new **Next.js** app:
   
![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/SettingsInVscode.PNG)

   ```bash
   npx create-next-app@latest Your-App-Name
   ```

2. Answer the prompts as follows:
   - **TypeScript**: Yes
   - **ESLint**: Yes
   - **Tailwind CSS**: Yes
   - **'src/' directory**: No
   - **App Router**: Yes
   - **Turbopack**: No
   - **Custom Import Alias**: No

  This will take some time...😴
---


## 🧰 **Step 4: Install Firebase SDK**

1. Navigate to your project directory and install the Firebase SDK:
   
![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/installfirebasetools.PNG)

```bash
   npm install firebase
   ```

2. Install **Firebase CLI** globally by running:

 ```bash
   npm install -g firebase-tools
   ```

3. Test the Firebase installation:

```bash
   firebase --version
   ```
   
![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/FirebaseError.PNG)

As you can see in the error message, there’s an error message related to the firebase.ps1 file on the C: \Users\username\AppData\Roaming\npm path.

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/Firebase.psifile.PNG)

Go to that path and delete the firebase.ps1 file.

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/After%20Firebase%20Error.PNG)

Test the Firebase installation again:

   ```bash
   firebase --version
   ```

Now it's solved 😎

---

## 📦 **Step 5: Log Into the Firebase**
  ![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/FirebaseLogin.PNG)
  1. **Login to Firebase** with:

   ```bash
   firebase login
   ```
  ![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/FirebaseLoginSuccess.PNG)
  A browser window will appear where you need to allow Firebase CLI to access your Google account.

---

## 🔧 **Step 6: Initialize Firebase in Your Project**

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/Firebaseinit.PNG)
1. Run the initialization command:

```bash
   firebase init
   ```
![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/FirebaseInitSettings1.PNG)

2. When prompted, select **Hosting** and configure for Firebase Hosting.
![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/FirebaseInitSettings2.PNG)

3. Choose the **Use an existing project** you created earlier.

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/SelectExistingProject.PNG)

4. Then select the existing project that you created earlier.

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/FinallySettingsdone.PNG)

5. Set **public directory** to `out`.
6. Configure it as a **single-page app** by selecting **Yes** when asked to rewrite all URLs to `/index.html`.
7. Choose **No** for GitHub Actions (optional).

---

## 📱 **Step 7: Add Firebase Realtime Database to Your Project**

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/CreateRealtimeDatabase.PNG)

1. In the Firebase Console, navigate to **Database** > **Realtime Database**.

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/SetupDatabase.PNG)

2. Select the **Singapore** as the realtime database location.

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/StartTestmode.PNG)

3. Click **Create Database** and choose **Start in test mode** and click enable.
4. Create a web app in the firebase.   

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/Add%20App.PNG)

5. In the project main menu click the **Add app**

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/Register%20App.PNG)

6. Fill the details according to your app & Check the **Also setup the **Firebase Hosting** for this app** and select the existing project and click Register app.

![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/AddSDK.PNG)

7. Copy your **Firebase Web App config** from this window or form **Project settings > General** under **Your apps**.
8. In your Next.js app, create a new file `firebase.js` in the `app/` folder and add:

   ```javascript
   import firebase from 'firebase/app';
   import 'firebase/database'; // Import Realtime Database service

   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
     databaseURL: "https://YOUR_PROJECT_ID.firebaseio.com",
     projectId: "YOUR_PROJECT_ID",
     storageBucket: "YOUR_PROJECT_ID.appspot.com",
     messagingSenderId: "YOUR_SENDER_ID",
     appId: "YOUR_APP_ID"
   };

   if (!firebase.apps.length) {
     firebase.initializeApp(firebaseConfig);
   } else {
     firebase.app();
   }

   export default firebase;
   ```

---

## 🌍 **Step 8: Deploy with Firebase Realtime Database Support**

1. Build the file from **Page.tsx** file, after compiling the build you can deploy it locally or deploy to the firebase 
   
![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/npmrunbuild.PNG)

**🔰You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file. 🔰**

2. **Test Locally**:
   
![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/npmrundev.PNG)

   Run your app locally using:

   ```bash
   npm run dev
   ```

   Or:

   ```bash
   firebase serve
   ```

   Ensure everything is working as expected with Firebase Realtime Database.

3. **Deploy to Firebase**:

   Once you’re ready, deploy your app to Firebase:
![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/FireabaseDeploy.PNG)

```bash
   firebase deploy
   ```

---
![](https://github.com/Kavi-ya/FireNext/blob/main/Assets/NextJS%20Test%20page.PNG)
## 🎉 **Congratulations!**

You’ve successfully set up and deployed your **Next.js** app on **Firebase Hosting** with **Realtime Database** support. Your app is now live and ready to be used! 🚀
---

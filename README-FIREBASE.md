# Firebase Setup Guide for Age Calculator SB

Follow these steps to link your own Firebase project to this application.

## 1. Create a Firebase Project
1. Go to [Firebase Console](https://console.firebase.google.com/).
2. Click **Add project** and follow the setup wizard.

## 2. Register a Web App
1. In your Firebase project overview, click the **Web** icon (</>) to register a new app.
2. Give it a name (e.g., `AgeCalculatorSB`).
3. You will see a `firebaseConfig` object. Keep this window open.

## 3. Configure the Applet
1. Locate the file `firebase-applet-config.json` in this project.
2. Replace the placeholder values with your actual configuration from the Firebase console.
3. **Important**: Ensure `firestoreDatabaseId` is set to `"(default)"` unless you created a custom database.

## 4. Enable Firestore
1. In the Firebase left sidebar, go to **Build** > **Firestore Database**.
2. Click **Create database**.
3. Choose a location and start in **Test mode** (or Production mode if you deploy rules immediately).

## 5. Security Rules
Copy the following into your Firebase Console's **Rules** tab for Firestore:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Default deny
    match /{document=**} {
      allow read, write: if false;
    }
    
    // User History Rules
    match /history/{itemId} {
      allow create: if request.auth != null && request.resource.data.userId == request.auth.uid;
      allow read: if request.auth != null && resource.data.userId == request.auth.uid;
    }
    
    // Birthday Rules
    match /birthdays/{bdayId} {
      allow read, write: if request.auth != null && (resource == null || resource.data.userId == request.auth.uid) && (request.resource == null || request.resource.data.userId == request.auth.uid);
    }
  }
}
```

## 6. Authentication (Optional but Recommended)
For the rules above to work, you should enable **Anonymous Auth** or **Google Auth** in the Firebase console under **Build** > **Authentication**.

# 💬 FCM Push Notification Integration for Chat (Mobile)

This project is a React Native application for the Android platform, demonstrating the implementation of Firebase Cloud Messaging (FCM) to handle push notifications. It simulates the recipient's side of a chat application, where a user can receive instant notifications for new messages.

## 🚀 Getting Started

Follow these steps to set up and run the Android app locally.

### Prerequisites

* **Node.js** (v18 or higher)
* **npm** or **yarn**
* **React Native CLI** (`npm install -g react-native-cli`)
* **Java Development Kit (JDK)** (v11 or higher)
* **Android Studio** with an emulator configured or an Android device for testing.
* A **Firebase project** with Cloud Messaging enabled.

### 1. Firebase Setup

1.  **Create a Firebase Project**: If you haven't already, go to the [Firebase Console](https://console.firebase.google.com/) and create a new project.
2.  **Add an Android App**: In your Firebase project, click the "Add app" button and select the Android platform (`</>`).
3.  **Register the App**: Provide the **package name** for your Android app. You can find this in `android/app/src/main/AndroidManifest.xml` under the `package` attribute (e.g., `com.fcmchatapp`).
4.  **Download `google-services.json`**: Firebase will prompt you to download a `google-services.json` file. **This is a critical step.** Download it and place it in the `android/app/` directory of your project.
5.  **Enable Cloud Messaging**: In the Firebase Console, navigate to **Project settings** > **Cloud Messaging**. Make a note of the **Server key** under the "Cloud Messaging API (Legacy)" tab. You'll need this for sending test notifications.

---

### 2. Project Configuration

1.  Clone this repository:
    ```bash
    git clone <YOUR_REPO_URL>
    cd <YOUR_PROJECT_NAME>
    ```
2.  Install the dependencies:
    ```bash
    npm install
    # or
    yarn install
    ```
3.  Make sure the `google-services.json` file is correctly placed in `android/app/`. This file contains all the necessary configuration for Firebase.

---

### 3. Running the Application

1.  Start the Metro Bundler:
    ```bash
    npm start
    # or
    yarn start
    ```
2.  In a new terminal, build and run the app on an Android device or emulator:
    ```bash
    npx react-native run-android
    ```
    *If you encounter a build error, try cleaning the Android project with `cd android && ./gradlew clean && cd ..` and then run the command again.*

---

### 4. How to Test Notifications

1.  **Grant Permission**: When the app starts, it will automatically request push notification permission. Grant the permission when prompted.
2.  **Get FCM Token**: The app will log the device's unique FCM token to the console. You can view this in the Android Studio logcat or by running `adb logcat | grep "FCM Token"`.
3.  **Send a Test Message**:
    * Go to the [Firebase Console](https://console.firebase.google.com/).
    * Navigate to **Engage** > **Cloud Messaging**.
    * Click "Send your first message" or "New notification".
    * Enter a title and text for your notification.
    * In the "Target" section, select "Send to a specific token".
    * Paste the FCM token you copied into the text field.
    * Click "Review" and then "Publish" to send the notification.

### Notification Scenarios

* **Foreground**: When the app is open and active, the notification will be handled within the app itself (e.g., displaying a message or a toast).
* **Background/Closed**: When the app is in the background or killed, the notification will be delivered as a native system notification on the Android device.

---

### 🛠️ Key Features

* **FCM Token Retrieval**: The app requests notification permission and retrieves a unique FCM token, which is logged for easy access.
* **Foreground Handling**: The app has listeners to handle incoming messages when it's in the foreground, allowing for custom UI display.
* **Background Handling**: The Firebase SDK handles background and killed app states, ensuring native system notifications are displayed automatically.
* **UI for Testing**: A simple UI simulates a chat message flow, which would trigger a notification in a real-world scenario.

---

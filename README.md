# Age Calculator SB - Setup Guide

Welcome to the **Age Calculator SB** Telegram Mini App! This guide will help you set up the application, configure Firebase, and understand the core features like the Point System and Admin Panel.

## 🚀 Quick Setup

1.  **Firebase Setup**:
    *   Initialize Firebase using the `set_up_firebase` tool or manually via the Firebase Console.
    *   Go to **Firestore Database** and create three main collections:
        *   `posts`: For storing blog content (Title, Image URL, Description/Content).
        *   `withdrawals`: For managing user bKash withdrawal requests.
        *   `settings`: Document `global` for theme customization.
        *   `users`: For storing user points and active status.
    *   Copy your Firebase configuration into `firebase-applet-config.json` in the root directory.

2.  **Authentication**:
    *   This app uses **Telegram Mini App SDK** to identify users.
    *   Firebase Auth is used for secure background communication.

## 🔐 Admin Panel

Access the Admin Panel via the **Profile -> Admin** button.

*   **Username**: `sbneeladmin`
*   **Password**: `neelbaba`

### Admin Features:
*   **Blog**: 
    *   **Viewing**: Users earn **1 point** for every blog post they scroll to (view).
    *   **Redirecting**: Clicking on a blog post redirects the user to the URL specified by the admin.
*   **Withdrawal**:
    *   Minimum Limit: **100 Points**.
    *   Payment Method: **bKash**.
    *   Status: Users can track if their request is "Pending" or "Accepted" from their profile.

## 🎨 Theme Customization

You can change the look of the app without touching the code:
1.  Log in as Admin.
2.  Go to the **Settings** tab.
3.  Pick a **Primary Color** (Buttons, icons, highlights).
4.  Pick a **Surface Color** (Background).
5.  Click **Save Settings**. The change will apply instantly to all users.

## 🇧🇩 Language Support

The app supports **English** and **Original Bengali**. You can switch languages from the Profile menu. The Bengali translation is optimized for natural phrasing.

---
*Created by Age Calculator SB Team*

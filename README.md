# ANU Ascend Bézier Canvas

This project renders an interactive Bézier drawing canvas that now requires users to authenticate with Firebase before interacting with the editor. Signed-in users can place control points, render smoothed curves, and export the drawing data as JSON.

## Getting started

1. Serve the project with any static file server (for example, run `npx serve .` from this directory).
2. Visit the served URL in a modern browser that supports ES modules.

## Firebase configuration

1. Create a Firebase project or open the existing **anuascend-3f734** project at <https://console.firebase.google.com/>.
2. In the Firebase console, add a new **Web app** to retrieve your configuration keys.
3. This repository already includes the configuration for the `anuascend-3f734` project inside [`firebase-config.js`](./firebase-config.js). If you spin up a different Firebase project, replace those values with the configuration snippet that Firebase generates for your app.
4. In **Authentication ▸ Sign-in method**, enable the **Email/Password** provider.
5. (Optional) Seed your first user under **Authentication ▸ Users** or use the in-app "Create account" button to register.
6. If you plan to serve this project from a custom domain, add that domain to **Authentication ▸ Settings ▸ Authorized domains**.

## Usage

- Use the **Sign in** button (or the overlay prompt) to authenticate with your email and password.
- New users can select **Create account** to register directly from the overlay when Email/Password authentication is enabled.
- After authentication, click on the canvas to add points; the curve and points update automatically.
- Use **Save JSON** to display the serialized curve data in a modal. The modal can be closed with the **Close** button or by clicking outside the dialog.
- Click **Clear** to remove all points from the canvas.
- Use **Sign out** to end the current session; this re-locks the canvas until another authentication occurs.

## Development notes

- Authentication is enforced entirely on the client side through Firebase Authentication.
- The Firebase SDK is loaded via ESM imports from the official CDN and initialized with your project configuration at runtime.
- No user data is stored beyond what Firebase manages; exporting JSON remains a local-only action.

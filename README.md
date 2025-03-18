# React OIDC Authentication Example

This is a simple React application demonstrating the use of OpenID Connect (OIDC) authentication with Cognito using the `react-oidc-context` library.

## Features
- Sign in with Cognito OIDC flow
- Display user information like email and tokens (ID, Access, and Refresh)
- Sign out functionality, both through `react-oidc-context` and a custom redirect to Cognito's logout endpoint

## Setup

### Prerequisites
Make sure you have **Node.js** and **npm** installed on your system.

Node: v22.14.0

### Install Dependencies

To get started, clone the repository and navigate to the project folder. Then, run the following command to install the necessary dependencies:

```bash
npm install
```

Run the Application
Once dependencies are installed, you can start the development server by running:

```bash
npm run
```

### Configuration

Before running the application, update the following placeholder values in the files:

#### 1. `index.js`

In this file, you need to replace the placeholder values with your **Cognito details**:

- **`authority`**: Set this to the base URL of your Cognito user pool (e.g., `https://cognito-idp.{region}.amazonaws.com/{userPoolId}`).
- **`client_id`**: Set this to your Cognito app client ID.
- **`redirect_uri`**: Set this to the URI to which Cognito will redirect after authentication (e.g., `http://localhost:3000`).
- **`scope`**: Typically, you'll use `openid`, `email`, and `profile` for the required scopes.

Example:

```js
const cognitoAuthConfig = {
  authority: "https://cognito-idp.{region}.amazonaws.com/{userPoolId}", // replace with your Cognito authority URL
  client_id: "your-client-id", // replace with your Cognito client ID
  redirect_uri: "http://localhost:3000", // replace with your redirect URI
  response_type: "code",
  scope: "email openid phone", // replace with required scopes
};
```

#### 2. `App.js`

In this file, you need to replace the following placeholders:

- **`clientId`**: Set this to your **Cognito app client ID**.
- **`logoutUri`**: Set this to the **URI** you want the user to be redirected to after logging out (e.g., `http://localhost:3000`).
- **`cognitoDomain`**: Set this to the **Cognito domain** for your user pool (e.g., `https://your-cognito-domain.auth.us-east-1.amazoncognito.com`).

Here’s the relevant section in `App.js`:

```js
const signOutRedirect = () => {
  const clientId = ""; // replace with your Cognito client ID
  const logoutUri = "<logout uri>"; // replace with your desired logout URI
  const cognitoDomain = ""; // replace with your Cognito domain
  window.location.href = `${cognitoDomain}/logout?client_id=${clientId}&logout_uri=${encodeURIComponent(logoutUri)}`;
};
```
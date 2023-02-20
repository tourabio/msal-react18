# MSAL.js for React Sample - Authorization Code Flow in Single-Page Applications

## About this sample

This developer sample is used to run basic use cases for the MSAL library. You can also alter the configuration in `./src/authConfig.js` to execute other behaviors.

## Notable files and what they demonstrate

1. `./src/App.js` - Shows implementation of `MsalProvider`, all children will have access to `@azure/msal-react` context, hooks and components.
1. `./src/index.js` - Shows initialization of the `PublicClientApplication` that is passed to `App.js`
1. `./src/pages/Home.jsx` - Homepage, shows how to conditionally render content using `AuthenticatedTemplate` and `UnauthenticatedTemplate` depending on whether or not a user is signed in.
1. `./src/pages/Profile.jsx` - Example of a protected route using `MsalAuthenticationTemplate`. If a user is not yet signed in, signin will be invoked automatically. If a user is signed in it will acquire an access token and make a call to MS Graph to fetch user profile data.
1. `./src/authConfig.js` - Configuration options for `PublicClientApplication` and token requests.
1. `./src/ui-components/SignInSignOutButton.jsx` - Example of how to conditionally render a Sign In or Sign Out button using the `useIsAuthenticated` hook.
1. `./src/ui-components/SignInButton.jsx` - Example of how to get the `PublicClientApplication` instance using the `useMsal` hook and invoking a login function.
1. `./src/ui-components/SignOutButton.jsx` - Example of how to get the `PublicClientApplication` instance using the `useMsal` hook and invoking a logout function.
1. `./src/utils/MsGraphApiCall.js` - Example of how to call the MS Graph API with an access token.
1. `./src/utils/NavigationClient.js` - Example implementation of `INavigationClient` which can be used to override the default navigation functions MSAL.js uses

### (Optional) MSAL React and class components

For a demonstration of how to use MSAL React with class components, see: `./src/pages/ProfileWithMsal.jsx` and `./src/pages/ProfileRawContext.jsx`.

_After_ you initialize `MsalProvider`, there are 3 approaches you can take to protect your class components with MSAL React:

1. Wrap each component that you want to protect with `withMsal` higher-order component (HOC) (e.g. [Profile](./src/pages/ProfileWithMsal.jsx#Profile)).
1. Consume the raw context directly (e.g. [ProfileContent](./src/pages/ProfileRawContext.jsx#ProfileContent)).
1. Pass context down from a parent component that has access to the `msalContext` via one of the other means above (e.g. [ProfileContent](./src/pages/ProfileWithMsal.jsx#ProfileContent)).

For more information, visit:

- [Docs: Class Components](../../../lib/msal-react/docs/class-components.md)
- [MSAL React FAQ](../../../lib/msal-react/FAQ.md)

## How to run the sample

### Pre-requisites

- Install node.js if needed (<https://nodejs.org/en/>).

### Configure the application

- Open `./src/authConfig.js` in an editor.
- Replace client id with the Application (client) ID from the portal registration, or use the currently configured lab registration.
  - Optionally, you may replace any of the other parameters, or you can remove them and use the default values.

##### Installing @azure/msal-react and @azure/msal-browser from released versions available on npm

```bash
# Change directory to sample directory
cd samples/msal-react-samples/react-18-sample

# Install packages from npm
npm run install:published

# Install rest of dependencies
npm install
```

#### Running the sample development server

1. create a .env file in the same level with package.json and copy all the keys from the .env.sample to the new .env and add the necessary values in it.
1. In a command prompt, run `npm start`.
1. Open [http://localhost:3000](http://localhost:3000) to view it in the browser.
1. Open [http://localhost:3000/profile](http://localhost:3000/profile) to see an example of a protected route. If you are not yet signed in, signin will be invoked automatically.

The page will reload if you make edits.
You will also see any lint errors in the console.

- In the web page, click on the "Login" button and select either `Sign in using Popup` or `Sign in using Redirect` to begin the auth flow.

#### Running the sample production server

1. In a command prompt, run `npm run build`.
1. Next run `serve -s build`
1. Open [http://localhost:3000](http://localhost:3000) to view it in the browser.
1. Open [http://localhost:3000/profile](http://localhost:3000/profile) to see an example of a protected route. If you are not yet signed in, signin will be invoked automatically.

#### Learn more about the 3rd-party libraries used to create this sample

- [React documentation](https://reactjs.org/).
- [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started)
- [React Router documentation](https://reactrouterdotcom.fly.dev/docs/en/v6)
- [Material-UI documentation](https://mui.com/getting-started/installation/)

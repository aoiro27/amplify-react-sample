# cognitoログインをReactアプリに組み込む手順をまとめたリポジトリ

1.create react app & add dependency
```
npx create-react-app web --template typescript
cd web
npm install aws-amplify @aws-amplify/ui-react
```

2.add amplify fonts to putlic/index.html
```
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Inter:slnt,wght@-10..0,100..900&display=swap"
      rel="stylesheet"
    />
```

3. change src/App.tsx to implements authentication
```
import { Amplify } from 'aws-amplify';

import { Authenticator } from '@aws-amplify/ui-react';
import '@aws-amplify/ui-react/styles.css';

Amplify.configure({
  aws_project_region: process.env.REACT_APP_AWS_PROJECT_REGION,
  aws_cognito_region: process.env.REACT_APP_AWS_COGNITO_REGION,
  aws_user_pools_id: process.env.REACT_APP_AWS_USER_POOLS_ID,
  aws_user_pools_web_client_id:  process.env.REACT_APP_AWS_USER_POOLS_CLIENT_ID,
});

export default function App() {
  return (
    <Authenticator>
      {({ signOut, user }) => (
        <main>
          <h1>Hello {user.username}</h1>
          <button onClick={signOut}>Sign out</button>
        </main>
      )}
    </Authenticator>
  );
}
```

4.  set local environment
```
$ export REACT_APP_AWS_PROJECT_REGION=ap-northeast-1
$ export REACT_APP_AWS_COGNITO_REGION=ap-northeast-1
$ export REACT_APP_AWS_USER_POOLS_ID=<UserPoolID>
$ export REACT_APP_AWS_USER_POOLS_CLIENT_ID=<UserPoolClientID>
```
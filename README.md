# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `yarn start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `yarn test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `yarn build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `yarn eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `yarn build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)


## Redux_Full_Tutorial
----

1. What is Redux?
   1.  Redux is a state manager package 

2. Why Redux?
   1. Typically in React we would have APP then we would have a component and sometimes we run a fetch for example to pull data into that component. Say we need that data to be accessessed elsewhere in our application. That would normally require us to lift the state back to the top level of our appication (if were not using Context in React) and then pass it back down via props.

3. Store
   1. Globalized State; Think of it as a seperate entity that your components can tap into

4. Action
   1. It describes what you want to do. Say for example we have an action that changes state on our app, maybe a counter that when a button is clicked this action increments by 1. This action would be increment

5. Reducer
    1. Describes how your actions transform your state into the next state
6. Dispatch
   1. Executes the action to the reducer. then the store gets updated.



### Setup the code
---

1. If you haven't already 
   1. npx create-react-app learn-redux
   2. npm install to install our dependencies
   3. npm install redux react-redux | both packages 

2. import createStore into index.js
   1. import { createStore }  from 'redux';
3. Create the action
   ```
   //ACTION INCREMENT

const increment = () => {
  return {
    type: 'INCREMENT'
  }
}

const decrement = () => {
  return {
    type: 'DECREMENT'
  }
}
```
4. Create the reducer and set the store

```
const counter = (state = 0, action) => {
  switch(action.type){
    case 'INCREMENT':
      return state + 1;
    case 'DECREMENT':
      return state - 1;
  }
}

let store = createStore(counter)
```

5. Dispatch increment to test
   ```
   //DISPATCH
store.dispatch(increment());
   ```


## Next Lesson in Redux
---

1. Best practice is to add the store inside the indexjs then create seperate files for for our actions and reducers
   1. lets start by creating two folders inisde the src, actions and reducers
   2. next lets create index.js inside reducers
   3. next lets create counter.js and isLogged.js inside reducers folder too

2. For our counter.js reducer 
   ```
   const counterReducer = (state = 0, action){
    switch(action.type){
        case 'INCREMENT':
            return state + 1
        case 'DECREMENT':
            return state - 1    
    }   
}

export default counterReducer;
```

3. For your isLogged.js
   ```
   const loggedReducer = (state = false, action){
    switch(action.type){
        case 'SIGN_IN':
            return !state;
        
    }   
}

export default loggedReducer;
```

4. Now we can createStore inside our index.js
    1. import createStore
    2. create store const   and assign to createStore()



## How to pass two reducers at the same time into createstore!?!?
---

1. We can import the method 'combineReducers' from redux
   1. ``import { createStore, combineReducers } from 'redux';``
   2. but we want to keep our index.js clean so we will move that over to our index.js inside our reducers folder!!

reducer folder index.js imports 
```
import counterReducer from "./counter";
import loggedReducer from "./isLogged";
import { combineReducers } from 'redux';

```

2. Now that we have our reducers combined into allReducer we can then import it into our index.js main file and when we call create store we can pass allReducer

```
import allReducer from './reducers'

const store = createStore(allReducer);
```

3. When you save you may notice some errors in our reducer files
   1. make sure to add a default case to our switch statement, we return state
   2. make sure to add an arror after the arguments as its a function and needs to be syntactically correct

## Installing the Redux DevTools Extension for Chrome
--

1. (Redux Extension Chrome Store)[https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd/related?hl=en]
2. 
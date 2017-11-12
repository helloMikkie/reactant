# reactant

## Introducing JSX Syntax
file: index.js
```jsx
import React from 'react';
        import ReactDOM from 'react-dom';

        ReactDOM.render(<h1>Hello World</h1>,
         document.getElementById('root'));
```
this is how you should enclose your elements:
```jsx
const element = <div>
  <span>Hello, </span>
  <span>Jane</span>
</div>;
```
#### Evaluating JavaScript expressions in JSX
```jsx
const name = "Jane";
        const element = <p>Hello, {name}</p>
```
or
```jsx
const user = {
    firstName: "Jane",
    lastName: "Doe"
}
const element = <p>Hello, {user.firstName}{user.lastName}</p>
```

## Declaring React Components
folder: src > file: App.js
```jsx
import React, { Component } from 'react';

class App extends Component {

    render(){
    return (
        <div>
        Hello World Again!
        </div>
    )
    }
}
export default App;
```
file: src/index.js:
```jsx
import React from 'react';
import ReactDOM from 'react-dom';

import App from './App';

ReactDOM.render(<App/>, document.getElementById('root'));

export default App;
```

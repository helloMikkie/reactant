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
## Styling JSX Elements

### JSX inline styling
file /src/App.js
```jsx
import React, { Component } from 'react';

class App extends Component {

    render(){
    const headerStyle = {
        color: '#ff0000',
        textDecoration: 'underline'
    }
    return (
        <div>
        // alternative: 
        // <h2 style={{color:'#ff0000'}}>Hello World Again!</h2>
        <h2 style={headerStyle}>Hello World Again!</h2>
        </div>
    )
    }
  }
export default App;
```
### external CSS
file: src/App.css
```css
h2 {
    font-size: 4rem;
}
```
file: src/App.js
```jsx
import './App.css';
```
## Stateless vs Stateful Components

Two Types of Data:  
props and state  

**props** are read only and set by parent component  
**state** is defined within a component and can change during the lifecycle of a component  

src/messages/message-view.js  

```jsx
import React, { Component } from 'react';

class MessageView extends Component {
    render() {
    return(
        <div className="container">
        <div className="from">
            <span className="label">From: </span>
            <span className="value">John Doe</span>
        </div>
        <div className="status">
            <span className="label">Status: </span>
            <span className="value"> Unread</span>
        </div>
        <div className="message">
            <span className="label">Message: </span>
            <span className="value">Have a great day!</span>
        </div>
        </div>
    )
    }
}

export default MessageView;
```
file: src/App.css
```css
container {
    margin-left: 40px;
}

.label {
    font-weight: bold;
    font-size: 1.2rem;
}

.value {
    color: #474747;
    position: absolute;
    left: 200px;
}

.message .value {
    font-style: italic;
}
```
src/App.js
```jsx
import React, { Component } from 'react';

import './App.css';
import MessageView from './messages/message-view';

class App extends Component {
    render(){
    return (
        <MessageView />
    )
    }
}

export default App;
```
#### using funcional syntax

file: src/messages/message-view.js
```jsx
import PropTypes from 'prop-types';

export default function MessageView({message}) {
    return (
    <div className="container">
        <div className="from">
        <span className="label">From: </span>
        <span className="value">{message.from}</span>
        </div>
        <div className="status">
        <span className="label">Status: </span>
        <span className="value">{message.status}</span>
        </div>
        <div className="message">
        <span className="label">Message: </span>
        <span className="value">{message.content}</span>
        </div>
    </div>
    );
}

MessageView.propTypes = {
    message: PropTypes.object.isRequired
}

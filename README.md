# 🌈 React Cheat Sheet

> A simple cheat sheet for facilitate the process in the workshops and event about React. Let me know if you see any problem, I'll love a pull request for improve this document.

## Table of contents

- [x] [Installation](#installation)
- [x] [No configuration](#no-configuration)
- [x] [ReactDOM](#reactdom)
- [x] [Component](#component)
- [x] [Composition](#composition)
- [x] [Module component](#module-component)
- [x] [Hot Module Replacement](#hot-module-replacement)
- [x] [Props](#props)
- [x] [State](#state)
- [x] [Methods and Events](#methods-and-events)
- [x] [State manipulation](#state-manipulation)
- [ ] [Refs](#refs)
- [ ] [Keys](#keys)
- [ ] [Component Lifecycle](#component-lifecycle)
- [ ] [Inline Styles](#inline-styles)
- [ ] [React Router](#react-router)
- [ ] [Storybook](#storybook)
- [ ] [Tests](#tests)
- [ ] [a11y](#a11y)
- [ ] [API comunication](#api-comunication)
- [ ] [Flux](#flux)
- [ ] [Redux](#redux)
- [ ] [MobX](#mobx)
- [ ] [Best Practices](#best-practices)
- [ ] [Concepts](Concepts)
    - [ ] [Immutable](#immutable)
    - [ ] [Functionnal programing](#functionnal-programing)
    - [ ] [Virtual Dom](#virtual-dom)

---

## Installation

* Add the tags in your HTML
    ```HTML
    <script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin></script>
    ```
* Run this scripts in your terminal
    ```SSH
    $ npm install react react-dom
    ```
 
---
 
## No configuration

Just start with React no configuration (run the scripts bellow in your terminal)
* Install the React
    ```SSH
    $ npm install -g create-react-app
    ```
* Create your application (change `myApp` to your application name)
    ```
    $ create-react-app myApp
    ```
* Go to the application folder and install the dependencies
    ```
    $ cd myApp
    $ npm install
    ```
* Start your application
    ```
    $ npm start
    ```
* Go to the browser by `URL` bellow and see your beautiful application
    [localhost:8080](http://localhost:8080)
    
---

## ReactDOM

```JS
import React, { Component } from 'react';
import ReactDOM from 'react-dom';

class MyComponent extends Component {
    ReactDOM.render( <h1>Hello React Ladies</h1>, document.getElementById('root') );
```

---

## Component

```JS
import React, { Component } from 'react';
import ReactDOM from 'react-dom';

class MyComponent extends Component {
    render() {
        return (
            <div className="main">
                <h1>Olá Mundo</h1>
            </div>
        );
    }
}

ReactDOM.render(
    <MyComponent />, 
    document.getElementById('root')
);
```
## Composition

```JS
import React, { Component } from 'react';
import ReactDOM from 'react-dom';

class Love extends Component {
    render() {
        return (
            <div clssName="love">
                <h1>My love</h1>
            </div>
        );
    }
}

class LoveList extends Component {
    render() {
        return (
            <div>
                <Love />
                <Love />
                <Love />
                <Love />
            </>
        );
    }
}

ReactDOM.render(
    <Love />,
    document.getElementById(´root´)
);

```

## Module component

```JS
//App.js
import React, { Component } from 'react';

class App extends Component {
    render() {
        return (
            <div className="app">
                <p>My App</p>
            </div>
        );
    }
}

export default App
```

```JS
//Index.js
//Index.js
import React, { Component } from 'react';
import ReactDOM from 'react-dom';
import App from './App.js';

class Index extends Component {
    render() {
        return (
            <div className="app">
                <App />
            </div>
        );
    }
}


ReactDOM.render (
    <Index />,
    document.getElementById('root')
);

```

---

## Hot Module Replacement
* Retain application state which is lost during a full reload.
* Save valuable development time by only updating what's changed.
* Tweak styling faster -- almost comparable to changing styles in the browser's debugger.

```JS
import React, { Component } from 'react';
import ReactDOM from 'react-dom';
import MyComponent from './MyComponent';

ReactDOM.render( <MyComponent />, document.getElementById('root') );

if (module.hot) {
    module.hot.accept();
}
```

---

## Props

```JS
import React, { Component } from 'react';
import ReactDOM from 'react-dom';

class App extends Component {
    render() {
        return (
            <div className="app">
                <p>My App {this.props.name}</p>
            </div>
        );
    }
}

class Index extends Component {
    render() {
        return (
            <div className="app">
                <App name="Simone"/>
            </div>
        );
    }
}

ReactDOM.render (
    <Index />,
    document.getElementById('root')
);

```

## State

```JS
import React, { Component } from 'react';
import ReactDOM from 'react-dom';

class App extends Component {
    constructor(props) {
        super(props);
        this.state = {messages: 0};
    } 

    render() {
        return (
            <div className="app">
                <p>My messages: {this.state.messages}</p>
            </div>
        );
    }
}

ReactDOM.render (
    <App />,
    document.getElementById('root')
);

```

## Methods and Events

```JS
import React, { Component } from 'react';
import ReactDOM from 'react-dom';

class App extends Component {

    escreve() {
      console.log("Eu te amo");
    }

    render() {
        return (
            <div className="app">
                <button onClick={this.escreve}>save</button>
            </div>
        );
    }
}

ReactDOM.render (
    <App />,
    document.getElementById('root')
);

```

## State manipulation

```JS
import React, { Component } from 'react';
import ReactDOM from 'react-dom';

class App extends Component {
    constructor(props) {
        super(props);
        this.state = {messages: 0};
    } 

    escreve() {
      this.setState({messages: this.state.messages + 1});
    }

    render() {
        return (
            <div className="app">
                <p>My messages: {this.state.messages}</p>
                <button onClick={this.escreve.bind(this)}>save</button>
            </div>
        );
    }
}

ReactDOM.render (
    <App />,
    document.getElementById('root')
); 

```

```JS
import React, { Component } from 'react';
import ReactDOM from 'react-dom';

class App extends Component {
    constructor(props) {
        super(props);
        this.state = {messages: ['love', 'sex', 'code']};
    } 
    
    escreve() {
      this.setState({messages: this.state.messages.push('text')});
    }
    

    render() {

      let listMessages = this.state.messages.map((msg) => {
        return (<li>{msg}</li>)
      })

        return (
            <div className="app">
              <button onClick={this.escreve.bind(this)}>save</button>
              {listMessages}
            </div>
        );
    } 
}

ReactDOM.render (
    <App />,
    document.getElementById('root')
);

```

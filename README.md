# React 

## Table of contents

- [ ] [Setup](#setup)
- [x] [Component](#component)
- [x] [Composition](#composition)
- [x] [Module component](#module-component)
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

## Setup


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

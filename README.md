# React 

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

## SubComponent

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

## Manipulating the state

´´´JS
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

´´´´
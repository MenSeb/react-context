<div align="center">
    <img src="https://github.com/MenSeb/react-context-reducer/blob/master/demo/logo.svg" width="250" height="250" alt="React Context Reducer" />
</div>

<h1 align="center">
    React Context Reducer
</h1>

<p align="center">
    Use React context with the reducer pattern.
</p>

<br>

![npm](https://img.shields.io/npm/v/@menseb/react-context-reducer)
![NPM](https://img.shields.io/npm/l/@menseb/react-context-reducer)
[![Build Status](https://travis-ci.com/MenSeb/react-context-reducer.svg?token=8TzPeku6xVPzgovguE6A&branch=master)](https://travis-ci.com/MenSeb/react-context-reducer)
[![CodeFactor](https://www.codefactor.io/repository/github/menseb/react-context-reducer/badge?s=d3b4606115f45a496c1e67e48d9651fba4afdd04)](https://www.codefactor.io/repository/github/menseb/react-context-reducer)
[![Coverage Status](https://coveralls.io/repos/github/MenSeb/react-context-reducer/badge.svg?branch=master)](https://coveralls.io/github/MenSeb/react-context-reducer?branch=master)

## Installation

```
npm i @menseb/react-context-reducer
```

## How to use

- Import the Provider

```javascript
import { Provider } from '@menseb/react-context-reducer';
```

- Use your actions (required)

```javascript
export const actions = {
    foo: (state, arguments) => {
        const { bar } = state;

        const { baz } = arguments;

        return { ...state, bar: baz };
    }
}
```

- Create your initial value (optional)
```javascript
export const initial = { bar: false };
```

- Create your configuration function (optional)
```javascript
export function config(initial) {
    const { bar } = initial;

    return { bar: !bar };
}
```

- Export your context
```javascript
export const Context = createReactContext({
    actions,
    config,
    initial,
});

// const { Consumer, Povider, useReactContext } = Context;
```

- Import your context and setup its Provider
```javascript
import Context from 'path/to/my/context.js';
import App from 'path/to/my/app.js';

render(
    <Context.Provider>
        <App>
    </Context.Provider>,
    document.getElementById('root')
);
```

- Use your context with Consumer or hook
```javascript
import Context from 'path/to/my/context.js';

export default function App() {
    return (
        <Context.Consumer>
            {({ api, state }) => (
                <>
                    <p>{`state: ${state}`}</p>
                    <button onClick={() => api.foo({ baz: true })}>
                        Click
                    </button>
                </>
            )}
        </Context.Consumer>
    );
}

// or

export default function App() {
    const { api, state } = Context.useReactContext();

    function click() {
        return api.foo({ baz: true });
    }

    return (
        <>
            <p>{`state: ${state}`}</p>
            <button onClick={click}>
                Click
            </button>
        </>
    );
}
```

## ISC License

ISC License

Copyright (c) 2020, Sébastien Menard

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
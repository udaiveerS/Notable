---
title: 006- Context
tags: [ReactNotes]
created: '2019-04-10T06:39:05.743Z'
modified: '2019-04-11T01:59:56.910Z'
---

# 006- Context 

## React context api 
```
/path/to/your/data_directory
├─┬ src
│ ├── foo.js
│ ├── bar.js
│ └── …
└─┬ context
  ├── auth-context.js
  ├── bar.md
  └── …
```
Context allows application to track global state for a application EG.. 

```
import React from 'react';


const authContext = React.createContext({
    authenticated: false,
    login: () => {}
});

export default authContext;
``` 

* context can be used with class based components by adding a static property ```componentType```

```
import React, {Component} from 'react';
import Person from "./Person/Person";
import withClass from "../../hoc/withClass";
import AuthContext from '../../context/auth-context';

const classes = {
    Persons: 'poopie scoopie'
};

class Persons extends Component {

    static contextType = AuthContext;

``` 

now you can acces this anywhere with the property ```this.contextType.__PROP_NAME__``` 

## functional component context 

* use the   ```usedContext({}) 

``` 



// import useContext (or we could write React.useContext)
import React, { useContext } from 'react';

const NumberContext = React.createContext();
// ...

function Display() {
  const value = useContext(NumberContext);
  return <div>The answer is {value}.</div>;
}
``` 

you can now acces the context object with each render call or even in other hooks 




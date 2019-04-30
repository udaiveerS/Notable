---
title: 005-Component render optimization
tags: [ReactNotes]
created: '2019-04-10T06:39:05.743Z'
modified: '2019-04-11T01:44:18.376Z'
---

# 005-Component render optimization


## React.memo

* Used to optamize functional components by autowatching the pops that are loaded on the component, this can cause overhed if used loosly. 

## shouldComponentUpdate

* a lifecycle method that can be use to optamize the rendering of a react component by watching prop changes 


## PureComponent 

* a special react component that can be extended and overrides that shouldComponentUpdate method that automaticly watches components for changes 




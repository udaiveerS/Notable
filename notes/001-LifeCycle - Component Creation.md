---
title: 001-LifeCycle - Component Creation
tags: [ReactNotes]
created: '2019-04-10T06:39:05.743Z'
modified: '2019-04-10T07:20:46.349Z'
---

# 001-LifeCycle - Component Creation

React has lifecycle events for each component 

<p align="center">
  <img src="@attachment/react_notes/react_lifecycle.png" width="592">
</p>


* **constructor** is the first thing called for a prop and can be overridden but you must calle super(prop) 

* **getDerivedFromPropState** is used to sync state if some props passed in are updated by the time you reach this function you can _sync state_ 

* **render** is the method that renders the jsx for the component 

* **component did mount** is the most frequently used method in component lifecycle hooks, cause use to set state after a Ajax request, but not as soon as this fucniton gets executed 





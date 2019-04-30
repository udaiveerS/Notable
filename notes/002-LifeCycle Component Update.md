---
title: 002-LifeCycle Component Update
tags: [ReactNotes]
created: '2019-04-10T06:39:05.743Z'
modified: '2019-04-10T08:44:07.299Z'
---

# 002-LifeCycle Component Update
React has lifecycle events for each component 

<p align="center">
  <img src="@attachment/react_notes/react_lifecycle_update.png" width="592">
</p>


* **getDerivedStateFromPropState** is used to sync state if some props passed in are updated by the time you reach this function you can _sync state_ 

* **shouldComponentUpdate** can be used to cancle an upate 

* **getShapShotBeforeUpdate** get the previous state before the update to get acces to prev scroll location, state ... etc 

* **componentDidUpdate** after componet is updated you can do some state upaate but should be done in a promise or it will cause a extra re-render cycle 

* **ComponentWillUnmount** this function 





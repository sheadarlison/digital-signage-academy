---
layout: developer-post
title:  "Development FAQ"
date:   2014-10-01 10:52:00
category: developer/common-header
parent-order: 0
order: 1
---

## How do I change the location CH makes Core API requests to?

You can overwrite ```CORE_URL``` value in your app, as in

```js
angular.module("myapp")
  .value("CORE_URL", "https://rvacore-test.appspot.com/_ah/api")
```

And Common Header will direct all Core API calls to that location.

## Can I use ui-router instead of ngRoute?

Actually, Common Header does not use any routing per se. It is up to the app that uses CH to decide what routing library it uses.

## How do I dynamically generate routes for navigation menu? Can I use ui-sref?

[settinghead](https://github.com/settinghead): I tried adding ui-sref option, but failed. There was some strange error that kept occurring.
So instead of using ui-sref, change the ```navOptions``` array on the scope:
```javascript
var updateNavigationMenu = function () {
   $scope.navOptions = [..., {
     title: "Dynamic Menu Item",
     link: $state.href("myState")
   }, ...]};
```

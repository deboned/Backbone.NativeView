Backbone.NativeView
===================

A drop-in replacement for Backbone.View that uses only native DOM methods for
element selection and event delegation. It has no dependency on jQuery.


To Use:
-------
Load Backbone.NativeView with your favorite module loader or add as a script
tag after you have loaded Backbone in the page. Wherever you had previously
inherited from Backbone.View, you will now inherit from Backbone.NativeView.

```js
var MyView = Backbone.NativeView.extend({
  initialize: function(options) {
    // ...
  }
})
```

As an alternative, you may extend an existing View's prototype to use native
methods:

```js
var MyView = Backbone.View.extend({
  initialize: function(options) {
    // ...
  }
});

_.extend(MyView.prototype, Backbone.NativeViewMixin);
```

Features:
---------
Delegation:
```js
var View = new NativeView(el: '#my-element');
view.delegate('click', view.clickHandler);
```

Undelegation with event names or namespaces
```js
var View = new NativeView(el: '#my-element');
view.delegate('click', view.clickHandler);
view.delegate('click.mynamespace', view.clickHandler);
view.undelegate('.mynamespace');
view.undelegate('click');
```

Requirements:
-------------
NativeView makes use of `querySelector`/`querySelectorAll`. For IE7 and below
you must include a polyfill for querySelector on `document` and `Element.prototype`.

Notes:
------
* The `$el` property no longer exists on Views. Use `el` instead.
* The `$` method returns a NodeList instead of a jQuery context. You can
  iterate over either using `_.each`.


With many thanks to @wyuenho for his initial code.


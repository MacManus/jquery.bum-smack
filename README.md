For when you hit the bottom... of a dom element while scrolling.

### Motivation

Infinite scrolling plugins do **way too much**: 
internally keep track of a scroll hitting the bottom of an element, fetch, then render, and rebind.

If you have a backbone app that requires infinite scrolling, then you often 
have a list view that listens to a collection and handles rendering. **Infinite scrolling
should be as simple as being notified when you've hit the bottom of the (scrollable) element,
and letting you call fetch on the proper collection.**

After you've `smack`ed the bottom, you have the option to call smack (if you want to be notified again).
For example, after you've loaded another page of results, you would want to detect when you've
smacked the bottom of the element. If you don't have any more results, then you wouldn't want to keep being notified.

### Demo:

http://jsfiddle.net/mrjoelkemp/TLdSW/1/

### Usage

Detect when you've scrolled to the bottom of the element

```javascript
$(selector).smack()
    .done(function () {
      // Do stuff like fetch from a collection
    });
```

Detect when you've scrolled through 80% of the element

```javascript
$(selector).smack({ threshold: 0.8 })
    .done(function () {
      // Do stuff like fetch from a collection
    });
```

Detect when smacking the bottom of the page itself

```javascript
$(window).smack()
    .done(function () {
      // Do stuff like fetch from a collection
    });    
```

### Options

*threshold*: float between 0 and 1

* represents scrolling through anywhere from 0 to 100% of the element
* default = 1; you're notified when you hit the bottom of the element


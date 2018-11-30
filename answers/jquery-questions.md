# JQUERY Questions

#### Describe event delegation in jQuery.

Event delegation allows us to attach a single event listener, to a parent element, that will fire for all descendants matching a selector, whether those descendants exist now or are added in the future.


```
<html>
<body>
<div id="container">
    <ul id="list">
        <li><a href="http://domain1.com">Item #1</a></li>
        <li><a href="/local/path/1">Item #2</a></li>
        <li><a href="/local/path/2">Item #3</a></li>
        <li><a href="http://domain4.com">Item #4</a></li>
    </ul>
</div>
</body>
</html>
```
When an anchor in our #list group is clicked, we want to log its text to the console. Normally we could directly bind to the click event of each anchor using the .on() method:

```
// Attach a directly bound event handler
$( "#list a" ).on( "click", function( event ) {
    event.preventDefault();
    console.log( $( this ).text() );
});
```
While this works perfectly fine, there are drawbacks. Consider what happens when we add a new anchor after having already bound the above listener:

```
// Add a new element on to our existing list
$( "#list" ).append( "<li><a href='http://newdomain.com'>Item #5</a></li>" );
```

If we were to click our newly added item, nothing would happen. This is because of the directly bound event handler that we attached previously. Direct events are only attached to elements at the time the .on() method is called. In this case, since our new anchor did not exist when .on() was called, it does not get the event handler.

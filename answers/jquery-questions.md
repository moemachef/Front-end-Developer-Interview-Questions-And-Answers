# JQUERY Questions

#### Describe event delegation in jQuery.


Suppose you’re developing a single page application that sells pictures of kittens. When the page loads, the first 20 kittens are displayed. As the user scrolls down the page, more kittens are loaded. Our HTML is shown below.

```
<section id="cats">
  <ul>
    <li>
      <img src="http://placekitten.com/200/200" alt=""/>
      <a href="/moreinfo">More info</a>
      <button>Add to cart</button>
    </li>
    ...
  </ul>
</section>
```
The key is the optional second argument to on(). By passing a selector here, on() knows it’s dealing with a delegated event handler rather than a directly bound event handler.

Our event handling code is a lot simpler now too. By getting a hold of event.target, and switching on it’s tagName, we can tell which element fired the event and can respond appropriately. Plus, we no longer have to attach event handlers for elements loaded in $(window).scroll, as the events fired by these new elements are delegated to the parent element.

A potential ‘gotcha’ to be aware of when using event delegation is that any event handlers attached to child elements are handled before the deletated event handler fires. Therefore, it’s possible for a child event handler to call event.stopPropagation() or return false, which will prevent the event from bubbling up to the delegated event handler, and leave you scratching your head as to why your event isn’t being delegated.

```
$(document).ready(function() {
  $('#cats')
    .on('click', 'img, a, button', function(event) {
      event.preventDefault();
      var target = event.target;

  switch(target.tagName.toLowerCase()) {
    case 'img':
      loadImage();
      break;
    case 'a':
      moreInfo();
      break;
    case 'button':
      addToCart();
      break;
    default:
      // do nothing
  }
});

  $(window).scroll(function() {
    var fragment = loadNewKittens();
    fragment.appendTo('#cats ul');
  });
});
```

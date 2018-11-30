# SASS Questions

#### How to define color variable in SASS?

Variables in SCSS are prefixed with a '$' sign and can be named whatever you like. Here we will set up a few basic color variables to be used later on in our stylesheets.

```
$color-red: #FF0000;
$color-green: #00FF00;
$color-blue: #0000FF;
```
Now that we've defined some color variables, it's time to put them to work. You can use SCSS variables just like you would the normal values for any CSS property, just make sure to include the '$' sign prefix to indicate variable status.

```
h1 { color: $color-red; }
p { color: $color-green; }
a { color: $color-blue; }
```


#### How to use mixins in SASS?

Creating a Mixin is very simple, all we have to do is use @mixin command followed by a space and our Mixin name, then we open and close our curly brackets. Something like this.

```
@mixin flex {
    // write the css here
    display: -webkit-flex;
    display: flex;
}
```

Now that we know how to declare Mixins, we can now learn how to use them in our SCSS code.To use a Mixin, we simply use @include followed by the name of the Mixin and a semi-colon.

```
.row {
    @include flex;
}
```



# HTML Questions

#### What does a `doctype` do?

It specifies which markup standard the page is using. With the information, the
browser determines how to render the page according to the page's source code.

#### What's the difference between standards mode and quirks mode?

They are modes used by browser rendering engines. In the standards mode, the
engine will render a page as HTML and CSS specifications specify. The quirks
mode is to render legacy pages written before these standards are fixed. The
legacy pages contain non-standard behaviours emulated in old browsers such as
Internet Explorer 5 or Navigator 4.

We can enforce browsers to use standards mode with a `<!DOCTYPE html>` tag.

#### What's the difference between HTML and XHTML?

XHTML is based on XML, and thus requires the source to be well-formed. Since XHTML is more strict than HTML, less pre-processing is needed by the rendering engine.

XHTML should be served as application/xhtml+xml for you to take advantage of the benefits, otherwise XHTML will be treated as ordinary HTML. Serving it as 'application/xhtml+xml' is not common on the web due to Internet Explorer, which cannot handle XHTML.

#### Are there any problems with serving pages as `application/xhtml+xml`?

IE < 8 will show a download dialog for the pages, instead of rendering them
properly.

#### How do you serve a page with content in multiple languages?

Use `lang` (or `xml:lang` for XHTML) in tags. Also metadata and
`Content-Language` HTTP header can be used.

#### What kind of things must you be wary of when design or developing for multilingual sites?

- `hreflang` attr in link
- `dir` attr indicating language direction, such as `rtl`
- `<meta charset='UTF-8'>`
- `font-size` for `:lang({language_code})` selectors in CSS
- difference in word langth for each language
- Using symbols which acceptable in some languages and other doesn't 

#### What are `data-` attributes good for?

It makes HTML elements contain extra information without using non-standard
attributes, or other hacks like that.

#### Consider HTML5 as an open web platform. What are the building blocks of HTML5?


- More semantic text markup
- New form elements
- Video and audio
- New javascript API
- Canvas and SVG
- New communication API
- Geolocation API
- Web worker API
- New data storage


#### Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.

LocalStorage:

- Web storage can be viewed simplistically as an improvement on cookies, providing much greater storage capacity. Available size is 5MB which considerably more space to work with than a typical 4KB cookie.
- The data is not sent back to the server for every HTTP request (HTML, images, JavaScript, CSS, etc) - reducing the amount of traffic between client and server.
- The data stored in localStorage persists until explicitly deleted. Changes made are saved and available for all current and future visits to the site.
- It works on same-origin policy. So, data stored will only be available on the same origin.


Cookies:

- We can set the expiration time for each cookie
- The 4K limit is for the entire cookie, including name, value, expiry date etc. To support most browsers, keep the name under 4000 bytes, and the overall cookie size under 4093 bytes.
- The data is sent back to the server for every HTTP request (HTML, images, JavaScript, CSS, etc) - increasing the amount of traffic between client and server.


sessionStorage:

- It is similar to localStorage.
- Changes are only available per window (or tab in browsers like Chrome and Firefox). Changes made are saved and available for the current page, as well as future visits to the site on the same window. Once the window is closed, the storage is deleted
- The data is available only inside the window/tab in which it was set.
- The data is not persistent i.e. it will be lost once the window/tab is closed. Like localStorage, it works on same-origin policy. So, data stored will only be available on the same origin.

#### Describe the difference between `<script>`, `<script async>` and `<script defer>`.

- `<script>` stops rendering process, and download and run a script.
- `<script async>` don't stop rendering process while asynchronously
  downloading a script. When finishing download, it stops rendering and runs the
  script.
- `<script defer>` don't stop rendering process while asynchronously
  downloading a script. When finishing rendering, it runs the script.

#### Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?

You usually put the <link> tags in between the <head> to prevent Flash of Unstyled Content which gives the user something to look at while the rest of the page is being parsed.

Since Javascript blocks rendering by default, and the DOM and CSSOM construction can be also be delayed, it is usually best to keep scripts at the bottom of the page.

Exceptions are if you grab the scripts asynchronously, or at least defer them to the end of the page.

#### What is progressive rendering?

When a HTTP response is flushed multiple times, a browser doesn't wait until
the whole content is loaded and renders each part earlier.

#### Have you used different HTML templating languages before?

Yes. Jinja2 and Django template language in Python. Jade and EJS in JavaScript.
Some more in other languages.

#### What is Semantic HTML?

Semantic HTML or semantic markup is HTML that introduces meaning to the web page rather than just presentation. 

For example, a ```<p>``` tag indicates that the enclosed text is a paragraph. This is both semantic and presentational because people know what paragraphs are, and browsers know how to display them. On the flip side of this equation, tags such as ```<b>``` and ```<i>``` are not semantic. They define only how the text should look (bold or italic), and don't provide any additional meaning to the markup.

Examples of semantic HTML tags include:

- ```Header tags <h1> through <h6>```
- ```<blockquote>```
- ```<code>```
- ```<em>```

There are many more semantic HTML tags to use as you build a standards-compliant website.

https://www.lifewire.com/why-use-semantic-html-3468271



#### What is the Pros and Cons of each putting script in head - putting script in end of body tag - using Async - using Defer ?

https://medium.com/@raviroshan.talk/async-defer-javascript-loading-strategies-da489a0ba47e

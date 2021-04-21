# General Questions

#### What did you learn yesterday/this week?

I studied about a Node.js ORM called Bookshelf.js and Express middleware
implementation. I also solved some problems in
[Project Euler](https://projecteuler.net) using Haskell, in which I am
currently interested

#### What excites or interests you about coding?

I'm generally interested in quite everything about coding. Nowadays I'm
especially fascinated by Haskell, one of the most beautiful languages I've
ever experienced.

Also I like to create tools and services I and many others can be helped by
and enjoy using.

#### What is a recent technical challenge you experienced and how did you solve it?

Recently I worked on building a web service and we needed to write test cases
for APIs of it. When writing a test case, it needs several database entities
which will be used in the test case, and it is really a pain to write all the
insertion code for the database and cleanup at the end.

To resolve the problem, I implemented concepts called 'state' and 'environment'.
'State' refers to a database instance which a session contains. 'Environment'
helps the 'state' manage its own entities. With the concepts, entities can be
created and managed easily in each test session and also cleaned all together
with the `cleanup` method implemented in a state instance.

#### What UI, Security, Performance, SEO, Maintainability or Technology considerations do you make while building a web application or site?

- **UI**: I like minimal UI which contains only what it should. I believe it
  results in the better user experience, as a user knows what to do
  intuitively.
- **Security**: I always try to make both frontend and backend secure,
  concerning CSRF, XSS, etc.
- **Performance**: I consider space and time complexity for the algorithms and
  logics I use and write.
- **SEO**: Set meta tags for search engines and consider and consider
  server-side rendering for SPA.
- **Maintainability**: Try to keep the source code consistent and make objects
  immutable. Use statically typed languages such as TypeScript. Use CI with
  tests and lints.
- **Technology**: I like to learn new technologies, but if the project is
  in production, I would consider using technologies which is well-documented
  and widely used.

#### Talk about your preferred development environment.

I like to work in terminal shell environments. For the time being, my favourite
dev environment are like below:

- OS X
- iTerm2
- Tmux
- Vim

Nevertheless, I don't want to say they are the silver bullets for everything. I
always try to find the best environment for each language and requirement.

#### Which version control systems are you familiar with?

Git. Not really familiar with others, but at least have experience of
Subversion and Mercurial too.

#### Can you describe your workflow when you create a web page?

I usually use Node.js to build a web page, so will describe the workflow with
it.

1. Decide a CSS preprocessor. I may consider using SCSS, but Less and Stylus
   are also viable options.
1. Decide a HTML template engine. I may go with Pug(formerly Jade).
1. Decide a JavaScript preprocessor or other languages being compiled to it.
   I may go with TypeScript or ES6 with Babel.
1. Decide a task manager. I recently like to just use NPM scripts instead of
   using huge task managers like Gulp or Grunt.
1. Write tests and make them fail.
1. Write app code and check the tests succeed.
1. Set CI.
1. Publish the code and check a task in CI succeed.

#### If you have 5 different stylesheets, how would you best integrate them into the site?

Use a CSS preprocessor to nest them with `@import` statements in class names
for each stylesheet, and merge them into a built file. In production, minify
the built file with a CSS minifier.

#### Can you describe the difference between progressive enhancement and graceful degradation?

**Progressive enhancement** is a way to implement a web page where basic
features, which are supported by most environments, are implemented first and
then progressively enhance them for advanced environments.

On the other hand, **graceful degradation** is an opposite. The advanced
features are freely implemented at any time, and additional works are done
to support the environment where the features don't work well.

#### How would you optimize a website's assets/resources?

Minimise CSS and JavaScript using minifier(or uglifier), archive them using
gzip, use separated file servers, use CDN, etc.

#### How many resources will a browser download from a given domain at a time?

It depends on browser implementations. Usually 6 to 8 in the modern browsers,
and less in the old browsers.

###### What are the exceptions?

When we use several subdomains pointing the same domain, we can increase the
concurrency level of the download.

#### Name 3 ways to decrease page load (perceived or actual load time).

- Use minifier and gzip to decrease the page size *- actual*
- Show spinner or progress bar *- perceived*
- Preload the page before actually loading it using libraries like
  [InstantClick](http://instantclick.io) *- both actual and perceived*

#### If you jumped on a project and they used tabs and you used spaces, what would you do?

- I would use tabs because it is the convention used for the project.
- Introduce a linter or other scripts to ensure indentations are consistent
- Use a tool like [EditorConfig](http://editorconfig.org) to configure editors
  team members are using automatically

#### Describe how you would create a simple slideshow page.

```html
<div class='slide-page'>...</div>
<div class='slide-page'>...</div>
<div class='slide-page'>...</div>
```

```css
html, body, .slide-page {
  width: 100%;
  height: 100%;
}

.slide-page {
  position: fixed;
  top: 0;
  left: 0;
  display: none;
}

.slide-page:first-child {
  display: block;
}
```

```js
window.addEventListener('click', () => {
  document.querySelector('.slide-page').remove();
});
```

#### If you could master one technology this year, what would it be?

Haskell. Haskell really helps developers a lot to perform much better, even
though they don't really use Haskell directly because through learning Haskell,
we can have better understand for other languages as well. It has been, and
will be a well-designed language and many other languages have been adopting
functional concepts from it and I would say it is fascinating and valuable
language for every developer.

#### Explain the importance of standards and standards bodies.

Standards describe how a thing does and should work. It is extremely
important especially in software, because the *thing* can be used by many
people for different perposes. For example, there are several engines for
JavaScript including V8, JavaScriptCore, Rhino, etc, and if there is no
standard for the language, developers and users cannot feel ensured when doing
something with it.

Standards bodies, in the same manner, do a key role to form a standards and
are essential in everywhere including both software and hardware.

#### What is Flash of Unstyled Content? How do you avoid FOUC?

It is caused when content is loaded before styles are applied to the content.
It happens when style tags are placed after other content, or applied
asynchronously, for example, by scripts.

To avoid FOUC, the styles should be placed in order that they can be loaded
and applied in the same rendering process as HTML elements do. The easiest way
is to place them in the `head`, and avoid applying styles by scripts at the
first load.

#### Explain what ARIA and screenreaders are, and how to make a website accessible.

They are for accessibility. To make a website accessible, we should try to
follow the usage of HTML elements, for example, `h1` for headers and `section`
for sections. Also it's good to take care of using visual contents, such as
not forgetting to add an `alt` attribute to `img` tags.

#### Explain some of the pros and cons for CSS animations versus JavaScript animations.

###### CSS animations
- **pros**: They use GPU, so they are CPU-efficient. Don't consume JavaScript
  event loops.
- **cons**: Hard to handle, as CSS doesn't contain logics. Not supported in
  old browsers.

###### JavaScript animations

Opposite to CSS animations

#### What does CORS stand for and what issue does it address?

CORS stands for cross-origin resource sharing. There could be situation where
some resources should be allowed from sources having different origin. CORS
is a standard to enable cross-site HTTP requests for:

- AJAX API call
- Web Fonts
- WebGL textures
- Image/video frames drawn to a canvas using drawImage
- Stylesheets
- Scripts

#### What do you know about design patterns and which one is your favourite?

In general there are 3 main categories: Creational - Structural - Behavioural.


My favourite is Factory pattern which is from the creational category, from its name we give it input and it produces output and thus it provides clean code , reusability and flexibility.

On the other hand an anti-pattern represents bad practice, An example of an anti-pattern would be modifying the ```Object``` class prototype. Almost all objects in JavaScript inherit from Object (remember that JavaScript uses prototype-based inheritance) so imagine a scenario where you altered this prototype. Changes to the Object prototype would be seen in all of the objects that inherit from this prototype—which would be most JavaScript objects. This is a disaster waiting to happen.

Another example, similar to one mentioned above, is modifying objects that you don’t own. An example of this would be overriding a function from an object used in many scenarios throughout the application. If you are working with a large team, imagine the confusion this would cause; you’d quickly run into naming collisions, incompatible implementations, and maintenance nightmares.

Similar to how it is useful to know about all of the good practices and solutions, it is also very important to know about the bad ones too. This way, you can recognize them and avoid making the mistake up front.


https://www.toptal.com/javascript/comprehensive-guide-javascript-design-patterns

https://www.youtube.com/watch?v=kuirGzhGhyw

https://dev.to/aershov24/9-unusual-design-patterns-interview-question-with-answers-3gjl

https://scotch.io/bar-talk/4-javascript-design-patterns-you-should-know

https://codingcompiler.com/javascript-design-patterns/


#### What are Web Components?

https://developer.mozilla.org/en-US/docs/Web/Web_Components

https://css-tricks.com/an-introduction-to-web-components/


#### What are the differences between Angular , React and Vue?

https://dzone.com/articles/react-vs-angular-vs-vuejs-a-complete-comparison-gu

https://medium.com/@onlineinerview/angular-react-or-vue-which-to-choose-63fe407890e1


#### What are the differences between Grunt and Rollup?

https://medium.com/thron-tech/rollup-is-a-great-bundling-tool-but-is-it-the-one-you-should-use-cdb9ea175056

https://stackshare.io/stackups/grunt-vs-rollup


#### What is tree shaking?

The Tree Shaking is a concept of dead code elimination from projects. The code present in your project but neither referenced nor used will be dropped here. It will eliminate the unused modules during the build process, making user application lightweight.


#### What is Jenkins?

Jenkins is a free open source Continuous Integration tool and automation server to monitor continuous integration and delivery. It is written in Java.

It is known as an automated Continuous Delivery tool that helps to build and test the software system with easy integration of changes to the system. Jenkins follows Groovy Scripting.

Also, it enables developers to continuously check in their code and also analyze the post-build actions. The automation testers can use to run their tests as soon as the new code is added or code is modified.

https://www.softwaretestinghelp.com/jenkins-interview-questions/


#### What are the advantages of GraphQL over REST ?

https://medium.com/@back4apps/graphql-vs-rest-62a3d6c2021d

https://www.youtube.com/watch?v=PeAOEAmR0D0


#### What does cherry-picking a commit with Git mean?

Cherry picking in Git means to choose a commit from one branch and apply it onto another. This is in contrast with other ways such as merge and rebase which normally apply many commits onto another branch.

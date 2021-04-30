# React Questions

#### Explain the upsides and tradeoffs of using the DllPlugin as opposed to CommonChunksPlugin.

CommonsChunkPlugin rationale


Project author defines a number of application entry points that will produce a bundle each. Typical examples are vendor, polyfills, main, but for example your app could be split in several independent "areas" that makes sense to load separately (like e.g. login, main, settings).

Project author then defines which one of those bundles, or a separate one, should contain code common to all of them. That is tipically 3rd party libraries and your own shared utilities across all entry points.

Then it is plugin responsibility to analyze and collect such common code, then put it in defined bundle. All such analysis and work happens again and again everytime you start a new build, and - in watch mode - when you modify code that is shared and happens to fall into commons bundle.

Such a split is useful both for a development build as well as for a production build. But for dev environment, let's just say that re-building code related to vendors and polyfills might take quite some time and it can be a waste when you're not really changing those parts (assuming 3rd party code you depend on is larger than your own codebase).

DllPlugin rationale


Given the same environment, for example development, project author creates two webpack configurations where there used to be one. The plugin could be applied to production environment, although it can be said that DllPlugin makes more sense in development (see below).

First webpack build configuration is needed for so-called DLLs, which are kind of close to the commons code seen before, but not exactly. To my understanding, DLLs mostly tend to group 3rd party code (vendor and polyfills) and not your own shared utility code, but again this is more an impression and not a strict rule. Anyway, here project author should group code that changes much less frequently during a normal development session. The idea, in dev environment, is to run this build every once in a while, for example when a dependency changes. And usually it is up to the developer to fire this build when s/he think is needed.

The other webpack build configuration is needed for project own code, or anyway code that changes regularly while doing dev work. This is the actual build that developer will run again and again, or will run in watch mode, and at this point it should be very much quicker as compared to the single build seen in CommonsChunk scenario.


#### Virtual DOM vs. Shadow DOM, are they the same thing?

The Virtual DOM is a tree of JavaScript objects that represent the real DOM elements.

Shadow DOM is not a standalone document like the actual DOM, but it resides in it. It's very similar to the component-based architecture of React or angular where every component has its own set of stylesheets and global styles as well. ReactJS does not use the shadow DOM for making it faster, it completely relies on the virtual one. But anyone can use this feature of HTML5 intentionally if required.

The Shadow DOM is a form of encapsulation on our elements. Think about using the ```<video>``` tag in your browser. In a video tag, your browser will create a set of video controls such as a play button, a timecode number, a scrubber progress bar etc. These elements aren’t part of your “regular DOM”, but instead, part of the “Shadow DOM”.
  
  
#### What is the diffrence between Controlled Component & Uncontrolled Component ?
  
A Controlled Component is one that takes its current value through props and notifies changes through callbacks like onChange. A parent component "controls" it by handling the callback and managing its own state and passing the new values as props to the controlled component. You could also call this a "dumb component".


A Uncontrolled Component is one that stores its own state internally, and you query the DOM using a ref to find its current value when you need it. This is a bit more like traditional HTML.

https://www.edureka.co/blog/interview-questions/react-interview-questions


#### What are Pure Components in React?

Pure Components do not depend or modify the state of variables outside their scope. These are the building blocks of Functional Programming.

https://medium.com/technofunnel/working-with-react-pure-components-166ded26ae48

#### What are the advantages of server side rendering ?

https://medium.com/walmartlabs/the-benefits-of-server-side-rendering-over-client-side-rendering-5d07ff2cefe8


#### What is Styled-Components ?

Styled components are a CSS-in-JS tool that bridges the gap between components and styling, offering numerous features to get you up and running in styling components in a functional and reusable way.

In React’s own words, styled components are “visual primitives for components”, and their goal is to give us a flexible way to style components. The result is a tight coupling between components and their styles.

Apart from helping you to scope styles, styled components include the following features:

- Automatic vendor prefixing, You can use standard CSS properties, and styled components will add vendor prefixes should they be needed.

- Unique class names Styled components are independent of each other, and you do not have to worry about their names because the library handles that for you.

- Elimination of dead styles Styled components remove unused styles, even if they’re declared in your code.

https://styled-components.com/docs/basics

https://www.smashingmagazine.com/2020/07/styled-components-react/


#### What does lifting state means in React?

https://medium.com/@jbbpatel94/react-react-state-shared-state-lifting-state-up-af17ff4e2972


#### What is Higher-Order Components in React ?

Higher-Order Components (or HOCs) in React are functions that take a component and return a new component, enhancing the original in some way.

HOCs are very useful for injecting functions, state, and additional data into components as props, as well as wrapping components with styling or more JSX. Using HOCs allow us to only extend the components that need to be extended, while at the same time keeping your codebase modular by separating specialised logic from component implementations.

https://medium.com/@rossbulat/how-to-use-react-higher-order-components-c0be6821eb6c



#### How React works under the hood ?

https://www.freecodecamp.org/news/react-under-the-hood/


#### What is the most important React Hooks you used ?

State Hook:

This useState returns value, its accessor and is initiated at the start: const [state, setState] = useState(initialState);. Thereby in retrospective, in contrast to class components by Constructor, and state manipulated functions such as handleIncrease which was bind to this scope.

Effect Hook:

Effect hook here, is used to perform side effects in functional components. From familiar user cases, it could be considered combination of methods: componentDidMount, componentDidUpdate, and componentWillUnmount. So when React renders (updates the DOM including first render) component, this hook becomes applied. Typical use cases for effect hooks are data fetching, managing subscriptions and dealing with manual DOM changes.

Context Hook:

This is applicable when using Context API introduced in React 16.3.0 to avoid props drilling. Here context hook can be used to interact with created context.

Ref Hook:

Reference hook can be used to refer React element created by render method. When there are DOM changes, ref’s .current value will be up to date.

Reducer Hook:

This can act as an alternative for state hook. All state changes are bundled in to central function called reducer, and state will be updated according to initiated action and existing state. Developers coming from Redux, this approach should feel familiar and state hook example is rewritten as this:

https://chathuranga94.medium.com/introduction-to-react-hooks-4694fe2d0fc0


#### How does Redux work ?

https://medium.com/javascript-in-plain-english/the-only-introduction-to-redux-and-react-redux-youll-ever-need-8ce5da9e53c6


#### What is Redux Thunk ?

https://medium.com/fullstack-academy/thunks-in-redux-the-basics-85e538a3fe60


#### What is the Difference Between useEffect and useLayoutEffect ?

It’s all in the timing. 

useEffect runs asynchronously and after a render is painted to the screen.

useLayoutEffect, on the other hand, runs synchronously after a render but before the screen is updated.

https://daveceddia.com/useeffect-vs-uselayouteffect/

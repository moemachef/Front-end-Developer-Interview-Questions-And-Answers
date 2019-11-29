# Node Questions

#### What is Express.js.

In layman terms, Express.js is a web application framework that is built on top of Node.js. It provides a minimal interface with all the tools required to build a web application. Express.js adds flexibility to an application with a huge range of modules available on npm that you can directly plug into Express as per requirement. It helps in easy management of the flow of data between server and routes in the server-side applications. It was developed by TJ Holowaychuk and was released in the market on 22nd of May, 2010. Formerly it was managed by IBM but currently, it is placed under the stewardship of the Node.js Foundation incubator.


Express is majorly responsible for handling the backend part in the MEAN stack. Mean Stack is the open-source JavaScript software stack that is heavily used for building dynamic websites and web applications in the market. Here, MEAN stands for MongoDB, Express.js, , and Node.js.

- Express quickens the development pace of a web application.
- It also helps in creating mobile and web application of single-page, multi-page, and hybrid types
- Express can work with various templating engines such as Pug, Mustache, and EJS.
- Express follows the Model-View-Controller (MVC) architecture.
- It makes the integration process with databases such as MongoDB, Redis, MySQL effortless.
- Express also defines an error-handling middleware.
- It helps in simplifying the configuration and customization steps for the application.

#### What is middleware.

Middleware functions are functions that have access to the request object (req), the response object (res), and the next middleware function in the application’s request-response cycle. The next middleware function is commonly denoted by a variable named next.

- As name suggests it comes in middle of something and that is request and response cycle.
- Middleware has access to request and response object.
- Middleware has access to next function of request-response life cycle.

Middleware functions can perform the following tasks:
- Execute any code.
- Make changes to the request and the response objects.
- End the request-response cycle.
- all the next middleware in the stack.

If the current middleware function does not end the request-response cycle, it must call next() to pass control to the next middleware function. Otherwise, the request will be left hanging.

https://medium.com/@selvaganesh93/how-node-js-middleware-works-d8e02a936113

https://medium.com/@jamischarles/what-is-middleware-a-simple-explanation-bb22d6b41d01

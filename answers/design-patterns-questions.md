# Design Patterns Questions

#### What are the differences between Tight Coupling and Loose Coupling?

- Tight and loose coupling are terms used to describe the relationship between components of an application. In tight coupling, the components of a system are highly dependent on each other. If one component fails, it will also affect the others and eventually bring down the entire system. This creates inflexibility issues since any modifications to one component may require modifications to others. This can make the system difficult to scale and maintain.  

- In a loosely coupled system, the components are independent of each other. Each component has its own well-defined interface and communicates with other components through standardized protocols. Changes to one component do not require changes to other components, making the system more flexible and easier to maintain. The only caveat here is the increased complexity of handling multiple resources especially for a large application. Loose coupling is increasingly becoming popular with the rise of modern technologies such as microservices, containers, and APIs.

https://cleancommit.io/blog/whats-the-difference-between-tight-and-loose-coupling/

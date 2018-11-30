# Performance Questions

#### What tools would you use to find a performance bug in your code?

Depends completely on the type of testing you want to perform. Whether you are looking to find bugs on the front end or back end? Or are you looking for a tool that will help you perform chaos testing? 

There are a lot of strategies involved in finding bugs on any website. There are tools offering their services to help users implement these testing strategies well.

- Performance Testing tool - To check if the application is able to cope up with excessive traffic incoming. Example - Apache JMeter
- Cross Browser Testing tool - Helps you in finding bugs of a website across a variety of thousands of browsers running on real OS and different devices. Example - LambdaTest - You can also find bugs in RWD (Responsive Web Design) with their automated screenshots.
- VAPT tools- Vulnerability Assessment & Penetration Testing tools - To help you identify the soft spots in your website’s security. Example - Wireshark, NMAP etc.
- Bug Tracking Tools - Jira, Asana, Microsoft VSTS helps you to maintain a neat and clean library of all the bugs you found so you could collaborate and organize better with your teammates. Note that LambdaTest provides integrations to these 3 and many other bug tracking platform.


#### What are some ways you may improve your website's scrolling performance?

- Diagnosing Your Paints
- Image Resizes
- Expensive Styles
- Reflows and Repaints


https://www.html5rocks.com/en/tutorials/speed/scrolling/



#### Explain the difference between layout, painting and compositing.

Layout:-

Browser will determine how much space each element takes up and where to place it.

Painting:-

This is the process of filling in pixels. It involves drawing out elements.

Compositing:-

Browser draws element to the screen in the correct order so the page renders correctly.

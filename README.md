# RevBoost Technical Assessment



## Table of Contents

- [General Questions](#general-questions)
  - [Question #1: What are some ways to make websites faster?](#question-1-what-are-some-ways-to-make-websites-faster)
  - [Question #2: When would you use a NoSQL solution instead of SQL?](#question-2-when-would-you-use-a-nosql-solution-instead-of-sql)
  - [Question #3: What type of experience have you had working with e-commerce sites?](#question-3-what-type-of-experience-have-you-had-working-with-e-commerce-sites)
- [Task Descriptions](#task-descriptions)
  - [Task 1: Quickly Clone a Page](#task-1-quickly-clone-a-page)
  - [Task 2: Simple Site/App Using an API](#task-2-simple-siteapp-using-an-api)

## General Questions

### Question #1: What are some ways to make websites faster?

To enhance website speed, consider the following techniques:

- **Minimizing HTTP Requests:** Reducing the number of elements on your page to decrease the number of HTTP requests required for rendering the page.
- **Using a CDN:** Distributing your content over a network of servers located in various global locations to reduce the loading time of your web page content.
- **Optimizing Images:** Ensuring images are no larger than necessary, using the right file format, and compressing them without losing quality.
- **WebP for Images:** Converting images to Web can significantly reduce the file size of images without compromising quality.
- **Avoiding Redirects:** Eliminate unnecessary redirects to decrease loading delays.
- **Enabling Browser Caching:** Use caching to speed up returns to your site by storing assets locally.
- **Reducing Server Response Time:** Aim for under 200ms by resolving bottlenecks like slow database queries.
- **Asynchronous CSS/JS Loading:** Load scripts asynchronously to prevent blocking the HTML parsing.
- **Deferring JavaScript:** Load JavaScript after the page has rendered to enhance user experience.

### Question #2: When would you use a NoSQL solution instead of SQL?

In the dynamic environment of digital agency projects, deciding between NoSQL and SQL databases really comes down to what each specific project needs. I find myself leaning towards NoSQL when a project needs to scale up quickly. NoSQL is great for those times when you're juggling unstructured or semi-structured data — it’s super flexible, which is a lifesaver for projects where things are still a bit up in the air or changing on the fly. This makes NoSQL a solid pick for building scalable, high-performance websites and apps that would meet the clients' projects.

Given the diverse range of client projects and requirements I might encounter in a digital agency environment. Here's how I would approach this decision in such a context:

- **Handling Large Volumes of Data:** For client projects that involve big data or real-time web applications, I'd recommend NoSQL due to its superior efficiency with large-scale data. This capability is crucial for developing scalable, high-performance websites and applications for our clients.

- **Need for High Scalability:** NoSQL databases excel in environments requiring quick scalability. Given the dynamic nature of digital projects, the ability to swiftly scale up by adding more servers can be a game-changer for growing client applications.

- **Flexible Data Models:** NoSQL databases offer the flexibility needed for evolving data models or working with unstructured data, such as JSON or XML files. This flexibility allows us to rapidly prototype and iterate based on client feedback or changing requirements.

- **Geographically Distributed Data:** For clients aiming for a global reach, NoSQL's capability to distribute data across multiple data centers can significantly improve application performance and user experience worldwide.

- **Development Speed and Agility:** The schema-less nature of NoSQL databases aligns with the fast-paced, iterative development environment of a digital agency. This agility would enable us to quickly adapt to new client requirements or technology trends, ensuring we deliver cutting-edge solutions.


### Question #3: What type of experience have you had working with e-commerce sites?

In my tenure at Rooster Grin Media, I had the privilege of working on a standout project for the PlumpJack Collection website [https://www.plumpjackcollection.com/](https://www.plumpjackcollection.com/), where I utilized JSON to showcase their wine collection. This role involved dynamically presenting complex product inventories, enhancing the user experience for an e-commerce platform.

This project not only highlighted my technical abilities in working with web technologies and data formats but also underscored my commitment to creating engaging and effective online shopping experiences. My experience spans developing responsive designs, managing product listings, and integrating seamless back-end to front-end connections, particularly using the WordPress API.

With a solid foundation in front-end development and a track record of elevating e-commerce platforms, I’m adept at delivering projects that combine technical excellence with intuitive design, making me a well-rounded candidate for web development roles focused on e-commerce solutions.

## Task Descriptions

### Task 1: Quickly Clone a Page

#### Loading the Cloned Website

To view the cloned site simply open the `index.html` located in the `task-1` folder file in your web browser. The page should load, displaying a clone of the original website.


### 1.a) Explain your method?

I approached the website cloning process with a focus on accurately replicating the site's core elements in a local environment. Here’s the method I followed:

- **Accessing the Source Code:**
    - I initiated the process by using the Developer Tools available in the web browser.
    - After navigating to the “Sources” tab within the Developer Tools, I accessed the complete HTML markup of the page.
- **Replicating the HTML:**
    - With the HTML code accessed, I selected all the content, ensuring not to miss any hidden or collapsible elements that might contain crucial layout or content information.
    - I then copied the HTML and pasted it into a text editor, in this case Visual Studio Code.
    - I saved this new file with a .html extension, ensuring it would be recognized by browsers as an HTML document.
- **Adjusting Resource Paths:**
    - Given that the resources, particularly images, were hosted externally, I carefully prepended ‘https:’ to all src attributes. This was an essential step to circumvent issues with protocol-relative URLs when the page is loaded locally.
    - This adjustment ensures that the images and other resources are fetched using HTTPS.
- **Handling the CSS:**
    - Fortunately, in this instance, the CSS was embedded within the HTML file itself, which simplified the process. There was no need to download and link a separate CSS file.
    - However, if this were not the case, I would have repeated a similar process for the CSS files as I did for the HTML, ensuring paths were correctly set to link the stylesheets.

By following this method, I minimized potential errors by directly using the browser's capabilities to access the necessary code, ensuring resource paths were correctly formatted for a local environment, and maintaining the structural and visual fidelity of the original website.

### 1.b) How you would minimize the errors?

To minimize errors when cloning a website, I adopted several strategies:

- **Protocol Specification:** By explicitly adding ‘https:’ to the resource paths, I ensured that all resources are requested securely and are compatible with the local file system which may not recognize protocol-relative URLs.
- **Consistency Checks:** I methodically reviewed the structure of the HTML to confirm that all tags were closed and properly nested. This helps in preventing layout issues.
- **Browser Testing:** I tested the cloned site in multiple browsers to identify any cross-browser compatibility issues.
- **Developer Console Monitoring:** By keeping an eye on the browser’s developer console, I could quickly spot and address any errors logged during the loading of the page.
- **Using Live Server in Visual Studio Code:** I used Visual Studio Code’s Live Server to serve the site locally, reducing path-related errors and enabling real-time updates during development.
- **Incremental Approach:** I tackled the cloning process step by step, verifying each stage before moving on to the next, which allowed me to isolate and fix issues systematically.

By combining these approaches, I was able to effectively reduce the margin for errors and ensure a more reliable replication of the website.

### 1.c) If you would need to eliminate scripts, explain why?

I would consider eliminating scripts in the cloned website primarily for performance and relevance. For instance, third-party tracking scripts, like Google Analytics, are unnecessary in a local testing environment and would needlessly attempt to send data to the live service. Additionally, removing scripts that handle live services or user-specific interactions helps avoid unintended side effects and ensures privacy. This streamlining not only speeds up local loading times but also maintains focus on the essential functionality required for development purposes.


### Task 2: Simple Site/App Using an API

Developed a simple application utilizing Nuxt 3 which allows users to search for artists using a free API.

#### Running the Project

To run this application:

1. **Navigate to the `task-2` folder:** Detailed instructions are provided in the `README.md` file located within this directory.

2. **Follow the Directions:** The `README.md` file in the `task-2` folder contains all the necessary steps to get the application up and running on your local machine. 



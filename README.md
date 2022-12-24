# NodeJS

## Goal

-   To learn what is NodeJS and how it works

## What is [NodeJS](https://nodejs.org/en/about/)?

-   It is **not a framework**.
-   It is **not a programming language**.
-   **Node is just a runtime environment** for Javascript, built using **Chrome's v8 engine**.

## What can we build with Node?

-   [API](https://www.redhat.com/en/topics/api/what-are-application-programming-interfaces)
-   [Backend](https://airfocus.com/glossary/what-is-a-back-end/)
-   [Frontend](https://airfocus.com/glossary/what-is-a-front-end/)
-   [Microservices](https://aws.amazon.com/microservices/)
-   [Mobile apps](https://www.g2.com/glossary/mobile-apps)
-   [Desktop apps](https://v2cloud.com/glossary/what-is-a-desktop-app#:~:text=A%20desktop%20application%20is%20a,are%20developed%20purely%20for%20entertainment.)
-   [Machine Learning](https://www.ibm.com/topics/machine-learning)
-   [Artificial Intelligence](https://www.ibm.com/topics/artificial-intelligence)

## Why we should use Node?

-   Fast code design.
-   Fast code implementation.
-   Fast code execution.

    **Note**: Even Javascript being known by it's pour performance, it only happens in the browser. If writen in the server side using NodeJS as runtime, Javascript can be really fast.

-   Scalability
-   Giant ecosystem
-   Cutting-edge applications
-   Fullstack applications with just one language

## Which cases we **shouldn't** use Node?

-   To process a **really large amount of data**. Node does not handle well with algorithms that **require high CPU usage**. If you need it, you should use a **lower level language** like C.

## Google's [v8 Engine](https://v8.dev/)

-   It is an **interpreter for JavaScript**.
-   Built in [C++](https://www.w3schools.com/cpp/cpp_intro.asp).
-   Always updated with **lastest JavaScript features**.
-   It was made to use in Chrome, but with great care **not to break Node**.
-   Does not have common APIs and properties like [DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction) or [console](https://developer.mozilla.org/en-US/docs/Web/API/console).
    -   But all features that are not related to the browser are inside NodeJS as built-in modules, like [console](https://nodejs.org/api/console.html), or even new ones that we can't acess in browser, like the [File System Manager](https://nodejs.org/api/fs.html).

## The lib that powers Node: [Libuv](https://libuv.org/)

-   It handles the **asynchronous I/O** (Input/Output).
-   It handles the **Event Loop**.
-   It handles the **Worker Threads**.
-   It is responsible for **preventing thread blocks**.

Details about each one of these in the next section.

## Characteristics

-   Single thread
    -   A **thread** is like a **worker doing his job**. In many languages, there are multiple workers, they are known as **multi-thread languages**, but **Node have only one thread**. Is that better? Not exactly, more workers means more tasks being done. Therefore, is Node slower than the other languages? Not at all. Node was from the beginning built thinking about using only one thread, so it's design works perfectly to increase this thread performance so **Node can compete and even win performance tests against multithreaded languages**.
-   Asynchronous by default
    -   Nothing can block the Node process, unlike the synchronous languages, if Node is waiting for something as a database response, it will not wait still. Node will directly to the next task, and if there is more waiting, it will go to the next, he never stops working. When the expected response comes, he will go back at it and continue it's job. This behavior, called **asynchronous**, is what makes Node have a really great performance, even being **single threaded**.
-   Non-blocking
    -   As told above, the asynchronous behavior of NodeJS is what makes possible to keep **working restlessly**, in synchronous languages, the **thread** will be block while waiting for a third-party response, but in NodeJS, **it will pick another task in the queue** and start it earlier, so it **never stops**, it is **never blocked**.
-   Event Driven
    -   One of the things that helps Node performance is the **Event Driven Architecture**.
    -   It is, simplifying, a **design based in Events** being executed asynchronously and **callbacks** to execute when these events are done.
    -   This cycle of events and callbacks can be **chained almost endlessly**.
-   Event Queue
    -   Just a queue where the Inputs/Request are stored. The Event Loop will execute one by one of them in the same order they came in.
-   Worker Thread
    -   When an event in queue can block the thread, event loop transfer it to a worker thread. It can be a call to database, a interaction with file system or any process that **does not rely on Node**.
    -   While these events are not ready, Node will execute the next event in queue, and when it is ready, an **event will be emitted** so the event loop will know.
-   Execution Callback
    -   When the worker thread notifies Node it is ready, **Node will put it back into the event queue**, to continue the execution.
-   Event Loop

    -   The great protagonist of **Node's performance**.
    -   A series of steps that Node runs and reruns unstoppably in a specific order, just like a (surprisingly) **loop of events**.
    -   Let's break it down:

    1. A **input/request** is received.
    2. Event loop adds it to the **Event Queue**.
    3. If it does not depend on third-party responses, only on Node, it will execute the code and return the **output/response**
    4. If there is any asynchronous call, the Event Loop will remove it from the Event Queue and send it to the **Worker Thread** (as explained above).
    5. Once the worker thread is complete, Event Loop put it back into the Event Queue, and the **same steps are repeated until the output is ready**.

    **Note**: Even if the asynchronous response to a third-party is returned instantly, that event will be put into the worker thread and then it will be put at the end if event queue, that's why the synchronous Javascript code will be executed first (unless, of course, the synchronous request came after the asynchronous event was completed and returned to event queue).

## More on Node

-   Read-Eval-Print-Loop

    -   Popular known as [REPL](https://nodejs.org/api/repl.html)
    -   It helps us write JavaScript directly into the Terminal.
    -   Just type `node` in any Terminal (of course you need to install Node in your machine before using it).

-   Node Package Manager

    -   Popular known as [NPM](https://www.npmjs.com/).
    -   NPM was built alongside with Node to be used as a giant library sharing.
        -   A Library is a ready-to-use code created and made available publicly or privately by people or companies to help us develop applications reusing their code so we don't have to reinvent the wheel.
    -   Writing a simple command like `npm install express`, npm install the package called **express** into our Node Application. And for removing it, you just type `npm uninstall express`.
        -   **Express** is a common package used to create APIs. It is not necessary, we can use build it from scratch, but we don't have to, that's the beauty of npm.

    **Note**: Tthere are other package managers that are used a lot nowadays as [Yarn](https://yarnpkg.com/) or [PNPM](https://pnpm.io/). You can choose which you prefer, the libraries they can install came from the same source, there are no packages that are exclusive to one manager.

-   Open source
    -   Node is completely open source, anyone can contribute, write new features, solve bugs and make improvements.
    -   Check the official [NodeJS repo](https://github.com/nodejs/node)

---
title: NPM, Node.js and JavaScript
author: Jun Hu
tags:
  - JavaScript
  - NPM
  - Node.js
  - backend
date: 2020-05-11 22:54:12
---

JavaScript, often abbreviated as JS, is a programming language that conforms to the ECMAScript specification. Alongside HTML and CSS, JavaScript is one of the core technologies of the World Wide Web. HTML is responsible for the structures, CSS is responsible for the decorations, and JavaScript is responsible for the interactions.

<!-- more -->

JavaScript should not to be confused with [Java](https://maologue.com/what-s-the-commonality-between-java-and-javascript/)!

Although JavaScript is popular in frontend developments, it can be used in backends as well. In 2009, Ryan Dahl took the opensource Google's V8 JavaScript engine and embedded it into a C++ program - the Node.js.
Node.js is a JavaScript runtime environment that executes JavaScript codes outside of the web browsers.
{% cq %}While the use of Node.js is not limited to the frontend or backend ... ... Node is a popular choice for building backends largely due to the fact that it shares the same base language, JavaScript, as many front-ends. This allows developers and teams to contribute, share and reuse code across the stack and manage full-stack projects with a single package manager (such as NPM). —[@danmjung](https://link.medium.com/yz7PVckWd6) {% endcq %}

Finally, NPM (originally short for Node Package Manager) is a package manager for the JavaScript programming language. It is the default package manager for the JavaScript runtime environment Node.js. It consists of a command line client, also called npm, and an online database of public and paid-for private packages, called the npm registry. Below shows how to install Hexo via NPM command line client from the registry.
```js
$ npm install hexo-cli -g
```

---

Reference:

*- [NPM](https://www.npmjs.com/)*
*- [Node.js](https://nodejs.org/en/)*
*- [Wikipedia:JavaScript](https://en.wikipedia.org/wiki/JavaScript)*


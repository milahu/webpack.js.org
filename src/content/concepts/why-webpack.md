---
title: Why webpack
sort: 7
contributors:
- debs-obrien
---

## Why webpack?

To understand why you should use webpack lets do a recap of how we use JavaScript on the web before bundlers were a thing.

There are two ways to run JavaScript in a browser. First, include a script for each functionality you want to implement, the issue is that the solution is hard to scale as loading too many scripts causes a network bottleneck. The other alternative is load a big .js file containing all your project code, but this results in an unmaintainable scripts that causes problems in scope, size, readability, fragility and monolith files.


## IIFE's - Immediately invoked function expressions

IIFEs solve scoping issues for large projects. When script files are wrapped by an IIFE, you can safely concatenate When script files are wrapped by an IIFE, you can safely concatenate or safely combine files without concern of scope collision. Wow, we can now write 100 files and squish them together without concerns that we are going to knock out a bunch of variables and scopes.

This lead to tools like Make, Gulp, Grunt, Broccoli, Brunch and StealJS being created. The purpose of these tools/task runners is to concatenate the files together in order to solve these problems. However there is much more to it. With these tools a full rebuild is needed every time. Anytime you want to change one file you have to rebuild the whole thing. This also leads to a lot of dead code. Concatenate doesn't help the usages across files. If you are concatenating files together how do you remove code your not using? How do you even know what code you are not using?

If you are only using one function from lodash or one date utility from moment.js you are actually adding the entire library and just squishing it together. Lot's of IIFE's are slow. Also how do you lazy load with a task runner? You don't. There is no way. Whatever you are building you are shipping all the code down the pipeline even if your app maybe only uses 10% of it to load and get your initial experience. As you can see there are a lot of problems with just concatenating scripts together.


## Birth of JavaScript Modules happened thanks to Node.js

If you are using webpack you are using Node.js as webpack relies on Node.js. Node.js is JavaScript that runs on the server. So how do you load JavaScript if there is no DOM? How do you add a script tag if there is no html in Node.js?

CommonJS came about and introduced `require` which allows you to inject other pieces of a module into the current module. This solves scope issues without having to use IIFE's and helps us to see exactly which modules are used.


## npm + Node.js + modules -- mass distribution

JavaScript is taking over the world as a language, as a platform and as a way to rapidly develop and create fast running applications. 

But there is no browser support for CommonJS. There are no [live bindings](https://medium.com/webpack/the-state-of-javascript-modules-4636d1774358). There are problems with circular references. Sync module resolution loader is slow. Bundlers/Linkers such as Browserify, RequireJS, SystemJS came about to solve these issues and allow you to write CommonJS modules which get bundled, making it possible to run them in the Web.

But with CommonJS there is no lazy loading. All bundles are loaded upfront. CommonJS doesn't allow for lazy loading, it has non standard syntax and has no real module system.


## ESM - ECMAScript Modules

ESM provides reusability, encapsulation, is organized and convenient but there is no ESM for Node.js. How do they work in the browser? Incredibly slow, therefore not an option.

Every library is different, library authors choose a module type they like and this is just for JavaScript. Each and any other filetype until now has had to have specific ways to process it. 


## Wouldn't it be nice….

To have something that will not only let us write modules but also support any module format (at least until we get to ESM) and that can handle resources and assets at the same time.

This is why webpack was born. webpack is a module bundler. It lets you write any module format or a mixed format and compiles them for the browser. It supports static async bundling (code splitting) where you can create separate lazy loaded bundles at build time and extra optimization with its rich, vast ecosystem. Today it is the most performant way to ship JavaScript and has 14 million downloads a month.


### Why webpack? That's why!!!!
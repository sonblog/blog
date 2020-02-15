---
author: client
comments: false
date: 2017-09-03 07:24:05+00:00
layout: post
link: https://quachson.com/nodejs-for-beginners/
slug: nodejs-for-beginners
title: NodeJS for beginners
wordpress_id: 1369
categories:
- Javascript
- node.js
tags:
- js
- node.js
---

Some keywords that you must find out if you want to learn nodejs: promise, asynchronous, callback, callback hell, eslint, ES6, functional programming, parameter as function.
**IDE**: **Visual Studio Code** (free), IntelliJ (license), Eclipse, Atom, sublime text, ....
These libraries that I used to use: npm, yarn, eslint, async, fs, lodash, expressJS, node-fetch, nconf, mongoosejs, graphql, react, redux , jsdoc, rimraf, husky
xml parser : sax, saxpath, xml2js.



 	
  * npm: https://egghead.io/courses/how-to-use-npm-scripts-as-your-build-tool

 	
  * eslint: https://github.com/airbnb/javascript

 	
  * Check eslint: ./node_modules/.bin/eslint --cache --fix ./src

 	
  * Create eslint report: node_modules/.bin/eslint app.js -o eslint_report.html -f html --color

 	
  * Log: just use console.log with format json. Log file: npm start >> log.files


If you're similar ES6, you will learn Stream in Java 8 quickly.
Example: Find max multiples of 3 in array
nodejs

[code lang="javascript"]
import { filter, max } from 'lodash';

const array = [99, 5, 4, 10, 8, 6, 33, 12, 45, 63];
console.log(max(filter(array, item => item % 3 == 0)));
[/code]

java

[code lang="java"]
int[] array = {99, 5, 4, 10, 8, 6, 33, 12, 45, 63};
Arrays.stream(array).filter(item -> item % 3 == 0).reduce(Integer::max).ifPresent(System.out::println);
[/code]

# [🏠 Home Page](../../readme.md)
- [🏠 Home Page](#-home-page)
  - [1.1 The Story of Node.js](#11-the-story-of-nodejs)
    - [1.1.1 Origins](#111-origins)
    - [1.1.2 Birth of Node.js](#112-birth-of-nodejs)
    - [1.1.3 Breakthrough of Node.js](#113-breakthrough-of-nodejs)
    - [1.1.4 Node.js Conquers Windows](#114-nodejs-conquers-windows)
    - [1.1.5 io.js: The Fork of Node.js](#115-iojs-the-fork-of-nodejs)
    - [1.1.6 Node.js Reunited](#116-nodejs-reunited)
    - [1.1.7 Deno: A New Star in the JavaScript Sky](#117-deno-a-new-star-in-the-javascript-sky)
    - [1.1.8 OpenJS Foundation](#118-openjs-foundation)
  - [1.2 Organization of Node.js](#12-organization-of-nodejs)
    - [1.2.1 Technical Steering Committee](#121-technical-steering-committee)
    - [1.2.2 Collaborators](#122-collaborators)
    - [1.2.3 Community Committee](#123-community-committee)
    - [1.2.4 Work Groups](#124-work-groups)
    - [1.2.5 OpenJS Foundation](#125-openjs-foundation)
  - [1.3 Versioning of Node.js](#13-versioning-of-nodejs)
    - [1.3.1 Long-Term Support Releases](#131-long-term-support-releases)
  - [1.4 Benefits of Node.js](#14-benefits-of-nodejs)
  - [1.5 Areas of Use for Node.js](#15-areas-of-use-for-nodejs)
  - [1.6 The Core: V8 Engine](#16-the-core-v8-engine)
    - [1.6.1 Memory Model](#161-memory-model)
    - [1.6.2 Accessing Properties](#162-accessing-properties)
    - [1.6.3 Machine Code Generation](#163-machine-code-generation)
    - [1.6.4 Garbage Collection](#164-garbage-collection)
  - [1.7 Libraries around the Engine](#17-libraries-around-the-engine)
    - [1.7.1 Event Loop](#171-event-loop)
    - [1.7.2 Input and Output](#172-input-and-output)
    - [1.7.3 libuv](#173-libuv)
    - [1.7.4 Domain Name System](#174-domain-name-system)
    - [1.7.5 Crypto](#175-crypto)
    - [1.7.6 Zlib](#176-zlib)
    - [1.7.6 Zlib](#176-zlib-1)
    - [1.7.7 HTTP Parser](#177-http-parser)
  - [1.8 Summary](#18-summary)

## 1.1 The Story of Node.js
To help you better understand what Node.js is and how some of the
development decisions came about, let's explore the history of the
platform.
### 1.1.1 Origins
Node.js was originally developed by Ryan Dahl, a PhD student in
mathematics who thought better of it, abandoned his efforts, and
instead preferred to travel to South America with a one-way ticket
and very little money in his pocket. There, he kept his head above
water by teaching English. During this time, he got in touch with PHP
as well as Ruby and discovered his affection for web development.
The problem with working with the Ruby framework, called Rails,
was that it couldn’t deal with concurrent requests without any
workaround. The applications were too slow and utilized the CPU
entirely. Dahl found a solution to his problems with Mongrel, a web
server for applications based on Ruby.

Unlike traditional web servers, Mongrel responds to user requests
and generates responses dynamically, where otherwise only static
HTML pages are delivered.

The task that actually led to the creation of Node.js is quite trivial
from today’s point of view. In 2005, Dahl was looking for an elegant

way to implement a progress bar for file uploads. However, the
technologies available at the time only allowed unsatisfactory
solutions. Regarding file transfers, HTTP was used for relatively
small files, and File Transfer Protocol (FTP) was used for larger files.
The status of the upload was queried using long polling, which is a
technique where the client sends long-lived requests to the server,
and the server uses the open channel for replies. Dahl’s first attempt
to implement a progress bar took place in Mongrel. After sending the
file to the server, it checked the status of the upload using a large
number of Asynchronous JavaScript and XML (AJAX) requests and
displayed it graphically in a progress bar. However, the downside of
this implementation was Ruby’s single-threaded approach and the
large number of requests that were required.

Another promising approach involved an implementation in C. Here,
Dahl’s options weren’t limited to one thread. However, C as a
programming language for the web has a decisive disadvantage:
only a small number of developers are enthusiastic about this field of
application. Dahl was also confronted with this problem and
discarded this approach after a short time.

The search for a suitable programming language to solve his
problem continued and led him to functional programming languages
such as Haskell. Haskell’s approach is built on nonblocking
input/output (I/O), which means that all read and write operations are
asynchronous and don’t block the execution of a program. This
allows the language to remain single-threaded at its core and doesn’t
introduce the problems that arise from parallel programming. Among
other things, no resources have to be synchronized, and no
problems are caused by the runtime of parallel threads. However,
Dahl still wasn’t fully satisfied with this solution and was looking for
other options.
### 1.1.2 Birth of Node.js
Dahl then found the solution he was finally satisfied with—
JavaScript. He realized that this scripting language could meet all his
requirements. JavaScript had already been established on the web
for years, so there were powerful engines and a large number of
developers. In January 2009, he began working on his
implementation for server-side JavaScript, which can be regarded as
the birth of Node.js. Another reason for implementing the solution in
JavaScript, according to Dahl, was the fact that the developers of
JavaScript didn’t envision this area of use. At that time, no native
web server existed in JavaScript, it couldn’t handle files in a file
system, and there was no implementation of sockets to
communicate with other applications or systems. All these points
spoke in favor of JavaScript as the basis for a platform for interactive
web applications because no determinations had yet been made in
this area, and, consequently, no mistakes had yet been made either.
The architecture of JavaScript also argued for such an
implementation. The approach of top-level functions (i.e., functions
that aren’t linked to any object, are freely available, and can be
assigned to variables) offers a high degree of flexibility in
development and enables functional approaches to solutions.

Thus, Dahl selected other libraries in addition to the JavaScript
engine, which is responsible for interpreting the JavaScript source
code, and put them together in one platform.

In September 2009, Isaac Schlueter started working on a package
manager for Node.js, the Node Package Manager (npm).

### 1.1.3 Breakthrough of Node.js
### 1.1.4 Node.js Conquers Windows
### 1.1.5 io.js: The Fork of Node.js
### 1.1.6 Node.js Reunited
### 1.1.7 Deno: A New Star in the JavaScript Sky
### 1.1.8 OpenJS Foundation

##  1.2 Organization of Node.js
### 1.2.1 Technical Steering Committee

### 1.2.2 Collaborators
### 1.2.3 Community Committee
### 1.2.4 Work Groups
### 1.2.5 OpenJS Foundation
## 1.3 Versioning of Node.js
### 1.3.1 Long-Term Support Releases
## 1.4 Benefits of Node.js
## 1.5 Areas of Use for Node.js
## 1.6 The Core: V8 Engine
### 1.6.1 Memory Model
### 1.6.2 Accessing Properties
### 1.6.3 Machine Code Generation
### 1.6.4 Garbage Collection
## 1.7 Libraries around the Engine
### 1.7.1 Event Loop
### 1.7.2 Input and Output
### 1.7.3 libuv
### 1.7.4 Domain Name System
### 1.7.5 Crypto
### 1.7.6 Zlib
### 1.7.6 Zlib
### 1.7.7 HTTP Parser
## 1.8 Summary
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

After Dahl integrated all the components and created the first
executable examples on the new Node.js platform, he needed a way
to introduce Node.js to the public. This also became necessary
because his financial resources shrank considerably due to the
development of Node.js, and he would have had to stop working on
Node.js if he didn’t find any sponsors. He chose the JavaScript
conference JSConf EU in November 2009 in Berlin as his
presentation platform. Dahl put all his eggs in one basket. If the
presentation was a success and he found sponsors to support his
work on Node.js, he could continue his involvement; if not, almost a
year’s work would have been in vain. In a rousing talk, he introduced
Node.js to the audience and showed how to create a fully functional
web server with just a few lines of JavaScript code. As another
example, he introduced an implementation of an Internet Relay Chat
(IRC) chat server. The source code for this demonstration comprised
about 400 lines. Using this example, he demonstrated the
architecture and thus the strengths of Node.js while making it
tangible for the audience. The recording of this presentation can be
found at www.youtube.com/watch?v=EeYvFl7li9E. The presentation
didn’t miss its mark and led to Joyent stepping in as a sponsor for
Node.js. Joyent is a San Francisco-based software and services
provider offering hosting solutions and cloud infrastructure. With its
commitment, Joyent included the open-source software Node.js in its
product portfolio and made Node.js available to its customers as part
of its hosting offerings. Dahl was hired by Joyent and became a fulltime
maintainer for Node.js from that point on.


### 1.1.4 Node.js Conquers Windows
The developers made a significant step toward the spread of Node.js
by introducing native support for Windows in version 0.6 in
November 2011. Up to that point, Node.js could only be installed
awkwardly on Windows via Cygwin.

Since version 0.6.3 in November 2011, npm has been an integral
part of the Node.js packages and is thus automatically delivered
when Node.js is installed.

Surprisingly, at the start of 2012, Dahl announced that he would
finally retire from active development after three years of working on
Node.js. He handed over the reins of development to Schlueter. The
latter, like Dahl, was an employee at Joyent and actively involved in
the development of the Node.js core. The change unsettled the
community, as it wasn’t clear whether the platform would continue to
develop without Dahl. A signal that the Node.js community
considered as being strong enough for solid further development
came with the release of version 0.8 in June 2012, which was
primarily intended to significantly improve the performance and
stability of Node.js.

With version 0.10 in March 2013, one of the central interfaces of
Node.js changed: the Stream application programming interface
(API). With this change, it became possible to actively pull data from
a stream. Because the previous API was already widely used, both
interfaces continued to be supported.

### 1.1.5 io.js: The Fork of Node.js

In January 2014, there was another change in the project
management of Node.js. Schlueter, who left Node.js maintenance in
favor of his own company (called npmjs), the host of the npm
repository, was succeeded by TJ Fontaine. Under his direction,
version 0.12 was released in February 2014. A common criticism of
Node.js at the time was that the framework had still not reached the
supposedly stable version 1.0, which prevented numerous
companies from using Node.js for critical applications.

Many developers were unhappy with Joyent, which had provided
maintainers for Node.js since Dahl, and so the community fractured
in December 2014. The result was io.js, a fork of Node.js that was
developed separately from the original platform. As a result, the
independent Node.js Foundation was founded in February 2015,
which was responsible for the further development of io.js. At the
same time, version 0.12 of the Node.js project was released.


### 1.1.6 Node.js Reunited

In June 2015, the two projects io.js and Node.js were merged into
the Node.js Foundation. With version 4 of the project, the merger
was completed. Further development of the Node.js platform is now
coordinated by a committee within the Node.js Foundation rather
than by individuals. As a result, we see more frequent releases and
a stable version with long-term support (LTS).

### 1.1.7 Deno: A New Star in the JavaScript Sky
Since the merger of io.js and Node.js, things have become quieter
around Node.js. The regular releases, the stability, and also the
integration of new features, such as worker threads, HTTP/2 or
performance hooks, keep up the good mood within the community.
And just when things were starting to get almost too quiet around
Node.js, an old acquaintance, Dahl, took the stage again in 2018 to
introduce a new JavaScript platform called Deno during his talk, “10
Things I Regret about Node.js.”

The idea behind Deno is to create a better Node.js, untethered from
the backwards compatibility constraints that prevent revolutionary
leaps in development. For example, Deno is based on TypeScript by
default and adds a fundamentally different module system. Deno’s
core is also quite different from Node.js, as it’s written almost entirely
in Rust.

Nevertheless, there are also some common features. For example,
Deno is based on the tried and tested V8 engine, which also forms
the heart of Node.js. And you don’t have to do without the huge
number of npm packages either. For this purpose, Deno provides a
compatibility layer. You can read more about Deno in Chapter 28.

### 1.1.8 OpenJS Foundation
In 2015, the Node.js Foundation was established to coordinate the
development of the platform. The foundation was a subordinate
project of the Linux Foundation. In 2019, the JS Foundation and the
Node.js Foundation then merged to form the OpenJS Foundation. In
addition to Node.js, it includes a number of other popular projects
such as webpack, ESLint, and Electron.


##  1.2 Organization of Node.js

The community behind Node.js has learned its lessons from the
past. For this reason, there are no longer individuals at the helm of
Node.js, but a committee of several people who steer the
development of the platform.


### 1.2.1 Technical Steering Committee

The technical steering committee (TSC) is responsible for further
developing the platform. The number of members of the TSC isn’t
limited, but 6 to 12 members are targeted, usually selected from the
contributors to the platform. The tasks of the TSC are as follows:

- Setting the technical direction of Node.js
- Performing project and process control
- Defining the contribution policy
- Managing the GitHub repository
- Establishing the conduct guidelines
- Managing the list of collaborators

The TSC holds weekly meetings via Google Hangouts to coordinate
and discuss current issues. Many of these meetings are published
via the Node.js YouTube channel
(www.youtube.com/c/nodejs+foundation).


### 1.2.2 Collaborators
Node.js is an open-source project developed in a GitHub repository.
As with all larger projects of this type, a group of people, called
collaborators, have write access to this repository. In addition to
accessing the repository, a collaborator can access the continuous
integration jobs. Typical tasks of a collaborator include supporting
users and new collaborators, improving Node.js source code and
documentation, reviewing pull requests and issues (with appropriate
commenting), participating in working groups, and merging pull
requests.

Collaborators are designated by the TSC. Usually the role of a
collaborator is preceded by a significant contribution to the project
via a pull request.


### 1.2.3 Community Committee

As the name implies, the Community Committee (CommComm)
takes care of the Node.js community with a special focus on
education and culture. The CommComm coordinates in regular
meetings, which are recorded in a separate GitHub repository
(https://github.com/nodejs/community-committee). The CommComm
exists to give the community a voice and thus counterbalance the
commercial interests of corporations.

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
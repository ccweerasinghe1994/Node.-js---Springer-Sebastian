# Accessing Properties

As you probably know, JavaScript doesn’t know classes; the object
model of JavaScript is based on prototypes. In class-based
languages such as Java or PHP, classes represent the blueprint of
objects. These classes can’t be changed at runtime. Prototypes in
JavaScript, on the other hand, are dynamic, which means that
properties and methods can be added and removed at runtime. As
with all other languages that implement the object-oriented
programming paradigm, objects are represented by their properties

and methods, where properties represent the state of an object, and
methods are used to interact with the object. In an application, you
usually access the properties of the various objects very frequently.
In addition, methods in JavaScript are also properties of objects that
are stored with a function. In JavaScript, you work almost exclusively
with properties and methods, so access to them must be very fast.

---
**Prototypes in JavaScript**

`
JavaScript differs from languages such as C, Java, or PHP in that
it doesn’t take a class-based approach but instead is based on
prototypes, such as the Self language. In JavaScript, every object
normally has a prototype property and thus a prototype. In
JavaScript, as in other languages, you can create objects. For this
purpose, however, you don’t use classes in conjunction with the
new operator. Instead, you can create new objects in several
different ways. Among other things, you can use constructor
functions or the Object.create method. These methods have in
common that you create an object and assign the prototype. The
prototype is an object from which another object inherits its
properties. Another feature of prototypes is that they can be
modified at application runtime, allowing you to add new properties
and methods. By using prototypes, you can build an inheritance
hierarchy in JavaScript.
`

Normally, accessing properties in a JavaScript engine is done
through a directory in the memory. So, if you access a property, this
directory is searched for the memory section of the respective
property, and then the value can be accessed. Now imagine a large
application that maps its business logic in JavaScript on the client
side, and in which a large number of objects are held in parallel in
the memory, constantly communicating with each other. This method

of accessing properties would quickly turn into a problem. The
developers of the V8 engine have recognized this vulnerability and
developed a solution for it—the hidden classes. The real problem
with JavaScript is that the structure of objects is only known at
runtime and not already during the compilation process because
such a process doesn’t exist with JavaScript. This is further
complicated by the fact that there isn’t just one prototype in the
structure of objects, but they can rather exist in a chain. In classical
languages, the object structure doesn’t change at application
runtime; the properties of objects are always located in the same
place, which significantly speeds up accessing them.

A `hidden class` is nothing more than a description in which the
individual properties of an object can be found in the memory. For
this purpose, a hidden class is assigned to each object. This
contains the offset to the memory section within the object where the
respective property is stored. As soon as you access a property of
an object, a hidden class is created for that property and reused for
each subsequent access. So for an object, there is potentially a
separate hidden class for each property.

In Listing 1.1, you can see an example that illustrates how hidden
classes work.

```js
class Person {
    constructor(firstname, lastname) {
        this.firstname = firstname; this.lastname = lastname;
    }
}

const johnDoe = new Person("John", "Doe");
```
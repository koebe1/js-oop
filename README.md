<h1 font-family="san-serif"  align="center">JS-OOP</h1>

  <p align="center">
Summary of OOP in JavaScript with focus on ES5/ES6 by Traversy Media
    <br />
    <br />
    <br />
    
  
  ## What is an Object in JS?

  Everything besides  primitive datatypes are objects on JS.
  
    Primitive datatypes: number, string, boolean, null, undefined, symbol, bigInt.

## Strings
But why can you then call methods on a string (e.g. "string".toUpperCase())?
  
    --> JS wraps the string with an Object behind the scenes!
  
  You can also create a string as an object: 
  
    --> const string = new String("string") where console.log(typeof string) 
    would log object to the console.


 
  
## Defining Objects
  
  Object literal: 
  
    const book = { 
      title: "Sapiens", 
      getTitle: function() { 
        return `${this.title}`
      } 
    }
  
  
  Constructor Function: 
  
     function Book(title) { 
        this.title = title; 
     } 
      
     const book = new Book("Sapiens")
  
  --> useful to create multiple instances of an object.
  
  
  Object.create():
  
  1. Object of prototype:
  
    const bookPrototype = {
      getTitle: function () { return this.title }
    }
  
  2. Create book object
  
    const book = Object.create(bookPrototype);
    book.title = "Sapiens";
    book.author = "Harari";
  
  or 
  
    const book = Object.create(bookPrototype, {
      title: { value: "Sapiens" },
      author: { value: "Harari" }
     });
  
  
  Defining Methods: 
  
  Since ES5 instead of defining a method like this:
  
    const book = {
      title: "Sapiens",
      getTitle: function () {
        return this.title;
      }
    }
  
  you can use shorthand syntax like this: 
  
    const book = {
      title: "Sapiens",
      getTitle() {
        return this.title;
      }
    }
  
  
  

  ## Prototypes
  
  Prototypes are the mechanism by which JavaScript objects inherit features from one another.
  Every object holds a reference to its prototype in the property __protp__.
  
  If you append a property or a method to the prototype of an object, the object inherits this property or method.
  Rather than being appended to the object itself the property or method lives with the prototype and can be accessed
  via the reference to the prototype.
  
    book.prototype.getBook = function () { return this.title };
    book.getBook() --> returns Sapiens
  
  --> Even though getBook() isn't existing in the book object itself book has access to the method via its prototype. 
  ---> This way book is more "lightweight" compared to having the method itself.
 
  ## Inheritance
  Example of prototypal inheritance:
  
  Constructor:
  
    function Book(title, author, year) {
      this.title = title;
      this.author = author;
      this.year = year;
    }
    
Add method to prototype:
  
    Book.prototype.getTitle = function () { return this.title }
    
 Constructor for magazine:
  
    function Magazine(title, author, year, month) {
      // Calls the Book constructor with "this" bound to the instance of magazine
      Book.call(this, title, author, year);
      this.month = month; 
    }
  
  
  Inherit prototype from Book to Magazine:
  
    Magazine.prototype = Object.create(Book.protoype);
    
Instatiate a magazine object:
  
    const mag = new Magazine("Sapiens Mag", "Harari, "2021", "Nov");
  
 getTitle() is now available for mag:
  
    console.log(mag.getTitle()); --> returns "Sapiens Mag"  
  
Use Magazine constructor in magazine prototype (default is book after inhereting its prototype):
  
    Magazine.prototype.constructor = Magazine;
    

  
  ## ES6 Classes 
  Classes are syntactic sugar for prototypal inheritance.
  
 Define a class as a "blueprint" of objects: 
  
    class Book {
      constructor(title, author, year) {
        this.title = title;
        this.author = author;
      }
      getTitle() {
        return this.title;
      }
    }
  
  
  --> getTitle() lives on the prototype of book not book itself.
  
  Instantiate object: 
  
    const book = new Book("Sapiens", "Harari);
  
  
  Static Methods: 
  
  -> Static methods are methods that live on the class and can only be called form the class itself.
  --> There is no need for a instance of the class to call the static method.
  
    class Book () {
      static sayHi() {
        return "Hello"
      }
    }
      
    Book.sayHi() -> returns "Hello"
  
  
  
  ## Subclasses 
  
  The extends keyword is use in class declarations or class expressions to create a class that is a child of 
  another class (or subclass).
  
  
    class Magazine extends Book {
      constructor(title, author, year, month) {
        super(title, author, year);
        this.month = month
      }
    }
  
  -> the super keyword calls the constructor of the parent class (in our case book)
  
    const mag = new Magazine("Sapiens Mag", "Harari", "2021", "Nov"); 
  
    mag.getTitle() -> return "Sapiens Mag"
  
  ---> Under the hood JS does prototypal inheritance to make the "class extends" syntax work!
  
  
  ## Some Useful Object Methods 
  
  1. Get the keys of an object:

    Object.keys(book)
  
  2. Get the values of an object: 
  
    Oject.values(book)
  
  
    ...to be continued!

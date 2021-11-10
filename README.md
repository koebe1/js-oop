<h1 font-family="san-serif"  align="center">JS-OOP</h1>

  <p align="center">
Summary of OOP in JavaScript with focus on ES5/ES6
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
  
  
  Constructor Function (ES5): 
  
     function Book(title) { 
        this.title = title; 
     } 
      
     const book = new Book("Sapiens")
  
  --> useful to create multiple instances of an object.
  
  ## Prototypes
  
  Prototypes are the mechanism by which JavaScript objects inherit features from one another.
  Every object holds a reference to its prototype in the property __protp__.
  
  ...to be continued!
  
  ## Some Useful Object Methods 
  
  1. Get the keys of an object:

    Object.keys(book)
  
  2. Get the values of an object: 
  
    Oject.values(book)

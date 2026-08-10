Javascript Data Types
     A data type tell JavaScript what kind of value a variable contains.

JavaScript has two main categories:
1. Primitive data types
2. Non-primitive data types.

-------------------------------------------------------------------------

1. Primitive data types

1> String
     A string represents text.

     const name = "Rohit";
     const city = "Nagpur";

     You can also use template literals;

     const age = 25;

     console.log(`I am ${age} years old.`);

Output:
I am 25 years old.

2> Number
     Used for integers and decimal numbers.

     const age = 25;
     const price = 99.99;

     JavaScript uses number for both.

     console.log(typeof age);

Output:
number

3> Boolean
     A Boolean has only two values:

     true
     false

     Example:

     const isLoggedIn = true;
     const isAdmin = false;

     Booleans are commonly used in React for conditonal rendering.

     if (isLoggedIn) {
        console.log("Welcome!");
     }

4> Undefined
     A variable is undefined when it has been declared but not been assigned a value.

     let username;

     console.log(username);

Output:
     undefined

5> Null
     null means intentionally empty.

     const selectedUSer = null;

     it means: 
            Thers is currently no user selected.

6> BigInt
     Used for very large integers.

     const bigNumber = 123456789012345678901234567890n;

     The n at the end makes it a BigInt.
     you won't normally nee this in beginner React applications.

7> Symbol
     Symbols create unique values.
     
     const id = Symbol("id");
      They are mainly used for advanced JavaScript scenarios.

2. Non-Primitive Data Types

8> Object
     Objects store data using key-value pairs.

     const user - {
        name: "Rohit",
        age: 25,
        city: "Nagpur"
     };

     Access values:

     console.log(user.name);
     console.log(user.age);
    
Output:
     Rohit
     25

     Objetcs are extremely important in React.

     For example:

     const user = {
        name: "Rohit",
        email: "Rohit@gmail.com"
     }
     
     This type of data is commonly passed to React components as props.

9> Array
     Arrays store multiple values.

     const skills = {
        "HTML",
        "CSS",
        "JavaScript",
        "React"
     };

     Access an item using its index;

     console.log(skills[0]);

Output:
     HTML

     Arrays are heavily used in React when rendering lists.
ex:
     const users = ["Rohit", "Amit", "Rahul"];

     Later in React:

     {uesrs.map(user => (
        <p>{user}</p>
     ))
     }

# Checking Data Types

     use:
      typeof
    
EX:  
     console.log(typeof "Rohit");
     console.log(typeof 25);
     console.log(typeof true);
     console.log(typeof undefined);

Output:
    string
    number
    boolean
    undedfined

# Important typeof Example
     You may notice something strange:

     console.log(typeof null);

Output:
    object
    
     This is historical JavaScript behaviour.

     *Remember it for interviews:*
      
      typeof null returns "object".

# Primitive vs Non-Primitive

Primitive
     String
     Number
     Boolean 
     Undefined
     Null
     BigInt
     Symbol

Non-Primitive
     Object
     Array
     Function

# Quick Reference

Data Type             Example

String                 "Rohit"
Number                  25
Booelan                 true
Undefined               undefined
Null                    null
BigInt                  100n
Symbol                  Symbol("id")
Object                  { name: "Rohit"}
Array                   ["React", "JavasScript"]

# React Connection

     React applications constantly work with different data types.

* String
  const name = "Rohit";

* Number 
  const count = 10;

* Boolean
  const isLoggedIn = true;

* Object 
  const user = {
    name: "Rohit",
    age: 25
  };

* Array 
  const products = [
    "Laptop",
    "Phone",
    "Tablet"
  ];

      Understanding these types is essential before learning React state, props, APIs, and components.

# Practise

 create variable for:

     const name = "Your Name";
     const age = 25;
     const isStudent = true;
     const skills = ["JavaScript", "React"];
     const uder = {
        name: "Your Name".
        age: 25
     };

     Then use typeof to check each value.

# Interview Questions

Q1. What are Javascript data types?
     JavaScript data types describe the kindo of stored in a variable. They are divided into primitive and non-primitive types.

Q2. What is difference between null and undefined?
     undefined usually means a value has not been assigned, while null represents an intentionally empty value.

Q3. What is the difference between an array and an object?
     An array stores an ordered collection of values, while an object stores data as key-value pairs.

Q4. How do you check a variable's type?
    Use:
     typeof varaible

Q5. What does typeof null return?
     "object"
     This is a historical JavaScript behaviour.
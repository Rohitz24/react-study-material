# JavaScript Objects
     
     Objects are extremely importantfor React. Props, API responses, users, products, configuration, and most real application data are represented as objects.

1. What is an Object?

     An object stores data using key-value pairs.

     const user = {
        name: "Rohit",
        age: 25,
        city: "Nagpur"
     };

     Here:

         name  -> key
         "Rohit" -> value

         age -> key
         25 -> value

2. Access Object Properties
     
     * Dot notation

     console.log(user.name);
     console.log(user.age);

Output:
     
     Rohit
     25

     * Bracket notation

     console.log(user["name"]);
     console.log(user["age"]);

     Both methods work.

3. When to Use Bracket Notation
     
     Bracket notation is useful when the property name is stored in a variable.

     const property: "name"
     
     console.log(user[property]);

Output:
     
     Rohit

     This is called dynamic property access.

4. Add a Property
     
     You can add a new property:
      
         user.email = "rohit@example.com";

     Now: 

         console.log(user);

     The object contains:
       
          name
          age
          city
          email

5. Update a Property
      
         user.age = 26;

     Now:
         
         console.log(user.age);

Output:  
      
      26

6. Delete a Property
     
     Use delete:

     delete user.city

     Now city is removed

7. Object with Different Data Types

      An object can contain many types of values.

      const user {
        name: "Rohit",
        age: 25,
        isStudent: true,
        skills: ["JavaScript", "React"],
        address: {
            city: "Nagpur"
            country: "India"
        }
      };

      This is very common in real applications.

8. Nested Objects
     
     An object can contain another object.
      
      const user = {
        name: "Rohit",
        address: {
            city: "Nagpur",
            country: "India"
        }
      };

      Access:

         console.log(user.address.city);

Output:    
     
     Nagpur

9. Optional Chaining
     
     If a nested property might not exist, use ?.
       
         console.log(user?.address?.city);

       This prevents errors when an intermediate property is null or undefined.

       This is especially useful with API data in React.

10. Object Methods
    
     An object can contain functions.

     const user = {
        name: "Rohit",

        greet() {
          console.log("Hello");
        }
     };

     user.greet();

Output:
     
     Hello!

     A function stored inside an object is called a method.

11. this Keyword
     
     Inside an object method, this can refer to the object.

     const user = {
        name: "Rohit",

        greet() {
            console.log(`Hello ${this.name}`);
        }
     };

     user.greet();

Output:
      
      Hello Rohit

     Here:
      
         this.name
    
     refers to:
         
         user.name

12. Object Destructing Preview
     
     You can extract properties from an object.

     const uder = {
        name: "Rohit"
        age: 25
     };

     const { name, age } = user;

     console.log(name);
     console.log(age);

Output:
     
     Rohit
     25
     
13. Object Spread Preview
    
     You can copy object properties using ....

     const user = {
        name: "Rohit",
        age: 25
     };

     const updatedUser = {
        ...user,
        age:26
     };

     Now:

          console.log(updatedUser);
    
     Result:
         {
            name:"Rohit",
            age: 26
         }

         This is very important in React state managment.

14. Objects and Arrays Together
     
     Real- world data often looks like this:
       
       const user = [
        {
            id: 1,
            name: "Rohit",
            role: "Developer"
        },
        {
            id: 2, 
            name: "Amit",
            role: "Designer"
        },
        {
            id: 3,
            name: "Rahul",
            role: "Developer"
        }
       ];

     This is:

      Array
       ├── Object
       ├── Object
       └── Object
     
     This structure is extremely common when receiving data from an API.

15. Access Objects Inside an Array:
      
      Console.log(user[0].name);

Output:
      
      Rohit

      Second user:

      console.log(user[1].role);

Output:
      
      Designer

16. Use map() with Objects
      
      users.map((user) => {
          console.log(user.name);
      });

Output: 
      
      Rohit
      Amit
      Rahul

      In React:
     
      {users.map((user) => (
          <div key={user.id}>
           <h2>{user.name}</h2>
           <p>{user.role}</p>
          </div>
      ))}

      This is one of the most common React patterns.

17. Object Keys
      
      Object.keys() returns an array containing the object's keys.
       
       const user = {
          name: "Rohit".
          age: 25,
          city: "Nagpur"
       };

       console.log(objects.keys(user));

      Result:

       ["name", "age", "city"]

18. Object Values
      
      object.values() returns an array containig the values.

      console.log(object.values(user));

      Result:

      ["Rohit", 25, "Nagpur"]

19. Object Entries
      
      Object.entries() returns key-values pairs.

      console.log(object.entries(user));

      Result:
       
       [
          ["name", "Rohit"]
          ["age", 25],
          ["city", "Nagpur"]
       ]

       This can be useful when dynamically processing object data.

20. Check if a Property Exists
       
      You can use:

       "name" in user

      Result:
         
         true
      
      Or:
       
       "email" in user
     
      Result:

       false

21. Objects in React Props
      
      This is extremely important.

      Suppose we have:
        
         const user = {
          name: "Rohit",
          age: 25
         };

      Pass it to a component:

      <UserCard user={user} />

      Receive it:
        
        function UserCard({ user}) {
          return (
               <div>
                  <h2>{user.name}</h2>
                  <p>{user.age}</p>
               </div>
          );
        }

      This object is passed from the parent component to the child components as a prop.

22. API Response Example
      
      Imagine your backend sends:

      {
          "id": 1,
          "name": "Rohit",
          "email": "rohti@example.com",
          "role": : "Developer"
      }

      In React you might access:

      user.name
      user.email
      user.role

      This is why understanding objects is essential before learning APIs.

23. Object Immutability in React

      Avoid directly modifying an object stored in React state.

      For example, instead of:

      user.name = "Amit";

      you will commonly create a new object:

      setUser({
          ..user,
          name: "Amit"
      });

      The ...user copies the existing properties, and name is replaced.

      This concept becomes very important when we learn useState().

24. Quick Reference
       
       | Concept           | Example                 |
       | ----------------- | ----------------------- |
       | Create object     | `{ name: "Rohit" }`     |
       | Dot access        | `user.name`             |
       | Bracket access    | `user["name"]`          |
       | Add property      | `user.email = "..."`    |
       | Update property   | `user.age = 26`         |
       | Delete property   | `delete user.age`       |
       | Nested object     | `user.address.city`     |
       | Optional chaining | `user?.address?.city`   |
       | Object keys       | `Object.keys(user)`     |
       | Object values     | `Object.values(user)`   |
       | Object entries    | `Object.entries(user)`  |
       | Spread            | `{ ...user }`           |
       | Destructuring     | `const { name } = user` |
      
# Interview Questions

Q1. What is an object?
    
:-  An object is a collection of related data stored as key-value pairs.

Q2. Hwow do you access an object property?

Using dot notation:-
      user.name

Or bracket notation:-
      user["name"]

Q3. What is a nested object?

:-  An object containing another object.
      const user = {
       address: {
         city: "Nagpur"
      }
};

Q4. What does Object.keys() return?

:- An array containing the object's keys/

Q5. What does the spread operator do with objects?

:- It copies enumerable properties into a new object.

       const newUser = {
          ...user,
            age: 26
      };

Q6. Why are objects important in React?

:- React uses objects extensively for props, state, API responses, configuration, and application data.

Q7. Why shouldn't you directly mutate React state objects?

:- React state should be updated by creating a new value rather than directly modifying the existing state. This makes updates predictable and allows React to detect changes properly.
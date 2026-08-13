# JavaScript Functions
   
     Functions are reusable blocks of code. They are extremely important in React because React components themeselves are functions.

1. What is a Functions?
    
     A function is a reusable block of code that performs a specific task.

     function greet() {
        console.log("Hello Rohit!");
     }

     greet();

Output: 
     
     Hello Rohit!

     The function is created with:

     function greet() {
        ...
     }

     and called using:
     
     greet();

2. Function Parameters
     
     Parameters allow us to pass data into a function.

     function greet(name) {
        console.log("Hello $ {name}`);
    }

    greey("Rohit");

Output:
      
      Hello Rohit

      Here:

      name -> parameter
      "Rohit" -> argument

3. Multiple Parameterss
     
     function add(a,b) {
        console.log(a + b);
     }

     add(10, 20);

Output:
     
     30

4. return
     
     A function can return a value

     function add(a, b) {
        return a + b;
     }

     const result = add(10, 20);

     console.log(result);

Output:
     
     30

     Think of it as:

     Input
       ↓
     Function
       ↓
     Output

5. Why return is Important
    
     Compare:

     function add(a,b) {
        console.log(a + b);
     }

     with:

     function add(a, b) {
        return a + b;
     }

     The second version allows us to use the result somewhere else:

     const total = add(10,20);

     const finalPrice = total * 2;

6. Function Expression
     
      A function can be stored inside a variable.

      const greet = function () {
          console.log("Hello");
      };

      greet();

      This is called a function expression.

7. Arrow Functions
      
      Modern JavaScript commonly uses arrow functions.

      instead of:
       
       function add(a, b) {
          return a + b;
       }

       You can write:

       const add = (a, b) => {
          return a + b;
       };

       Even shorter:

       const add = (a, b) => a + b;

       This is called an implicit return.

8. Arrow Function with One Parameter

      With one parameter, parantheses can be omitted:

      const greet = name => {
          consol.log(`Hello ${name}`);
      };

      However, keeping parantheses is also perfectly valid:

      const greet = (name) => {
          console.log(`Hello ${name}`);
      };

      Both work.

9. Default Parameters
     
      You can provide a default value.

      function greet(name = "Guest") {
          console.log(`Hello ${name}`);
      }

      greet();

      Output:
              
          Hello guest

      If a value is provided:

      greet("Rohit");

      Output:
          
          Hello Rohit

10. Callback Functions
      
      A callback is a function passed to another function.

Example:
      
      function greet(name, callback) {
          console.log(`Hello ${name}`);
          callback();
      }

      function done() {
          console.log("Finished!");
      }

      greet("Rohit", done);

      Output:
          
          Hello Rohit
          Finished!

      Callbacks are extremely important in JavaScript and React.

11. Functions with map()
      
      Remember our previous lesson:

      const numbers = [1, 2, 3];

      const doubled = numbers.map((number) => {
          return number * 2;
      })

      The function:

      (number) => {
          return number * 2;
      }

      is passed to map() as a callback.

12. Functions with forEach()
     
      const names = ["ROhit", "Amit", "Rahul"];

      names.forEach((name) => {
          console.log(name);
      });

      The arrow function runs once for each item.

13. Functions in React
      
      This is extremely important.

      A React component is commonly written as a function:

      function Welcome() {
          return <h1>Hello React!</h1>;
      }

      Then:

      <Welcome />

      React calls the function and user the returned JSX.

14. React Component with Parameters
     
      React uses props to pass data into components.
       
      function Welcome({ name }) {
          return <h1>Hello {name}</h1>;
      }

      Usage:
          
           <Welcome name="Rohit" />
      
      Result:
           Hello Rohit

      The { name } value comes from the component's props.

15. Event Handler Functions in React
     
      Functions are also used to respond to user actions.
      
      functions App() {

          const handleClick = () => {
               console.log("Button clicked!");
          };

          return (
               <button onClick={handleClick}>
               Click Me
               </button>
          );
      }

      When the user clicks
      
       handleClick()
            ↓
      "Button clicked!"

16. Don't call the Function Immediately
     
      Correct:
          
           <button onClick={handleClick}>
           Click
           </button>

      Usually incorrect:
           
           <button onCLick={handleClick()}>
            Click
           </button>

      Why?

      handleClick
          ↓
      passes the function
          ↓
      handleClick()
          ↓
      calls the function immediately

      This is a very common beginner React mistake.

17. Function Returning JSX
     
      React components return JSX:

      function User() {
           const name = "Rohit";
           
           return (
               <div>
                  <h1>{name}</h1>
               </div>
           );
        }
     
      The impotant concept is:
      
      Function
         ↓
      returns JSX
         ↓
      React renders UI

18. Pure FUnctions
     
      A pure function gives the same output for the same input and doesn't modify outside data.

      function add(a, b) {
          return a + b;
      }  

      For:

      add(2, 3);

      the result is always:

       5

      Pure functions are useful in React because predicatable code is easier to maintain.

19. Function Scope
      
      Variables declared inside a function are generally available only inside that function.

      function test() {
          const message = "Hello";

          console.log(message);
      }

      test();

      This works.

      But:

      console.log(message);

      outside the function will fail because message exists inside the function's scope.

20. Function Types - Qucik Comparison
      
      Type                        Example

      Function Declaration        function add() {}
      Function Expression         const add = function() {}
      Arrow Function              const add = () => {}
      Callback                    Function passed to another function

# React Connection
      
      function UserCard({ user}) {

          const handleClick = () => {
               console.log(user.name);
          };

          return (
               <div>
                 <h2>{user.name}</h2>

                 <button onClick={handleClick}>
                   Viw User
                 </button>
               </div>
          );
      }

      This small component uses:

      Function
        ↓
      Props
        ↓
      Arrow function
        ↓
      Event handler
        ↓
       JSX
      
      You'll use these concepts constantly in React.

# Interview Questions

Q1. What is a function?
     
      ~ A reusable block of code designed to perform a specific task.

Q2. What is an arrow function?

      ~ A shorter syntax for writing functions.

      const add = (a, b) => a + b;

Q3. What is a callback?

      ~ A function passed as an argument to another function.

Q4. What does return do?

      ~ It send a value back from a function and stops that functon's execution.

Q5. Why are functions important in React?
 
      ~ React components are commonly functions, and functions are also used for event handlers, callbacks, data processing, and hooks.

Q6. What's the difference between handleClick and handleClick() in onClick()?
 
      ~ onclick = {handleClick}

      passes the function.

      onClicks={handleClick()}
      calls it immediately while rendering.
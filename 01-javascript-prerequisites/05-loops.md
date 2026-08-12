# JavaScript Loops

     A loop repeats a block of code until a condition is met.

For example:
     
     console.log("Rohit");
     console.log("Rohit");
     console.log("Rohit");

     we can use loop.

1. for Loop
     
     The loop is one of the most common loops.

     * Syntax
      
         for (initializating; condition; update) {
            // code
         } 

Example:
 
     for (let i = 1; i <= 5; i++) {
        console.log(i);
     }

Output:
     1
     2
     3
     4
     5

How it works
     let i = 1 
         ↓ 
     i <= 5 ? 
         ↓ 
     run code 
         ↓ 
        i++ 
         ↓ 
     check condition again.

2. Loop Through an Array
    
     const fruits = ["Apple", "Banana", "Mango"];

     for (let i = 0; i < fruits.length; i++) {
        console.log(fruits[i]);
     }

Output:
     
     Apple
     Banana
     Mango

     Remember:

         Array indexes start from 0.

         Apple  -> 0
         Banana -> 1
         Mango  -> 2

3. while Loop

     A while loop runs while a condition is true/

     let count = 1;

     while (count <= 5 ) {
        console.log(count);
        count++;
     }

Output:

     1
     2
     3
     4
     5

     * Important

     Make sure the condtion eventually become false.

     Otherwise, you can create an infinite loop.

4. do...while
     
     do...while runs the code at least once.
     
     let count = 1;

     do {
        console.log(count);
        count++;
     } while (count <= 5);

Output:
     1
     2
     3
     4
     5

     Difference:

     while
     -> checks condition first

     do...while
     -> runs code first
     -> checks condition afterward

5. for...of
     
     for...of is useful for getting values from an iterable such as an array.

     const fruits = ["Apple", "Banana", "Mango"];

     for (const fruit of fruits) {
        console.log(fruit);
     }

Output: 
    
     Apple
     Banana
     Mango

     This is usually cleaner than manually managing an array index.

6. for..in
     
     for...in is commonly used to iterate over the keys of an object.

     const user = {
        name: "Rohit"
        age: 25,
        city: "Nagpur"
     };

     for (console key in user) {
        console.log(key);
     }
    
Output:
     
     name
     age
     city

     You can access the value using:

     console.log (user[key]);

Example:
     
     for (const key in user) {
        console.log(key, user[key]);
     }

Output:
     
     name Rohit
     age 25
     city Nagpur
    
* Important
     
     Prefer:
      
      for...of -> arrays
      for...in -> object keys

7. break

     break stops a loop immediately.

     for (let i =1; i <= 10; i++) {

        if (i === 5) {
            break;
        }

        console.log(i)
     }

Output:
     
     1
     2
     3
     4

     When i becomes 5, the loop stops.
 
 8. continue
    
     continue skips the current iteration and continues with the next one.

     for (let i = 1; i <= 5; i++) {

        if(i === 3) {
            continue;
        }

        console.log(i);
     }

Output:
     
     1
     2
     4
     5

     3 was skipped.

9. Nested Loops
    
     A loop can exist inside another loop.

     for (let i = 1; i <= 3; i++) {

        for (let j = 1; i <= 2; j++) {
            console.log(i, j);
        }
     }

Output:
     
     1 1
     1 2
     2 1
     2 2
     3 1
     3 2

     Nested loops are useful for some data-processing, problems, but avoid unnecessary nesting because it can make code harder to understand.

10. forEach()

     forEach() is an array method used to execute a function for every array item.

     const fruits = ["Apple", "Banana", "Mango"];

     fruits.forEach((fruits) => {
        console.log(fruit);
     });

Output:
    
     Apple
     Banana
     Mango

     It is often easier to read than a traditional for loop.

11. map() -- VERY IMPORTANT for React
     
     map() creates a new array by transformaing every item.

Example:
     
     const numbers = [1,2,3,4];

     const doubled = numbers.map((number) => {
        return number * 2;
     });

     console.log(doubled);

Output:
     
     [2,4,6,8]

     Short version: 

     const doubled = numbers.map(number => number * 2);

12. map() in React
    
     This is extremely important.

     Suppose we have:

     const users = [
        "Rohit",
        "Amit",
        "Rahul"
     ];

     We can display them in React:

     function Users() {
        const users = ["Rohit", "Amit", "Rahul"];

        return (
          <div>
            {users.map((user) => (
                <p>{user}</p>
            ))}
          <div>
        );
     }

     React will generate:

     Rohit
     Amit
     Rahul

     This is called list rendering.

13. key in React Lists

     When rendering lists, React expects a key.

     const users = [
        { id: 1, name: "Rohit" },
        { id: 2, name: "Amit" },
        { id: 3, name: "Rahul" },
     ];

     function Users() {
        return (
           <div>
           {users.map((user) => (
             <p> key={user.id}>
               {user.name}
             </p>
           ))}
           </div>
        );
     }

     Use a stable unique value such as:

     key={user.id}

     Avoid using array indexes as keys when the list can be reordered, inserted into, or deleted from.

14. forEach() vs map()

     This is an important distinction.

     * forEach()

     Used when you want to perform an action for every item.

     const numbers = [1, 2, 3];

     numbers.forEach(number => {
        console.log(number);
     });

     it does not create a new array for you.

     * map()

     Used when you want to transform items and createe a new array.

     const numbers = [1, 2, 3];

     const doubled = numbers.map(number => number * 2);

     Result:

     [2, 4, 6]

     React

     For rendering arrays, you will usually use:
     array.map(...)

15. Loop Comparison

     Loop                    Main Use
     
     for                     General repetition
     while                   Repeat while condition is true
     do...while              Execute at least once
     for...of                Iterate over object keys
     forEach()               Execute function for each array item
     map()                   Transform array/ React list rendering

16. Real-World Example

     Suppose we have products;

     const products = [
        { id: 1, name: "Laptop", price: 50000 },
        { id: 2, name: "Phone", price: 30000 },
        { id: 3, name: "Tablet", price: 20000 },
     ];

     Using map():

     const productNames = products.map((product) => {
        return product.name;
     });

     console.log(productNames);

Output:
     
     ["Laptop", "Phone", "Tablet"]

     In React:

     function Products() {
        const products = [
            { id: 1, name: "Laptop", price: 50000 },
            { id: 2, name: "Phone", price: 30000 },
            { id: 3, name: "Tablet", price: 20000 },
        ];

        return (
            <div>
              {products.map((product) => (
                <div key={product.id}>
                  <h2>{product.name}</h2>
                  <p>{product.price}</p>
                </div>
              ))}
            </div>
        );
     }

     This is pattern you'll use constantly in React applications.

# Interview Questions

Q1. What is loop?
     ~ A loop repeatedly executes a block of code while a condition or iteration rule is satisfied.

Q2. Difference between for...of and for...in?
     ~ for...of iterates over values, while for...in iterates over keys/properties.

     for (const value of array) {}

     for (const key in object) {}

Q3. Difference between foreach() and map()?
     ~ forEach() performs an operation for each item, with map() creates a new array containing transformed values.

Q4. Why is map() important in React?
     ~ React commonly uses map() to convert an array of data int0 an array of JSX elements.

      {users.map(user => (
        <p key={user.id}>{user.name}</p>
      ))} 

Q5. Why does React need a key when rendering lists?
     ~ The key helps React identify which list items have changed, been added, or removed.

Q6. Can map() modify the original array?
     ~ map() normally creates a new array. It does not modifty the original array itself.

Q7. What does break do?
     ~ It immediately exists the loop.

Q8. What does continue do?
     ~ It skips the current iteration and moves to the next iteration. 
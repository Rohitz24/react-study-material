# JavaScript Array?

1. What is an Array?

     An array stores multiple values in a single variable.
    
     const fruits = ["Apple", "Banana", "Mango"];

     Instead of:

     const fruit1 = "Apple";
     const fruit2 = "Banana";
     const fruit3 = "Mango";

     We can use one array;

     const fruits = ["Apple", "Banana", "Mango"];

2. Array Index
     
     Array index start from 0.

     const fruits = ["Apple", "Banana", "Mango"];

     Apple  -> index 0
     Banana -> index 1
     Mango  -> index 2

     Access values:

     console.log(fruits[0]);
     console.log(fruits[2]);

Output:
     
     Apple 
     Mango

3. Array Length
     
     Use .length to get the number of items.
     
     const fruits = ["Apple", "Banana", "Mango"];

     console.log(fruits.length);

Output: 
     
     3

     The last item can be accessed using:

     console.log(fruits[fruits.length - 1]);

4. Change an Array Item

     Arrays are mutable, meaning their elements can be changed.

     const fruits = ["Apple", "Banana", "Mango"];

     fruits[1] = "Orange";

     console.log(fruits);

     Result:
        
         ["Apple", "Banana", "Mango"]

5. push()
     
     Add an item to the end.

     const fruits = ["Apple", "Banana"];
     fruits.push("Mango");
     console.log(fruits);

     Result:

     ["Apple", "Banana", "Mango"]
     
6. pop()
     
     Removes the last item.

     const fruits = ["Apple", "Banana", "Mango"];

     fruits.pop();

     console.log(fruits);

     Result:

      ["Apple", "Banana"];

7. unshift()

     Add an item to the beginning.

     const fruits = ["Banana", "Mango"];

     fruits.unshift("Apple");

     console.log(fruits);

     Result:
     
     ["Apple", "Banana", "Mango"]

8. shift()
     
     Removes the first item.

     const fruits = ["Apple", "Banana", "Mango"];

     fruits.shift();

     console.log(fruits);

     Result:
      
      ["Banana", "Mango"];

9. includes()
    
     Checks whether an array contains a value.

     const skills = ["HTML", "CSS", "JavaScript", "React"];

     console.log(skills.includes("React"));

Output:

     true

Example:
     
     console.log(skills.includes("Python"));\

Output:
     
     false

10. indexOf()
    
     Finds the index of an item.

     const skills = ["HTML", "CSS", "JavaScript"];

     console.log(skills.indexOf("CSS"));

Output:
     
     1

     If the value doesn't exist:

     console.log(skills.indexOf("React"));

Output:
     
     -1

11. forEach()
    
     Runs a function for every item.

     const skills = ["HTML", "CSS", "React"];

     skills.forEach((skill) => {
        console.log(skill);
     })

Output:
     
     HTML
     CSS
     React

     forEach() is useful when you want to perform an action, but it does not create a new array.

12. map()
     
     map() creates a new array by transforming every item.

     const numbers = [1, 2, 3, 4];

     const doubled = numbers.map((number) => {
        return number * 2;
     })
     
     console.log(doubled);

     Result:
      
      [2, 4, 6, 8]

      Short version:

      const doubled = numbers.map(number => number * 2);

      React Connection

      This is one of the most important React patterns:

      {users.map((user) => (
          <p key={user.id}>{user.name}</p>
      ))}

13. filter()
     
      filter() creates a new array containing only items that satisfy a condition.

      const numbers = [1, 2, 3, 4, 5]

      const evenNumbers = numbers.filter((number) => {
          return number % 2 === 0;
      });

      console.log(evenNumbers);

      Result: 

          [2, 4]
     
      Real-world example:

      const products = [
          { name: "Laptop", price: 50000 },
          { name: "Phone", price: 30000 },
          { name: "Mouse", price: 1000 },
      ];

      const expensiveProducts = products .filter(
          product => product.price > 20000 
      );

      Result:

      Laptop
      Phone

      * React Connection

      You can filter data before displayin it:

      {products
         .filter(product => product.price > 20000)
         .map(product => (
          <p key={product.name}>{product.name}</p>
         ))}

14. find()
      
      find() returns the first item matching a condition.

      const number = [10, 20, 30, 40];

      const result = numbers.find(number => number > 20);
      
      console.log)result;

Output:
     
      30

      important difference:

      filter() -> returns an array
      find()   -> returns one item

15. findIndex()
      
      Returns the index of the first matching item.

      const numbers = [10, 20, 30, 40];

      const index = numbers.findIndex(number => number > 20);

      console.log(index);

Output:
      
      2

16. some()
      
      Checks whether at last one item satisfies a condition>

      const numbers = [1, 3, 5, 8];

      const hasEvenNumber = numbers.some(
          number => number % 2 === 0
      );

      console.log(hasEvenNumber);

Output:
       
       true

      Think:

           Does at least one item match?

17. every()
      
      Checks whether all item satisfy a condition.

      const numbers = [2, 4. 6, 8];

      const allEven = numbers.every(
          number => number % 2 === 0
      );

      console.log(allEven);

Output:
      
      true

      Think: 
            
            Do all items match?

18. Reduce()
      
      reduce() combines array values into one result.

Example:
       
       const numbers = [10, 20, 30];

       const total = numbers.reduce (
          (sum, number) => sum + number,
          0
       );

       console.log(total);

Output:
       
       60

      Think: 
          
           [10, 20, 30]
               ↓
            reduce
               ↓
               60

* Real-world example:
      
      calculate shopping-cart total:

      const cart = [
          {name: "Laptop", price: 50000},
          {name: "Mouse", price: 1000},
          {name: "Keyboard", price: 2000},
      ];

      const total = cart.reduce(
          (sum, item) => sum + item.price,
          0
      );

      consol.log(total);

      Result:

      53000

19. sort()
      
      Sorts array elements.

      const numbers = [5, 2, 8, 1];

      numbers.sort((a, b) => a - b);

      console.log(numbers);

      Result:
       
          [1, 2, 5, 8]

      Descending:
            
            numbers.sort((a, b) => b - a);

      Result:
          
           [8, 5, 2, 1]

      *  important: sort() mutates the original array.

      in React, you should be careful about directly mutating state arrays.

20. slice()
      
      const fruits = [ 
          "Apple",
          "Banana",
          "Mango",
          "Orange",
      ];

      const result = fruits.slice(1, 3);

      console.log(result);
      
      Result:
           
           ["Banana", "Mango"]

21. splice()
     
      splice() can add, remove, or replace items.

      const fruits = ["Apple", "Banana", "Mango"];

      fruits.splice(1, 1);

      console.log(fruits);

      Result:

           ["Apple", "Mango"]

      * Unlike slice(), splice() changes the original array.

22. Important Array Methods
      
      Remember this table:

      Method             Purpose                   Returns

      push()             Add at end                New length

      pop()              Remove from end           Removed item

      shift()            Remove from begining      Removed Item

      undhift()          Add at begining           New length

      includes()         Check value               Boolean

      indexOf()          Find index                Number

      forEach()          Execute for each item     undefined
      
      map()              Transform items           New array

      filter()           Select items              New array

      find()             Find first match          item/undefined

      findIndex()        Find first matchn index   Number

      some()             At least one matches      Boolean

      every()            All match                 Boolean

      reduce()           Combine values            Single value

      slice()            Copy part                 New array

      splice()           Add/remove items          Removes items


23. Arrays and React

      React applications frequently receive array from APIs.

Example:

      const users = [
          {
               id = 1,
               name: "Rohit",
               role: "Developer"
          },
          {
               id = 2,
               name: "Amit",
               role: "Designer"
          }
      ];

      Display them:

      function Users() {
          return (
               <div>
                 {users.map((user) => (
                     <div key={user.id}>
                       <h2>{uesr.name}</h2>
                        <p>{user.roe}</p>
                     </div>
                 ))}
                </div>  
          );
      }

      Filter them:

      const developers = users.filter(
          user => user.role === "Developer"
      );

      Find one:

      const user = users.find(
          user => user.id ===1
      );

      This combination:
      
      filter()
      find()
      map()
      reduce()

      is extremely important for real React applications.

24. React State and Arrays
      
      Later, you'll learn React state:

      const [users, setUsers] = useState([]);

      When updating arrays in React, prefer creating a new array instead of directly modifying the existing state.

      For exampple, adding a user:

      setUsers([
          ...users,
          newUser
      ]);

      Removing a user:

      setUSers(
          users.filter(user => user.id !==id)
      );

      This connects directly to the next JavaScript topic: spread syntax.

# Interview Questions

Q1. What is an array?
      ~ An array is an ordered collection of values stored in a single variable.

Q2. Difference between map() and filter()?
      ~ map() transforms every item and returns a new array.
      filter() returns a new array containing only items that satisfy a condition.

Q3. Difference between find() and filter()?
      
      ~ find()   -> first matching item
      filter()   -> all matching items

Q4. Whatt does reduce() do?
      ~ It processes array elements and combines them into a single result.

Q5. Difference between slice() and Splice()?
      ~ slice() -> does not modify original array
      splice()  -> modifies original array

Q6. Why is maP() important in React?
      ~ It is commonly used to convert an array of data into JSX elements for list rendering.

Q7. Why should you avoid directly mutating React state arrays?
      ~ React relies on state updates and references to determine when components need to render. Creating a new array makes state changes predictable.
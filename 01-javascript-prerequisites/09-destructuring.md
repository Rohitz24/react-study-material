# JavaScripting Destructuring

1. What is Destructuring?
    
     Destructuring allows you to extract values from an array or object and store them in variables.

     Without destructuring:

     const user = {
        name: "Rohit"
        age: 25
     };

     const name = user.name;
     const age = user.age;

     With destructuring:

     const user = {
        name: "Rohit",
        age: 25
     };

     Now:
         
         console.log(name);
         console.log(age);

Output:
      
      Rohit
      25

2. Object Destructuring
     
     Basic Syntax:
       
       const { property1, property2 } = object;

Example:
      
      const student = {
        name: "Rohit",
        course: "MCA",
        age: 25
      };

      const { name, course, age } = student;

     You now have:

     name 
     course 
     age

     as seprate variables.

3. Destructure Only What You Need
      
      You don't have to extract every property.

      const user = {
        name: "Rohit",
        age: 25,
        city: "Nagpur"
      };

      const { name }  = user;

      console.log(name);

Output:
      
      Rohit

4. Rename Variables
     
     Sometimes you want a different variable name.

     const user = {
        name: "Rohit",
        age: 25
     };

     const { name: userName, age: userAge } = user;

     console.log(userName);
     console.log(userAge);

Output:
     
     Rohit 
     25

     The Syntax:

     const { name: userName } = user;

     means:

     object property  -> variable name
     name             -> userName

5. Default Values
     
     You can provide a default value.

     const user = {
        name: "Rohit"
     };

     const { name, age = 25 } = user;

     console.log(name);
     console.log(age);

Output:
      
      Rohit
      25

      if age doesn't exist 25 is used.

6. Nested Object Destructuring
     
     consider:

     const user = {
        name: "Rohit",
        address: {
            city: "Nagpur",
            country: "India"
        }
     };

     You can destructure:

     const {
        name,
        address: { city, country }
     } = user;

     Now:

     console.log(name);
     console.log(city);
     console.log(country);

Output:
      
      Rohit
      Nagpur
      India

7. Array Destructurin
     
     Arrays use square brackets:

     const numbers = [10, 20, 30];

     const [a, b, c] = numbers;

     console.log(a);
     console.log(b);
     console.log(c);

Output:
      
      10
      20
      30

     Remember:

     object -> {}
     Array  -> []

8. Array Destructuring Uses Position
     
     This is important.

     const colors = ["red", "green", "blue"];

     const [first, second, third] = colors;

     Result:

     first -> red
     second -> green
     third -> blue

     Unlike objects, array destructuring depends on position.
    
9. Skip Array Values
     
     You can skip values commas.

     const numbers = [10, 20, 30];

     const [, second] = numbers;

     console.log(second);

Output:
     
     20

Example:
      
      const numbers = [10, 20, 30];

      const [first, , third] = numbers;

     Result:

     first -> 10
     third -> 30

10. Rest with Destructuring
     
     You can collect the remaining values using ... .

     const numbers = [10, 20, 30, 40];

     const [ first, ...rest] = numbers;

     console.log(first);
     console.log(rest);

Ouput:
     
     10
     [20, 30, 40]

11. Destructuring Function Parameters
     
     This is extremely important for React.
    
     * Without destructuring:

     function greet(user) {
        console.log(user.name);
     }

     * With destructuring:

     function greet({ name }) {
        console.log(name);
     }

     * call:

     greet({
        name: "Rohit"
        age: 25
     });

Output:
      
      Rohit

12. Destructuring React Props
     
     This is something you'll see constantly.

     *Without destructuring:

     function UserCard(props) {
        return (
            <div>
               <h2>{props.name}</h2>
                 <p>{props.age}</p>
            </div>    
        );
     }

     With destructuring:

     function UserCard({ name, age }) {
        return (
            <div>
               <h2>name</h2>
                <p>{age}</p>
             </div>   
            );
     }

     Usage:
         
         <UserCard
             name="Rohit"
             age={25}
             />
     
     Much cleaner.

13. The Most Important React Example
     
     function UserCard({ name, role, age }) {
        return (
            <div>
               <h2>{name}</h2>
                <p>{role}</p>
                <p>{age}</p>
             </div>
        );
     }

     Here:

     {name, role, age}

     is object destructuring.

14. useState() and Array Destructuring
     
     This is one of the most important things to understand before learning React.
     
     You will eventually write:

     const [count, setCount ] = useState(0);

     Why?

     useState(0) returns an array containing two values:

     [
        currentState,
        functionToUpdateState
     ]

     Conceptually:

     const result = useState(0);

     const count = result[0];
     const setCount = result[1];

     Array destructuring lets us write:

     const  [count, setCount] = useState(0);

     This is why understanding array destructuring is essential for React.

15. Swapping Variables
     
     Destructuring makes swapping values easy.

     * Without destructurin:

     let a = 10;
     let b = 20;

     const temp = a;
     a = b;
     b = temp;

     * With destructuring:

     let a = 10;
     let b = 20;

     [a, b] = [b, a];

     Now:
     a  -> 20
     b  -> 10

16. Destructuring API Data
     
     Suppose an API returns:

     const response = {
        id: 101,
        name: "Rohit",
        email: "rohit@example.com;
        role: "Frontend Developer"
     };

     Instead of:

     console.log(response.name);
     console.log(response.email);
     console.log(response.role);

     you can write:

     const {name, email, role } = response;

     console.log(name);
     console.log(email);
     console.log(role);

     This makes API-related code much cleaner.

17. Destructuring in .map()
    
     Suppose:

     const users = [
        { id: 1, name: "Rohit", role: "Developer" },
        { id: 2, name: "Amit", role: "Designer" }
     ];

     * Normal:

     users.map((user) => {
        console.log(user.name);
     });

     * With destructuring:

     users.map(({ name, role }) => {
        console.log(name, role);
     });

     Very useful in React:

18. React .map() Example
     
     Instead of:

     {users.map((user) => (
        <div key={user.id}>
          <h2>{user.name}</h2>
           <p>{user.role}</p>
        </div>
     ))}

     you can write"
     {users.map(({ id, name, role }) => (
       <div key={id}>
         <h2>{name}</h2>
         <p>{role}</p>
       </div>
     ))}

     Both are correct.

19. Object vs Array Destructuring

     Remember:

     Object:

     const user = {
        name: "Rohit",
        age: 25
     };

     const {name, age } = user;

     uses:
     {}

     and matches property names.

     Array:

     const numbers = [10, 20];

     const [first, second] = numbers;

     Uses:
     []
     and matches position

20. Quick Comparison

| Type               | Syntax               | Matching        |
| ------------------ | -------------------- | --------------- |
| Object             | `{}`                 | Property name   |
| Array              | `[]`                 | Position        |
| Function parameter | `function({ name })` | Object property |
| React props        | `function({ name })` | Prop name       |
| `useState`         | `[state, setState]`  | Position        |

# Interview Questions

Q1. What is destructuring?
    
     Destructuring is a JavaScript syntax for extracting values from arrays or objects into variables.

Q2. Difference between object and array destructuring?
     
     Object destructuring uses property names:

     const { name } = user;

     Array destructuring uses positions:

     const [first] = numbers;

Q3. Why is destructuring common in React?
     
     It makes props, statr values, API data, and function parameters easier to work with.

Q4. Explain:
     
     const [const, setCount] = useState(0);

     useState() returns an array containing the current state and a state-update function. Array destructuring assigns those values to count and setCount.

Q5. What does this mean?
    
     function User({ name }) {}

     It means the function receives an object and extract its name property.
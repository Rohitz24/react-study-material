# JavaScript Spread & Rest Operators

1. What is ...?
    
     The three dots:
     ...
     are called the spread syntaxa or rest syntax, depending on how they are used.

     The same sayntax has two different purposes:

     Spread -> expands values
     Rest   -> collects values

2. Spread with Arrays
     
     Suppose:
     
     const numbers = [1, 2, 3];

     You can copy the array:

     const copy = [...numbers];

     console.log(copy);

Output:

      [1, 2, 3]
    
     Think:
      numbers
     [1, 2, 3]
         ↓
     ...numbers
         ↓
      1, 2, 3

3. Combine Arrays
      
      You can combine arrays easily:

      const frontend = ["HTML", "CSS"];
      const backend = ["Java", "Spring Boot"];

      const skills = [...frontend, ...backend];

      console.log(skills);

Output:
      
      ["HTML", "CSS", "Java", "Spring Boot"]

4. Add Items While Copying
       
       const numbers  = [2, 3, 4];
       const newNumbers = [1, ...numbers, 5];
       console.log(newNumbers);

Ouputt:
     
    [1, 2, 3, 4, 5]
    
     This is useful when you want to create a new array.

5. Spread with Objects
     
     Suppose:

     const user = {
        name: "Rohit"
        age: 25
     };

     Copy it:

     const copy = {
        ...user
     };

     Result:

     {
        name: "Rohit",
        age:25
     }

6. Update an Object
     
     This is one of the most important React patterns.

     Suppose:

     const user = {
        name: "Rohit",
        age: 25,
        city: "Nagpur"
     };

     You want to change the age.

     instead of modifying the original:

     user.age = 26;

     create a new object:

     const updateUser = {
        ...user,
        age:26
     };

     Result:
     {
        name: "Rohit",
        age: 26,
        city: "Nagpur"
     }

     The later age: 26 overrides the copied age: 25.

7. Why Order Matters
    
     Consider:

     const user = {
        name: "Rohit",
        age: 25
     };

     const updatedUser = {
        age: 30,
        ...user
     };

     Result:

     {
        age:25.
        name: "Rohit"
     }
     
     Why?

     Beacuse:

     age: 30
       ↓
     ...user
       ↓
     age: 25

     The later property wins.

     Ususally, when updating an object, write:
     {
        ...user,
        age: 30
     }

8. Spread and React State
     
     This pattern is extremely important:

     setUser({
        ...user,
        name: "Amit"
     });

     Suppose state is:

     const [user, setUser] = useState({
        name: "Rohit",
        age: 25,
        role: "Developer"
     });

     To update only the name:

     setUser({
        ...user,
        name: "Amit"
     });

     The other properties remain:
     name -> Amit
     age  -> 25
     role -> Developer

9. Spread with React Arrays
     
     Suppose: 
        
        const [skills, setSkills] = useState([
            "HTML",
            "CSS"
        ]);

     Add a new skill:

     setSkills([
        ...skills,
        "React"
     ]);

     Result:

     ["HTML", "CSS", "React"]

     You create a new array instead of directly changing the old one.
    
10. Add item at Begining

     setSkills([
        "JavaScript",
        ...skills
     ]);

     Result:
     ["JavaScript", "HTML", "CSS"]

11. Remove an Item with filter()
    
     Suppose

     const skills = [
        "HTML",
        "CSS",
        "React"
     ];

     Remove "CSS":

     const updatedSkills = skills.filter(
        skill => skill !== "CSS"
     );

     Result:

     ["HTML", "React"]

     in React:

     setSkills(
        skills.filter(skill => skill !== "CSS")
     )

     This is another important immutable-state pattern.

12. Spread with Function Arguments
    
     Suppose:

     function add(a, b, c) {
        return a + b + c;
     }

     const number = [10, 20, 30];
     console.log(add(...numbers));

Output:
      
      60

     Without spread, you'd have to write:
     
     add(numbers[0], numbers[1], numbers[2]);

13. Spread with Strings
     
     spread can also expand a string:

     const name = "Rohit";

     const letters = [...name];

     console.log(letters);

     Result:

     ["R", "o", "h", "i", "t"]

14. Rest Parameters
     
     Now let's look the other use of ....
     
     Rest collects multiple arguments into an array.

     function add(...numbers) {
        console.log(numbers);
     } 

     add(10, 20, 30, 40);

Output:
    
     [10, 20, 30, 40]

     Here:
        
        ...numbers
    
     is rest, not spread.

15. Rest Parameter Example
     
     You can use it to calculate a total:

     function add(...numbers) {
        return numbers.reduce(
            (total, number) => total + number,
            0
        );
     }

     console.log(add(10, 20, 30));

Ouput:
    
     60

     And:
      
      console.log(add(10, 20, 30, 40, 50));

Ouput:
     
     150

16. Rest with Normal Parameters
     
     You can have normal parameters before the rest parameter.

     function greet(greeting, ...names) {
        console.log(greeting);
        console.log(names);;
     }

     greet("Hello", "Rohit", "Amit", "Rahul");

Output:
     
     Hello
     ["Rohit", "Amit", "Rahul"]

     The rest parameter must be the last parameter.

     Correct:

     function test(a, b, ...rest) {}

     Incorrect:

     function test(...rest, a, b){}

17. Rest with Array Destructuring
      
      Remember destructuring:

      const numbers = [10, 20, 30, 40];

      const [first, ...rest] = numbers;

      console.log(first);
      console.log(rest);

Output:
     
     10
     [20, 30, 40]

     Here:

     first -> 10
     rest  -> [20, 30, 40]

18. Rest with Object Destructuring
     
     You can also collect remaining object properties.

     const user = {
        name: "Rohit",
        age: 25,
        city: "Nagpur"
     };

     const { name, ...otherDetails }= user;

     console.log(name);
     console.log(otherDetails);

Output:
     
     Rohit
     {
        age: 25,
        city: "Nagpur"
     }

19. Spread vs Rest
     
     This is the most important distinction.

     Spread

     Expands something.

     const numbers = [1, 2, 3];

     console.log(...numbers);

     Conceptually:
     
     [1, 2, 3]
       ↓
      1 2 3

     Rest:

     Collects multiple values.

     function test(...numbers) {
        console.log(numbers);
     }

     Conceptually:
       1 2 3
         ↓ 
      [1, 2, 3]
     
     Remember:
     
     Spread -> expands
     Rest   -> collects

20. React Props and Spread
     
     Suppose:

     const user = {
        name: "Rohit",
        age: 25,
        role: "Developer"
     };

     You can pass the properties individually:

     <UserCard
        name={user.name}
        age={user.age}
        role={user.role}
     />

     Or use spread props:

     <UserCard {...user} />

     This is equivalent to passing:

     <UserCard
        name="Rohit"
        age={25}
        role="Developer"
     />

     The component:

     function UserCard({ name, age, role }) {
        return (
            <div>
              <h2>{name}</h2>
              <p>{age}</p>
              <p>{role}</p>
            </div>
        );
     }

21. Spread with Nested Objects
     
     Be careful:

     const user = {
        name: "Rohit",
        address: {
            city: "Nagpur",
            country: "India"
        }
     };

     const updatedUser = {
        ..user,
        address: {
            ...user.address,
            city: "Pune"
        }
     };

     Result:
     {
        name: "Rohit",
        address: {
            city: "Pune",
            country: "India"
        }
     }

     This patterns becomes useful when updating nested React state.

22. Important Warning: Spread is Shallow
    
     Consider:

     const user = {
        name: "Rohit",
        address: {
            city: "Nagpur"
        }
     };

     const copy = {
        ...user
     };

     The top-level object is copied, but nested objects are still references to the same nested object.

     Conceptually:

     copy
     |___name -> copied
     |___address -> same nested reference

     That's why nested updates often require:

     {
        ..user,
        address: {
            ...user.address,
            city: "Pune"
        }
     }

23. Real React Example
     
     Suppose:

     const [user, serUser] = useState({
        name: "Rohit",
        age: 25,
        address: {
            city: "Nagpur"
        }
     });

     Update the city:

     setUser({
        ...user,
        address: {
            ...user.address,
            city: "Pune"
        }
     });

     Notice the two spreads:

     ...user
     ...user.address

     One copies the user object.

     The other copies the nested address object.

24. Common Beginner Mistake
     
     Don't confuse these:

     const newArray = [...array];

     with:
     
     const newArray = array;

     The second one does not create a new array.

     const a = [1, 2, 3];
     const b = a;

     b.push(4);

     console.log(a);

Ouput:
     
     [1, 2, 3, 4]
    
     Both variables refer to the same array.

     Using spread:

     const a = [1, 2, 3];
     const b = [...a];

     b.push(4);

     console.log(a);
     console.log(b);

Output:
     [1, 2, 3]
     [1, 2, 3, 4]

25. Quick Reference
    
| Syntax                     | Meaning                             |
| -------------------------- | ----------------------------------- |
| `[...array]`               | Copy/expand array                   |
| `{...object}`              | Copy/expand object                  |
| `function(...args)`        | Collect arguments                   |
| `[first, ...rest]`         | Collect remaining array values      |
| `{name, ...rest}`          | Collect remaining object properties |
| `<Component {...props} />` | Spread props                        |

# Interview Questions

Q1. What is the spread operator?

     Spreas expands the elements/properties of an iterable or object.
    
     Example:
              
              const newArray = [...oldArray];

Q2. What is the rest operator?
     
     Rest collects multiple values into a single array or remaining properties into an object.

     function add(...numbers) {}

Q3. Difference between spread and rest?
     
     Spread -> expands
     Rest   -> collects

Q4. Why is spreas important in React?
     
      It is commonly used to create new arrays/objects when updating state.

      setUser({
        ...user,
        name, "Amit"
      });

Q5. How do you add an item tp a React state array?
     
     setItems([
        ...items,
        newItem
     ]);

Q6. How do you remove an item?
     
     Usually with filter();

     setItems(
        items.filter(item => item.id !== id)
     );

Q7. Is spread a deep copy?
     
     No. spread creates a shallow copy.

* React Patterns to Memorize

     Add to array
       setItems([
         ...items,
         newItem 
     ]);

     Update object
       setUser({
       ...user,
       name: "Amit"
     });

     Update nested object
      setUser({
      ...user,
      address: {
     ...user.address,
     city: "Pune"
     }
     });

     Pass all props 
     <UserCard {...user} />
     Collect function arguments
     function add(...numbers) {
     // ... 
     }
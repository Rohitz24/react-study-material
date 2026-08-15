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
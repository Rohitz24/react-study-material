# JavaScript Operators
     Operators are symbols used to perform operations on values.

Example:
      const result = 10 + 5;
      console.log(result);

Output:
     15
    
1. Arithmetic Operators
     Used for mathematical calculations.
    
Operator        Meaning          Example          Result
   +            Addition         10 + 5            15
   -            Subtraction      10 - 5            5
   *            Multiplication   10 * 5            50
   /            Division         10 / 5            2
   %            Remainder        10 % 3            1
   **           Power            2 ** 3            8

Example:
     
     const pricec = 100;
     const quantity = 3;

     const total = price * quantity;
     console.log(total);

Output:
     300

2. Assignment Operators
     Used to assign or update values.
      let count = 10;

      Common operators:

      count += 5;  // 15
      count -= 3;  // 12
      count *= 2;  // 24
      count /= 4;  // 6

      Instead of:

      count = count + 5;

      you can write:

      count += 5;

      React Connection

     You'll frequently see this concept when updating values.
     However, React state should normally be updated using its setter rather than directly modifying the variable.

3. Comparison Operators
     Comparison operators compare two values and return true or false.
    
     const age = 25;
     console.log(age > 18);

Output: 
     true

     Common Operators:
      
      Operator                    Meaning
       >                          Greater than
       <                          Less than
       >=                         Greater than or equal
       <=                         Less than or equal 
       ===                        Strictly equal
       !==                        Strictly not equal

Example: 
     const age = 20;
     console.log(age >= 18);

Output: 
     true

4. == vs ===
     This is very important.

  *   ==
      Performs type conversion when comparing values.
      
      console.log(5 == "5");
      
      Result:
      true
  
  *  ===
      Checks both value and data type.
      console.log(5 === "5");

      Result:
      false

      * Why?

      5   -> number
      "5" -> string

      Best Practice
      prefer:

      ===
      !==

      Over: 

      == 
      !=
       in modern JavaScript.

5. Logical Operators

     Logical opertors combine conditions.

     * AND &&

     Returns true when both conditions are true.

     const age = 25;
     const hasID = true;

     console.log(age >= 18 && hasID);

     Result:
     true

     * React Example

      {isLoggedIn && <h1>Welcome!</h1>}

     Meaning:
      If isLoggedIn is true, display the leading.

     * OR ||

     Returns true if at least one conditon is true.

     const isAdmin = false;
     const isManager = true;

     console.log(isAdmin || isManager);

     Result:
     true

     * Not !
      
      Reverses a Boolean value

      const isLoggedIn = true;
      console.log(!isLoggedIn);
      
      Result:
      false

6. Ternary Operator
    
    The ternary opertor is a short way to write a simple if...else.

Synatax:
     
     Condition ? valueIfTrue : valueIfFalse

Example: 
     const age = 20;

     const message = age >= 18
     ? "Adult"
     : "Minor";

     console.log (message);

Output:
     
    Adult

    * React Example

     Ternaries are commonly used for conditional rendering:

     {isLoggedIn ? (
        <Dashboard />
     ) : (
        <Login />
     )}

     Meaning: 
     Logged in    -> Dashboard
     Not logged in -> Login

7. Nullish Coalescing ??
     ?? provides a fallback when the value is null or undefined.

     const username = null;
     const name = username ?? "Guest";
     console.log(name);
    
Output:
     Guest
    
    Another Example:
     
     const username = "Rohit";
     const name = username ?? "Guest";
     console.log(name);

Output:
     Rohit

*   React/API Connection
     This is useful when API data might be missing:
     <p>{user.name ?? "unknown User"}</p>
    
8. Optional Chaining ?.

     Optional chaining lets you safely access nested properties.

     ~ Without optional chaining:

     user.profile.name

     if profile doesn't exist, JavaScript can throw an error.
    
     ~ With optional chaining:
       
     user?.profile?.name
     
     if something is missing, it returns:
     undefined
     instead of throwing an error.

     * React/API Example
     <p>{user?.profile?.name}</p>
     This is extremely common when working with API responses.

9. Increment and Decrement
    
     ~Increment
      
      let count = 5;
      count++;

      Now:
      6
     
     ~Decrement
      
       count--:
       Now:
       5

       You will often see these in loops and counters.

10. Operator Precedence
    
     JavaScript follows an order when evaluating expressions.
Example:
     
      const result = 10 + 5 * 2;

      Multipactions happen first:
      
      5 * 2 = 10

      10 + 10 = 20

     Result:
     20

     Use parentheses when you want to make the order clear:
     
     const result = (10 + 5) * 2:
     Result:
     30

     *  React Operators Should Know
     When learning React, these are especially important:

     ===   Strict comparison
     !==   Strict inequality
     &&    Conditional rendering
     ||    Fallback values
     ??    Null?undefined fallback
     ?.    Safe property access
     ?:    Conditional rendering

Example:

      function  User ({ user}) {
        return (
            <div>
              <h2>{user?.name ?? "Guest"}</h2>

              {user?.isAdmin && (
                <p>Administrator</p>
              )}

              {user?.isLoggedIn ? (
                <p>Welcome back!</p>
              ) " (
                <p>Please login.</p>
              )}
              </div>
        );
      } 

      This small example uses several JavaScript operators that you'll use regularly in React.

# Interview Questions

Q1. What is the difference between == and ===?
~    == allows type conversion, while === checks both value and type.

Q2. What does && do?
~   It evaluates multiple conditions and is also commonly used in React for conditional rendering.

Q3. What is the ternary operator?
~   A short way to write a simple if...else expression.
condition ? trueValue : falseValue

Q4. What is optional chaining?
~   ?. Safely accesses properties that may not exist .
user?.profile?.name

Q5. What is the difference between || and ?? ?
~   || uses a fallback for any falsy value such as 0, false, "", null, or undefined. ?? only uses a fallback for null pr undifined.

Example:

0 || 10
// 10

0 ?? 10
// 0 



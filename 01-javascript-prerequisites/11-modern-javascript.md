# JavaScript Modern Syntax

We will learn:
     1. Optional Chaining?.
     2. Nullish Coalescing??
     3. Ternary Operator?:
     4. Combining them in React

1. Optional Chaining ?.
     
     Optional chaining lets you safely access properties that might not exist.

     Suppose:

          const user = {
            name: "Rohit"
          };

     This is safe:

     console.log(user.name);

     But this can cause an error:

     console.log(user.address.city);

     Because:
      
      user.address
         ↓
      undefined
         ↓
      .city ❌

      * Using ?.

      console.log(user.address?.city);

      Result:
          
          undefined
    
     Instead of throwing an error.
    
2. Multiple Optional Chains
      
      Consider API data:
    
     const user = {
        profile: {
            address: {
                city: "Pune"
            }
        }
     };

     You can safely access:

     console.log(
        user?.profile?.address?.city
     );

Output:
     
     Pune

     If ant property doesn't exist:

     user?.profile?.address?.city

     simply produces:

     undifined

3. Optional Chaining with Arrays 

     Suppose:

     const users = [
        {
            name:"Rohit"
        }
     ];

     console.log(users[0]?.name);

Output: 
     
     Rohit

     If the array is empty:

     const users = [];

     console.log([users[0]?.name])l

     Result"

     Undefined

     No error.

4. Optional Chaining with Functions
    
     Optional chaining can also check whether a function exists.

     const user = {
        name: "Rohit"
     };

     user.login?.();

     If login doesn't exist, JavaScript won't throw an error.

5. Why Optional Chaninig Is Important in React
     
     Imagine your React compnent recives API data:

     const user = {
        profile: {
            name: "Rohit"
        }
     };

     You mighy write:
     <h2>{user?.profile?.name}</h2>

     If the API hasn't loaded the data yet, optional chaining can prevent errors.

     This is very common with:

     * API responses
     * nested objects 
     * user profiles
     * configuration objects
     * optional props

6. Nullish Coalescing ??
     
     The ?? opertor provides a default value when the left side is:

     null 
     undefined

Example:
      
      const name = null:

      const displayName = name ?? "Guest";

      console.log(displayName);

Output:
     
     Guest

7. Another Example

     const username = undefined;

     const displayName = username ?? "Guest";

     console.log(displayName);

Output:
      
      Guest

8. Important Difference: ?? vs ||
     
     This is very important.

     consider:

     const value = 0;

     using ||:

     const result = value || 100;

     console.log(result);

Output:
     
     100

     Because 0 is considered falsy.

     But:

     const result  = value ?? 100;

     console.log(result);

Ouput:
     
     0

     Because ?? only considers:

     null 
     undifned

     as missing.

9. Values Considered Falsy
      
      JavaScript considers these values falsy:

      false
      0
      ""
      null 
      undefined
      NaN

      But ?? only reacts to:

      null 
      undefined

      That's why:
      0 ?? 100

      returns0

      while:

      0 || 100

      returns:

      100

10. React Example with ??
     
     Suppose:
     
     const user = {
        name: null
     };

     You can display:

     <h2>{user.name ?? "Guest User"}</h2>

     Result:

     Guest User

11. Optional Chaining + Nullish Coalescing
     
     These two operators are often used together.

     const user = {};

     const city = user?.address?.city ?? "Unknown";

     console.log(city);
    
Ouput:
     
     Unknown

     Think:
     
       user
        ↓
      address?
        ↓
      city?
        ↓
      if null/undefined
        ↓
      "Unknown"

      This pattern is extremely useful with API data.

12. Ternary Operator? :
    
     The ternary operator is a short way of writing an if...else.

     Normal:

     const age = 25;

     let message;

     if (age >= 18) {
        message = "Adult";
     } else {
        message = "Minor";
     }

     Using ternary:

         const age = 25;

         const message = 
           age >= 18
           ? "Adult"
           :  "Minor";

     Result:
      
          Adult

13. Ternary Syntax
     
     Remember: 
         
         condition ? valueIfTrue : valueIfFalse

Example: 
      
      const isLoggedIn = true;

      const message = 
          isLoggedIn
          ? "Welcome"
          : "Please login";

14. Ternary in React
     
     This is one of the most common uses.

     function App() {
        const isLoggedIn = true;
        
        return (
            <div>
              {isLoggedIn
               ? <h1>Welcome~!</h1>
               : <h1>Please Login</h1>
              }
            </div>
        );
     }

     If:
         
         isLoggedIn = true
    
     React shows:
         
         Welcome!
    
     If:
        
         isLoggedIn = false
    
     React shows:
         
         Please Login

15. Ternary for Buttons
     
     <buttons>
        {isLoggedIn ? "Logout" : "Login"}
     </button>

     This produces"
       
       Logged in -> Logout
       Logged Our -> Login
    
     Very common in React applications.

16. Ternary with CSS Classes
     
     <div className={isActive ? "active" : "inactive"}>
       Profile
     </div>

     if: 

         isActive  = true
    
     then:

         className="active"

     Otherwise:

         className="inactive"

17. Nested Ternary

     You technically can write:

     const score = 80;

     const grade = 
        score >= 90 
          ? "A"
          : score >= 75
            ? "B"
            : "C";
    
     But avoid excessive nested ternaries because they become difficult to read.

     Prefer:
       
         if / eles if / else

     when the logic becomes complicated.

18. Ternary vs &&
     
     React also commonly uses && for rendering something only when a condition  is true.

Example: 
      
         {PisLoggedIn && <h1>Welcome</h1>}

     If:
        
         isLoggedIn = true
    
     React displays:
         
         Welcome!
    
     If false, nothing is rendered.

19. && vs Ternary
     
     Use && when you have:

     show something
     OR
     show nothing

Example:
      
      {isAdmin && <AdminPanel />}
    
     Use ternary when you have:

     show A
     OR
     show B

Example:
     
     {isLoggedIn ? <Dashboard /> : <Login />}

20. Important React Pattern
     
     You will frequently see:

     {user?.profile?.name ?? "Guest"}
     
     This means:

     Does user exist?
          ↓
     Does profile exist?
          ↓
     Does name exist?
          ↓
     Yes → display name
     No  → display "Guest"

     This is an excellent pattern to understand before working with APIs.

21. Combine Everything
     
     function UserProfile({ user }) {
        const name = user?.profile?.name ?? "Guest";

        return (
            <div>
               <h2>{name}</h2>

               {user?.isLoggedIn
                 ? <button>Logout</button>
                 : <button>Login</button>
               }
            </div>
        );
     }

     This small example uses:

     ?.  -> optional chaining
     ??  -> Default value
     ?:  -> Conditional rendering

22. Real API Example
     
     Imagine your API returns:

     const response = {
        user: {
            profile: {
                name: "Rohit"
            }
        }
     };

     You could safely display:

     <h1>
        {response?.user?.profile?.name ?? "Unknown User"}
     </h1>

     If the API returns:

     {
        user: null
     }

     You still get:
         
         Unknown User
    
     Instead of an error.

23. Quick Refernce

Syntax	  | Purpose
?.	      | Safely access properties
??	      | Default for null / undefined
? :	      | Short if...else
&&	      | Render when condition is true
`	

# Interview Questions

Q1. What is optional chaining?
     
     Optional chaining ?. safely accesses a property without throwing an error when an intermediate value is null or undefined.

         user?.profile?.name

Q2. What does ?? do?
     
     It provides a fallback when the left-hand value is null or undefined.

         const name = user.name ?? "Guest";

Q3. Difference between || and ?? ?
     
     || treats all falsy values as a reason to use the fallback.
     
     ?? only falls back for:

     null
     undefined

Q4. What is a ternary operator?
     
     A concise way to express if...else.
        
         condition  ? trueValue : falseValue

Q5. How is ternary used in React?
    
     For conditional rendering:
         
         {isLoggedIn ? <Dashboard /> : <Login />}

Q6. Difference between && and ternary in React?
 
     {isAdmin && <AdminPanel />}

     renders something only when the condition is true.

         {isLoggedIn ? <Dashboard /> : <Login /> }
    
     Chooses between two UI elements.

     * Memorize These
         
         Safe access
             user?.profile?.name
        
         Default value
             user?.name ?? "Guest"
         
         Two possible UI results
             {isLoggedIn ? <Dashboard /> : <Login />}

         Render only if true
             {isAdmin && <AdminPanel />}

     These four patterns will appear everywhere in React projects.


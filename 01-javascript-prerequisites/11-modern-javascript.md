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

13.

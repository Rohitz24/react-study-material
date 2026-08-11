# JavaScript Conditions
   
     Conditions allow a program to make decisions.

     For example:

      IF user is looged in -> show dashboard
      otherwise -> Show Login

      JavaScript provides several ways to create conditions.

1. if Statement
     
     The if statement runs code when a conditions is true.

     const age = 25;

     if (age >= 18) {
        console.log("You are an adult");
     }

Output: 
     You are an adult

     IF the condition is false, the code inside if does not run.

2. if...else
     
     Use else when you want to execute another block if the condition is false.

     const age = 16;

     if (age >= 18) {
        console.log("Adult");
     } else {
        console.log("Minor");
     }

Output:
     
     Minor

     Structure:

     If condition is true
             ↓
        execute if
             ↓
        otherwise
             ↓
        execute else

3. else if
     
     Use else if when you have multiple conditions.

     const marks = 75;

     if (marks >= 90) {
        console.log("Grade A+");
     } else if (marks >= 75){
     console.log("Grade A");
     } else if (marks >= 60"){
     console.log("Grade B");
     } else {
        console.log("Fail");
     }

Output:

     Grade A

     JavaScript checks the conditions from top to bottom.

4. Multiple Conditions

     You can combine conditions using logical operators.

     const age = 25;
     const hasLicense = true;

     if (age >=18 && hasLicense) {
        console.log("You can drive");
     }

     Both conditions must be true because we used &&.

5. Nested if 
    
     An if statement can exist inside another if.

     const isLoggedIn = true;
     const isAdmin  = true;

     if (isLoggedIn) {

        if (isAdmin){
            console.log("Admin Dashboard");
        }
     }

     However, deeply nested conditions can make code difficult to read.

     Prefer simple logic when possible.
    
6. Switch

     Switch is useful when comparing one value against multiple possible values.

     const day = "Monday";

     switch (day) {
        case "Monday":
         console.log("start of the week");
         break;

        case "Friday":
         console.log("Almost weekend");
         break;

        case "Sunday":
         console.log("Weekend");
         break:

        default:
         console.log("Normal day");        
     }

Output:
   
     Sart of the week

     WHY break?

     break stops the switch.

     Without it, JavaScript may continue executing following cases.

7. default
    
     default runs when none of the cases match.

     const role = "guest";

        switch (role) {
            case "admin":
             console.log("Admin");
             break;

            case "user":
             console.log("User");
             breaK;

             default:
              console.log("Guest");
        }

Output:
    
     Guest

8. Truthy and Falsy Values
     
     Javascript converts values to true or false when used in conditions.

     * Falsy Values

     Thes values behave like false:

     false 
     0
     -0
     ""
     null
     undefined
     NaN

Example"

     const username = "";

     if (username) {
        console.log("Username exists");
     } else {
        console.log("Username is empty");
     }

Output:
    
     Username is empty

9. Truthy Values
    
     Almost everything else is truthy.

Examples:
     
     "Rohit"
     25
     []
     {}
     true

Example:

     const username = "Rohit";

     if (username) {
        console.log("Username exists");
     }

Output:
     
     Username exists

10. Consitional Operator
    
     You can use the ternary operator for simple conditions.

     const age = 20;

     const result = age >= 18
      ? "Adult"
      : "Minor";

      console.log(result);

Output:
     
     Adult

     For simple conditions, ternary is convenient.
     For complex logic, use.

11. Conditions in React
    
     Conditions are extermely important in React beacause the UI often depends on application state.

For example:
     
     function App () {
        const isLoggedIn = true;

        if (isLoggedIn) {
            return <h1>Welcome!</h1>;
        }

        return <h1>Please Login</h1>;
     }

     React displays different UI depending on the condition.

12. Condtional Rendering with &&

     A very commmon React pattern:

     function App() {
        const isAdmin = true;

        return (
            <div>
              <h1>Dashboard</h1>

              {isAdmin && <button>Admin Panel</button>}
            </div>
        );
     }

     if:

     is Admin === true
     the button appears.

     isAdmin ===false
     the button does not appear.

13. Conditional Rendering with Ternary
    
     Another common React pattern:

     function App() {
        const isLoggedIn = true;

        return (
            <div>
              {isLoggedIn ? (
                <h1>Dashboard</h1>
              ) : (
                <h1>Login</h1>
              )}
            </div>
        );
     }

     This is one of the most important React patterns to understand.

14. Loading Example
    
     Conditions are also used for API loading states.

     function App() {
        const isLoading = true;

        return (
            <div>
              {isLoading ? (
                <p>Loading..</p>
              ) : (
                <p>Data loaded!</p>
              )}
            </div>
        );
     }

     This pattern will become very important when we learn APIs.

15. Authentication Example

     A realistic React example:
      
      function App() {
        const user = {
            isLoggedIn: true,
            isAdmin: false
        };

        if (!user.isLoggedIn) {
            return <h1>Please Login</h1>;
        }

        return (
            <div>
              <h1> Welcome to Dashboard</h1>

              {user.isAdmin && (
                <button>Admin Panel</button>
              )}
            </div>
        );
      }
    
    Logic:

    Not logged in 
         ↓ 
    Login page Logged in 
         ↓ 
    Dashboard Admin 
         ↓ 
    Admin Panel

16. When Should You Use What?
     
     Situation                    Recommended

     One simple condition          if
     Two alternatives              if...else
     Multiple conditions           else if
     Multiple fixes values         switch
     Simple UI condition           Ternary
     Show/hide one React element   &&
     Fallback for missing data     ??

# Interview Questions

Q1. What is conditional rendering in React?
     ~ Conditional rendering means displaying different UI based on a condition.
Example: 
     {isLoggedIn ? <Dashboard /> : <Login />}

Q2. What are truthy and falsy values?
     ~ Truthy values behave like true in conditions, while falsy values behave like false.

     common falsy values include:

     false
     0
     ""
     null
     undefined
     NaN

Q3. When should you use switch instead of if...else?
     ~ switch is used when comparing one values against multiple fixed values.

Q4. What is the difference between && and a ternary in React?
     ~ && is useful when you want to show something only when a condition is true.

     {isAdmin && <AdminPanel />}

     A ternary is uesful when you need two alternatives.

     {isLoggedIn ? <Dashboard /> : <Login />}

Q5. Can you use if directly inside JSX?
     ~ NO

     This is invalid:

     return (
        <div>
         if (isLoggedIn) {
            ...
         }
        </div>
     );

     Instead, use:
     
     * if before the return
     * ternary ?:
     * &&
     * other conditional expressions
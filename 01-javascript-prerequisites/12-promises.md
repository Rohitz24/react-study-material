# JavaScript Promises
    
     Promises are important because React applications frequently communicate with APIs.

1. What is Promise?
     
     A Promise represents a value thatt will be available now, later, or never.

     For example, imagine asking a server for user data:
     
        React
          ↓
        Request API
          ↓
        Waiting...
          ↓
        Server responds
          ↓
        User data
    
     While waiting, the promise is pending.

     A Promise has 3 states:
       
           Pending
              ↓
        ┌───────────┐
        ↓           ↓
     Fulfilled   Rejected
     (success)   (error)

2. Creating a Promise

      const promise  = new Promise((resolve, reject) => {
        // operation
      });

     There are two important functions:

     resolve() -> success
     reject()  -> failure

Example:
      
      const promise = new Promise((resolve, reject) => {
        resolve("Success!");
      });

3. Using .then()

     To recive the successful result:

     promise.then((result) => {
        console.log(result);
     });

Output:
      
      Success!
    
     So:
         
         resolve("Success!");
    
     Passes the value to:

         .then((result) => {})

4. Handling Errors with .catch()
     
     const promise = new Promise((resolve, reject) => {
        reject("Something went wrong");
     });

     promise
       .then((result) => {
        console.log(result);
       })
       .catch((error) => {
        console.log(error);
       });
    
Output:
      
      Something went wrong

5. .finally()
     
     fianlly() runs whether the promise succeeds or fails.

     promise 
        .then((result) => {
            console.log(result);
        })
        .catch((error) => {
            console.log(error);
        })
        .finally(() => {
            console.log("Finished");
        });

     Useful for things like:

       Loading...
          ↓
       API request
          ↓
       Success/Error
          ↓
       Stop loading

6. Simple Real-World Example
     
     Imagine a login request:
      
      const login = new Promise((resolve, reject) => {
        const success = true;

        if(success) {
            resolve("Login successful");
        } else {
            reject("Invalid credential");
        }
      });

     Use it:

     login
        .then((message) => {
            console.log(message);
        })
        .catch((error) => {
            consol.log(error);
        });

Output:
      
      Login successful

7. Promise with a Delay

     JavaScript can simulate an API request:

     const getData = new Promise((resolve) => {
        setTimeout(() => {
            resolve("Data received");
        }, 2000);
     });

     Then: 

     getData.then((data) => {
        console.log(data);
     });

     The message appears after approximately 2 seconds.

8. Why does this matter?
     
     When an API request takes time, JavaScript shouldn't freeze the entire applications while waiting.

     For exmple:
     
     Start request
         ↓
     Application continues
         ↓
     Server responds
         ↓
     Promise resolves
         ↓
      Process data

     This is part of asynchronous JavaScript.

9. Promise Chaining
      
      You can chain multiple .then() calls.

      Promise.resolve(10)
        .then((number) => {
            return number * 2;
        })
        .then((number) => {
            return number + 5;
        })
        .then((result) => {
            console.log(result);
        });

Output:
     
     25

     Flow:
     10
     ↓ ×2
     20
     ↓ +5
     25

10. Important Rule: Return the Value
     
     This: 
        
        .then((number) => {
            return number * 2;
        })

     passes the result to the next .then().
     
     So:

     .then((number) => {
        return number * 2;
     })
     .then((result) => {
        console.log(result);
     });

     The second .then() recives the returned value.

11. Promise Error Handling
    
     Errors can be handled using .catch():

     Promise.reject("API failed")
       .then((data) => {
        console.log(data);
       })
       .catch((error) => {
        cosnsole.log("Erro:", error);
       });

Output:
      
      Error: API failed

12. Promise.resolve()
     
     You can create an already-successful Promise:

     const promise = Promise.resolve("Hello");

     promise.then((value) => {
        console.log(value);
     })

13. Promise.reject()
     
     You can create an already-failed Promise:

     const promise = Promise.reject("Failed");

     promise.catch((error) => {
        console.log(error);
     });

14. Multiple Promises
     
     Suppose you have:

     const p1 = promise.resolve("User");
     const p2 = promise.resolve("Posts");
     const p3 = promise.resolve("Comments");

     You can write for all of them:

     Promise.all([p1, p2, p3])
        .then((result) => {
            console.log(results);
        });
    
     Result:
      
      ["User", "Posts", "Comments"]

15. Promise.all()
     
     This is useful when multiple independent API requests need to finish.

Example: 
     
     Promise.all([
        fetchUsers(),
        fetchProducts(),
        fetchPosts()
     ])
     .then(([users, products, posts]) => {
        console.log(users);
        console.log(products);
        console.log(posts;)
     });

     Conceptually:

     fetchUsers()     ──┐
     fetchProducts()  ──┼──→ Promise.all() → results
     fetchPosts()     ──┘

     If one Promise rejects, Promise.all() rejects.

16. Promise.allSettled()
    
     Sometimes you want results from all opertions, even if one fails.

     Promise.allSettled([
        Promise.resolve("Users"),
        Promise.reject("Posts failed"),
        Promise.resolve("Products"),
     ])
     .then((results) => {
        console.log(results);
     });

     You get the status of each Promise.

     Useful when individual failures shouldn't stop everything.

17. Promise.race()
    
     Promise.race() returns whichever Promise finishes first.

     const p1 = new Promise(resolve => {
        setTimeout(() => resolve("First"), 1000);
     });

     const p2 = new Promise(resolve => {
        setTimeout(() => resolve("Second"), 2000);
     });

     Promise.race([p1, p2])
       .then(result => {
        console.log(result);
       });

Output:
     
     First

     because it finished first.
    
18. promise Methods to Remember

| Method                 | Purpose                   |
| ---------------------- | ------------------------- |
| `.then()`              | Handle success            |
| `.catch()`             | Handle error              |
| `.finally()`           | Always execute            |
| `Promise.all()`        | Wait for all              |
| `Promise.allSettled()` | Get every result          |
| `Promise.race()`       | First settled Promise     |
| `Promise.resolve()`    | Create successful Promise |
| `Promise.reject()`     | Create failed Promise     |

19. Promise in React
     
     useEffect(() => {
        fetchUsers()
         .then((data) => {
            setUsers(data);
         })
         .catch((error) => {
            console.log(error);
         });
     }, []);

     This flow is:
     
     Component loads
          ↓
     API request
          ↓
     Promise pending
          ↓
     API responds
          ↓
      .then()
          ↓
     setUsers()
          ↓
     React re-renders

20. Promise vs Normal Function

     Normal synchronous code:

     const result = calculate();
     console.log(result);

     The result is immediately available.

     Asynchronous code:

     const result: fetchdata();

     The data isn't immediately available.

     Instead:

      fetchData()
        .then((data) => {
            console.log(data);
        });
    
     The promises represents the future result.

21. Promise vs async/await
    
     You can write;

     fetchData()
      .then((data) => {
        console.log(data);
      })
      .catch((error) => {
        console.log(error);
      });

     Later, you'll learn:

     async function loadData() {
        try {
            const data = await fetchData();
            console.log(data);
        } catch (error) {
            console.log(error);
        }
     }

     Both work with Promises.

     async/wait generally makes asynchornous code easier to read.

* Important Mental Model
    
     Think of a Promise like ordering food:

        You place order
              ↓
           Pending
              ↓
         ┌───────────┐
         ↓           ↓
     Food ready   Order failed
        ↓           ↓
     resolve()   reject()

     Then: 
         
         .then()
    
     means:

         "What should i do if it succeeds?"
    
     And:
        
         .catch()
     
     means: 
         
         "What should i do if it fails?"

# Interview Questions

Q1. What is Promise?
     
     A promise is an object representing the eventual completion or failure of an asynchronous operation.

Q2. What are the three Promise states?
     
     Pending
     Fulfilled
     Rejected

Q3. What does .then() do?
    
     Handles the successful result of a promise.

Q4. What does .catch() do?

     Handles a rejected Promise or error.

Q5. What does .finally() do?

     Runs after the Promise settles, regardless of success or failure.

Q6. What is Promise.all() ?
    
     It waits for multiple Promises to fulfill and returns thier results together. If one rejects, the combined Promise rejects.

Q7.  Why are Promises important in React?
    
     React applications frequently perform asynchronous opertions such as API requests, database requests, authentications, and file operations. 

     * Remember this pattern:
     fetchData()
      .then((data) => {
     console.log(data);
     })
      .catch((error) => {
     console.log(error);
     })
      .finally(() => {
       console.log("Finished");
     });
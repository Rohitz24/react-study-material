# async/await

1. What is async/await?
    
     async/await is a simpler way to work with Promises.

     Instead of:
                
         fetchData()
            .then((data) => {
                console.log(data);
            })
            .catch((error) => {
                console.log(error);
            });
    
     you can write:
         
         async function loadData() {
            try {
                const data = await fetchData();
                console.log(data);
            } catch (error) {
                console.log(error);
            }
         }

         It makes asynchronous code easier to read.

2. The async Keyword
      
     When you put async before a function:

     async function greet() {
        return "Hello";
     }

     the function alwayd returns a Promise.

     So:

     const result = greet();

     console.log(result);

     returns a Promise rather than directly returning "Hello".

3. Using .then() with as Async Function
     
     Because async functions return Promises:

     async function greet() {
        return "Hello";
     }

     greet().then((message) => {
        console.log(message);
     });

Output:
       
     Hello

4. The await Keyword
     
     await waits for a Promise to settle and gives you its fulfilled value.

Example:
       
       function getData() {
        return Promise.resolve("Data received");
       }

       async function loadData() {
        const result = await getData();

        console.log(result);
       }

       loadData();

Output:
      
      Data received

     Think:
        
        getData()
           ↓
        Promise
           ↓
         await
           ↓
     "Data received"

5. await Only Works in Async Functions

     Normally:
          
         functions loadData() {
            const data = await getDat();
         }

     This causes an error:

     Use:
        
         async function loadData() {
            const data = await getData();
         }

     Modern JavaScript also supports top-level await in certain ES modules.

6. async/await vs .then()

     Promise style:
          
         getData()
            .then((data) => {
                console.log(data);
            });
    
     Async/await style:

         async function loadData() {
            const data = await getData();

            console.log(data);
         }

         Both use the same underlying Promise.

7. Handling Errors with try/catch
      
     This is extremely important.

         async function loadData() {
            try {
                const data = await getData();

                console.log(data);
            } catch (error) {
                console.log(error);
            }
         }
    
     Think:

     try
      ↓
     Run async operation
      ↓
     Success → continue
      ↓
     Failure → catch

8. Example with a Rejected Promise
     
     function gerData() {
        return Promise.rejecr("Server error");
     }

     async function loadData() {
        try{
            const data = await getData();

            console.log(data);
        } catch (error) {
            console.log("Error:", error);
        }
     }

     loadData();

Output:
     
     Error: Server error

9. finally with async/await
     
     You can also use finally:

         async function loadData() {
            try{
                const data = await getData();

                console.log(data);
            } catch (error) {
                console.log(error);
            } finally {
                console.log("Request finished");
            }
         }

     finally runs whether the request succeeds or fails.

10. Waiting for a Delay
     
     Create a reusable delay function:

         function delay(ms) {
            return new Promise((resolve) => {
                setTimeout(resolve, ms);
            });
         }
     
     Now:
         
         async function test() {
            console.log("Start");

            await delay(2000);

            console.log("End");
         }

         test();

Output:
      
     Start

     After 2 seconds:

         End

11. Multiple awaits
     
     You can perform multiple asynchronous operations:

     async  function loadData() {
        const user = await getUser();

        const posts = await getPosts();

        console.log(user);
        console.log(posts);
     }

     The secong operation starts after the first one finishes.

     Conceptually:

     getUser()
        ↓
      await
        ↓
     getPosts()
        ↓
      await
        ↓
     result

12. Sequential vs Parallel Operations
     
     Suppos you need:

     User data
     Posts
     Products

     If they don't depend on each other, doing this:

     const user  = await getUser();
     const posts  = await getPosts();
     consts products = await getProducts();

     can unnecessarily wait for each request.

     Instead, use Promise.all():
      
         const [user, posts, products] = await Promise.all([
            getUser(),
            getPosts(),
            getProducts()
         ]);

     Now they can run concurrently.

     This is an important performance pattern.

13. Example:
     
     function getUser() {
        return new Promise((resolve) => {
            setTimeout(() => {
                resolve("User");
            }, 2000);
        });
     }

     function gerPosts() {
        return new Promise((resolve) => {
            setTimeout(() => {
                resolve("Posts");
            }, 2000);
        });
     }

     Sequential"
      
         async function load() {
            const user = await getUser();
            const posts = await gerPosts();

            console.log(user);
            console.log(posts);
         }

     Approximately:
         
         2 sec + 2 sec = 4 sec

     Parallel:
         
         async function load() {
            const [user, posts] = await Promise.all([
                gerUser(),
                gerPosts()
            ]);

            console.log(user);
            console.log(posts);
         }

     Approximately:
         
         max(2 sec, 2 sec) = 2 sec
        
14. await Does Not Freeze the Entire Application
     
     A common beginner misconception is:
         
         "await freezes JavaScript."
    
     It doesn't block the entire browser/application while waiting for an asynchronous operation.

For example:
     
     async function load(){
        const data = await fetchData();

        console.log(data);
     }

     The asynchronous operation can continue while the rest of the environment remains responsive.

15. Async Function Return Value
     
     Consider:
         
         async function gerUser() {
            return {
                name: "Rohit"
            };
         }
    
     Because it's async, it returns a Promise/

     So:
          
         getUser().then((user) => {
            console.log(user.name);
         });
    
Output:
     
     Rohit

     Or:

         async function main() {
            const user = await getUser();

            console.log(user.name);
         }

         main();

16. Returning Data from an Async Function
     
     This pattern is very important for API functions.

     async function getUser() {
        const user = {
            id: 1,
            name: "Rohit"
        };

        return user;
     }

     Then:
          
          async function main() {
            const user = await getUser();

            console.log(user);
          }

17. Real API Pattern
     
     async function getUser() {
        try {
            const response = await fetch("API_URL");
            
            const data  = await respons.json();

            return data;
        } catch (error) {
            console.log(error);
        }
     }

     This is very common pattern in frontend development.

18. response.json() is Also Asynchronous.
     
     This is important.

     When you write:
         
         const response  = await fetch(url);

     you receive a Response object.

     Then:
         
         const data = await response.json();
        
     converts the respons body into JavaScript data.

     So there are two asynchronous operations:
     
     fetch()
       ↓
     Response
       ↓ 
     response.json()
       ↓
     JavaScript data

19. Loading State in React
     
     When making API requests, you'll often need:

     Loading
     Success
     Error

     Conceptually:

         async function loadUsers() {
            try {
                // loading starts

                const users = await getUsers();

                // success
            } catch (error) {
                // error
            } finally {
                // loading ends
            }
         }

     Later, React state will control the UI:
         
     Loading... ⏳
        ↓
     Users displayed 👥

     or

     Error message ❌

20. Common Mistake
     
     Don't do:

         const data  = await fetch(url);

     Outside an appropriate async context.

     Instead:
         
         async function loadData() {
            const data  = await fetch(url);
         }

21. Common Mistake - Forgetting await
     
     Suppose:
        
         async function getUser() {
            return {
                name: "Rohit"
            };
         }

     This:

         const user = getUser();

         console.log(user.name);
    
     doesn't work as expected becauser user is a Promise.

     Use:
         
         const user = await getUser();
    
     inside an async function.

22. Common mistake - Forgetting try/catch
    
     for operations that can fail:
        
         async function loadData() {
            const data = await getData();
         }
     
     It's ususally better to handle errors:

     async function loadData() {
        try {
            const data = await getData();
        } catch (error) {
            console.log(error);
        }
     }

23. React Example

     Later, you'll see something like:

      useEffect(() => {
        async function loadUser() {
            try{
                const response = await fetch("/api/users");
                const data = await response.json();

                serUsers(data);
            } catch (error) {
                console.error(error);
            }
        }

        loadUsers();
      }, ([]));

     Understand this flow:
     Component
        ↓
     API request
        ↓
     await fetch()
        ↓
     response
        ↓
     await response.json()
        ↓
     data
       ↓
     setUsers()
       ↓
     UI updates

24. async/await cheat sheet
     
     Basic:
          
          async function loadData() {
            const data = await getData();
          }

     Error handling
         
         async function loadData() {
            try {
                const data = await getData();
            } catch (error) {
                console.log(error);
            }
         }
     
     Finally:
         
         async function loadData() {
            try {
                await getData();
            } catch (error) {
                console.log(error);
            } finally {
                console.log("Finished");
            }
         }

     Multiple requests:
         
         const [users, posts] = await Promise.all([
            gerUsers(),
            getPosts()
         ]);

# Interview Questions

Q1. What is async/await?
     
     It's syntax built on top of Promises that makes asynchronous code easier to read and write.

Q2. What does async do ?
     
     An async function always returns a Promise.

Q3. What does await do?
    
     It waits for a Promise's result inside an appropriate async context.

Q4. How do you handle errors?

     Using try/catch:

         try {
            const data = await getData();
         } catch (error) {
            console.log(error);
         }

Q5. Can you use await without async?
     
     Normally, no. await is used inside an async function, with top level await being supported in certain ES modules.

Q6. How do you run multiple independent async operations efficiently?

     Use:
         
         const [a, b] = await Promise.all([
            operationA(),
            operationB()
         ]);

Q7. Is async/await different from Promises?
     
     async/await doesn't replace Promises. It provides cleaner syntax for consuming Promise based operations.

* The pattern You Must Remember

     async function loadData() {
       try {
         const response = await fetch(url);

         const data = await response.json();

         console.log(data);
        } catch (error) {
         console.error(error);
       } 
     }

     Understand the flow:
    
     async
       ↓
     await
       ↓
     Promise result
       ↓
     try/catch
       ↓
      data
# Fetch API

1.  What is Fetch API?
      
      fetch() is a built-in JavaScript function used to communicate with servers/APIs.

     For example:
      
      React Application
      ↓
      fetch()
      ↓
      API Server
      ↓
      Response
      ↓
      JSON Data
      ↓
      React UI

     You'll use this constantly as a frontend developer.

2. Basic GET Request
     
     The simple request:

         const response = await fetch(
            "https://jsonplaceholder.typicode.com/users"
         );

         const data = await response.json();

         console.log(data);

     This is requests user data from an API.

3. Using async/await
    
     Usually you'll put it inside a function:

         async function getUsers() {
            const response = await fetch(
                "https://jsonplaceholder.typicode.com/users"
            );

            const data = await response.json();

            console.log(data);
         }

         getUsers();

4. What Does fetch() Return?
     
     This: 
         
         const response = await fetch(url);
    
     does not directly give you the JSON data.

     It gives you a Response object.

     Then:
         
         const data = await response.json();
    
     converts the response body into JavaScript data.

     So:
        
        fetch()
           ↓
        Response object
           ↓
        response.json()
           ↓
        JavaScript object/array

5. Understanding JSON
      
      APIs commonly send data as JSON.

Example:
      
     </> JSON

      {
        "id": 1,
        "name": "Rohit",
        "role": "Developer"
      }

      JavaScript can work with it after parsing:

      const data = await response.json();

      console.log(data.name);

Output:
      
     Rohit

6. Check Response Status
     
     Don't assume every request succeeds.

     Use:
         
         if (!response.ok) {
            throw new Error("Request failed");
         }

     Complete example:

     async function getUsers() {
        const response = await fetch(
            "https://jsonplaceholder.typicode.com/users"
        );

        if (!response.ok) {
            throw new Error("Request failed");
        }

        const data = await response.json();

        return data;
     }

7. try/catch with Fetch
     
     Recommend pattern:

     async function getUsers() {
        try{
            const response = await fetch(
                "https://jsonplaceholder.typicode.com/users"
            );

            if (!response.ok) {
                throw new Error("Failed to fetch users");
            }

            const data = await response.json();

            console.log(data);
        } catch (error) {
            console.error(error);
        }
     }

     getUsers();

8. Important: fetch() and HTTP Errors

     A common beginner mistake is thinking:
          
          if the server returns 404 or 500, fetch() automatically goes to catch.

     Usually, it doesn't.

     For example:

     404 Not Found
     500 Server Error

     can still produce a Response.

     That's why you check:

         if (!response.ok) {
            throw new Error("Request failed");
         } 

9. response.ok

     This property tells you whether the HTTP response was successful.

Example:
        
         if (response.ok) {
            console.log("Success");
         }
    
     For typical successful responses:

     200
     201
     204

     response.ok is true.

     For common errors:
     
     400
     401
     403
     404
     405

     it's false.

10. HTTP Status Codes You Should Know

| Status | Meaning      |
| ------ | ------------ |
| `200`  | OK           |
| `201`  | Created      |
| `204`  | No Content   |
| `400`  | Bad Request  |
| `401`  | Unauthorized |
| `403`  | Forbidden    |
| `404`  | Not Found    |
| `500`  | Server Error |

11. GET Request
     
     GET means:
         
         "Give me data."

Example:
      
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/users"
      );

     This is a GET request because GET is the default method.

     You can explicity write:

         const response = await fetch(
            "https://jsonplaceholder.typicode.com/users",
            {
                method: "GET"
            }
         );

     Usually you don't need to specify GET.

12. Getting One User
     
     You can request a specific resource:

         const response = await fetch(
            "https://jsonplaceholder.typicode.com/users"
         );

         const user = await response.json();

         console.log(user);

     You should receive one user object.

13. API URL Structure
      
     For example:
      
      https://jsonplaceholder.typicode.com/users/1

     can be thought of as:

     https://
      ↓
     domain
      ↓
     /users
      ↓
     resource
      ↓
     /1
      ↓
     specific user

14. Query Parameters
     
     Sometimes you need to send parameters in the URL.

Example:
        
        /users?name=Rohit

     You can use:
          
          const response = await fetch(
            "https://example.com/users?name=Rohit"
          );
     
     Multiple parameters:

          /users?name=Rohit&role=developer

15. URLSearchParams
     
     Instead of manually constructing a URL:

      const params = new URLSearchParams({
        name: "Rohit",
        role: "developer"
      });

      const url = `https://example.com/users?$(params)`;

     This becomes:

     /users?name=Rohit&role=developer

     This is useful when query parameters are dynamic.

16. POST Request 
      
      GET retrieves data.
    
     POST usually sends data to the server.
    
Example:
      
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/posts",
        {
            method: "POST",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify({
                title: "My Post",
                body: "Hello World",
                userId: 1
            })
        }
      );

17. Why JSON.stingfy()?
    
    JavaScript object:

     {
        title: "My Post",
        body: "Hello World"
     }

     needs to be converted to JSON text before sending in the request body.

     Use:

      JSON.stringfy({
        title: "My Post",
        body: "Hello World"
      });

      Conceptually:

      JavaScript Object
       ↓
      JSON.stringify()
       ↓ 
      JSON
       ↓
      Server

18. Complete POST Example:
     
     asynce function createPost() {
        try {
            const response = await fetch(
                "https://jsonplaceholder.typicode.com/posts",
                {
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    body: JSON.stringfy({
                        title: "React Learning",
                        body: "Learning Fetch API",
                        userId: 1
                    })
                }
            );

            if (!response.ok) {
                throw new Error("Failed to create post");
            }

            const data = await response.json();

            console.log(data);
        } catch (error) {
            console.error(error);
        }
     }

     createPost();

19. PUT Request
     
     PUT is generally used to replace/update a resource.

Example:
      
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/posts",
        {
            method: "PUT",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify({
                id:1,
                title: "Updated title",
                body: "Updated content",
                userId: 1
            })
        }
      );

20. PATCH Request
     
     PATCH is generally used to partially update a resource.

Example:
      
       const response = await fetch(
        "https://jsonplaceholder.typicode.com/posts/1",
        {
            method: "PATCH",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringfy({
                title: "New title"
            })
        }
       );

     Only the title is being updated.

21. DELETE Request
     

     DELETE is used to delete a resource.
        
        constt response = await fetch(
            "https://jsonplaceholder.typicode.com/posts/1",
            {
                method: "DELETE"
            }
        );

        if (response.ok) {
            console.log("Deleted successfully");
        }

22. HTTP Methods

GET
 ↓
Read data

POST
 ↓
Create data

PUT
 ↓
Replace/update data

PATCH
 ↓
Partially update data

DELETE
 ↓
Delete data

These are extremely important for frontend interviews.

23. Headers
     
     Headers provide additional information about the request.

Example:
     
     headers: {
        "Content-Type": "application/json"
     }

     This tells the server:

        "The data i'm sending is JSON."

     Another common header is authorization:

      headers: {
        "Authorization": `Bearer $(token)`
      }

24. Request Body
     
     For POST/PATCH/PUT:

      body: JSON.stringfy({
        name: "Rohit",
        role: "Developer"
      })

       Think:

       headers -> information about request
       body -> actual data being sent

25. Fetch Flow
     
fetch()
   ↓
Response
   ↓
Check response.ok
   ↓
response.json()
   ↓
Data
   ↓
Use data

For a POST:

JavaScript object
       ↓
JSON.stringify()
       ↓
body
       ↓
fetch()
       ↓
Server

26. Fetch + React
     
     This is where everything you've learned starts connecting.

     A React component might eventually do:

      useEffect(() => {
        async function loadUsers() {
            try {
                const response = await fetch (
                    "https://jsonplaceholder.typicode.com/users"
                );

                if(!response.ok) {
                    throw new Error("Failed to fetch users");
                }

                const data = await response.json();

                setUsers(data);
            } catch (error) {
                console.error(error);
            }
        }

        loadUsers();
      }, []);

     The important part is:
     API
      ↓
     fetch
      ↓
     JSON
      ↓
     setUsers
      ↓
     React UI

27. Loading, Success & Error
     
     A real application usually needs three states:

     Loading
       ↓
     Success
      OR
     Error

     For example:
     ⏳ Loading users...

        ↓

      Rohit
      Amit
      Rahul

      Or: 
         
         Failed to load users

     Later, React state wil manage this.

28. A Better API Function
     
     Instead of putting everything inside the component, create a function:

       
       async function getUsers() {
        const response = await fetch(
           "https://jsonplaceholder.typicode.com/users"
        );

        if (!response.ok) {
           throw new Error("Failed to fetch users");
        }

       return response.json();
       }

     Then:

       async function main() {
        try {
            const users = await getUsers();

            console.log(users);
        } catch (error) {
            console.error(error);
        }
       }

       main();

     This is sepration becomes very useful in real projects.

29. API Service Pattern

     In larger projects you might have:

src/
├── components/
├── pages/
├── services/
│   └── userService.js
└── App.jsx

userService.js:

     export async function getUsers() {
      const response = await fetch(
        "https://example.com/users"
       );


       if (!response.ok) {
       throw new Error("Failed to fetch users");
       }


       return response.json();
       }

     Then your React component can use it.

30. Important Security Note

     Never put secret API keys directly into frontend JavaScript if the key is supposed to be private.

     Avoid:

     const API_KEY = "my-secret-key";

     in code that gets shipped to the browser.

     Frontend code can be inspected by users.

     For sensitive credentials, use a backend/server-side layer. 

#  Interview Questions

Q1. What is Fetch API?

     A browser-provided JavaScript API used to make HTTP requests.

Q2. What does fetch() return?

     A Promise that resolves to a Response object.

Q3. How do you get JSON from a response?

     const data = await response.json();

Q4. Does fetch() automatically reject on HTTP 404?

     Generally, no. You should check:

     if (!response.ok) {
     throw new Error("Request failed"); 
     }

Q5. What is the difference between GET and POST?
    
     GET  → retrieve data
     POST → send/create data

Q6. Why use JSON.stringify()?

     To convert a JavaScript value/object into JSON text for a request body.

Q7. What are common HTTP methods?

     GET
     POST
     PUT
     PATCH
     DELETE

Q8. What is Content-Type?

     A header that tells the server what format the request body uses.

Example:

     "Content-Type": "application/json"
     
# Quick Cheat Sheet

GET:
const response = await fetch(url);
const data = await response.json();
POST
const response = await fetch(url, {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify(data)
});

Error handling:
if (!response.ok) {
  throw new Error("Request failed");
}

Complete pattern:
async function getData() {
  try {
    const response = await fetch(url);


    if (!response.ok) {
      throw new Error("Request failed");
    }


    const data = await response.json();


    return data;
  } catch (error) {
    console.error(error);
  }
}
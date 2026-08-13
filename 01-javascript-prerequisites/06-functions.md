# JavaScript Functions
   
     Functions are reusable blocks of code. They are extremely important in React because React components themeselves are functions.

1. What is a Functions?
    
     A function is a reusable block of code that performs a specific task.

     function greet() {
        console.log("Hello Rohit!");
     }

     greet();

Output: 
     
     Hello Rohit!

     The function is created with:

     function greet() {
        ...
     }

     and called using:
     
     greet();

2. Function Parameters
     
     Parameters allow us to pass data into a function.

     function greet(name) {
        console.log("Hello $ {name}`);
    }

    greey("Rohit");

Output:
      
      Hello Rohit

      Here:

      name -> parameter
      "Rohit" -> argument

3. Multiple Parameterss
     
     function add(a,b) {
        console.log(a + b);
     }

     add(10, 20);

Output:
     
     30

4. return
     
     A function can return a value

     function add(a, b) {
        return a + b;
     }

     const result = add(10, 20);

     console.log(result);

Output:
     
     30

     Think of it as:

     Input
       ↓
     Function
       ↓
     Output

5. Why return is Important
    
     Compare:

     function add(a,b) {
        console.log(a + b);
     }

     with:

     function add(a, b) {
        return a + b;
     }

     The second version allows us to use the result somewhere else:

     const total = add(10,20);

     const finalPrice = total * 2;
Javascript Variables
~    Vraibles are used to store data in JavaScript.

1> let:-
     Use let when the value may change.
ex:  let age = 25;
     age = 26;
     console.log(age);

Output:
26

2> const:-
     Use const when the variable should not be reassigned.
ex:  const name: "Rohit";
     console.log(name);
     You cannot do :
     name = "John";

3> var:-
     var is the older way of declaring variables.
ex:  var city = "Nagpur";

Modern javascript genrally prefers:
let
const
instead of var.

4> Difference

Keyword         Reassign     scope        Recommended
----------------------------------------------------------------
let              yes         Bloack        ✅
----------------------------------------------------------------
const            No          Block         ✅
----------------------------------------------------------------
var              yes         Function      X Usually avoid

5> React Connection 
You will frequently use const in React:

const userName = "Rohit";
const age = 25;

Later, React's useState() will allow us to manage values that change:
const [count, setCount] = useState(0);

Interview Question
Q: What is the difference between let, const, and var?
ans:
    let and const are block-scoped modern JavaScript variables. let can be reassigned, while const cannot be reassigned. var is function-scoped and is genrally avioded in modern JavaScript. 

# Functions


### What is a function?

- Black box metaphor
    - Put stuff in, get stuff out.

- Built in functions: they’re just like the functions we write,
    - except we can run them from any folder

- We can write functions just like the built in ones (your homework problems)

- What is a .m file? .p file? .mat file?

- What is a “script” and why is it different from a function?
- Why are functions better?

- Key function topics (why we like functions)
    - Abstraction and how we use it to manage complexity
    - Encapsulation: things defined in the function only known to the function
        - embodied in the concept of function scope
    - Both of these simplify problem solving (taking a big problem and breaking it down into steps)

- Similar to a function in math
- f(x)=x^2 +4


### Defining vs. Calling


- What does `“calling”` mean? Running a predefined function with some set of inputs

- When we want to use a function, whether it is built in or one that we’ve
    - created, we “call” it (calling works the same for both
    - this is a big step for students’ understanding!)

- Show how to “call” a function

- When we want to write a new function, we need to “define” it (i.e. your homework)


### Function headers


- Valid function headers / invalid
    - Brackets around multiple outputs
    - Parentheses around input(s)
    - Inputs are comma-separated, outputs don’t have to be
    - Never put any literal values, such as numbers

    - This is always free points on their exam!!

- Examples of:
    - 1. Multiple outputs 2. Multiple inputs 3. No outputs
        - 4. No inputs

    - NEVER hardcode literal values as the input, take a second to explain what “hard- coding” is

- Doing this is equivalent to defining a function to only work for one set of inputs, which breaks our rule of abstraction

- Reminder - function file MUST be the same as function name

``` MATLAB
- function nether
- function biome(taiga)
- function [ocelot wolf] friends(tamed)
- function theEnd = ENDERDRAGON
- function [ride, wheat, wheat, carrot] = toTame(horse cow sheep pig)
- Function pickaxe = craft(diamond, sticks)
```


- `Formal` vs `Actual` parameters
    - Formal = variable names used in function definition
        - Variables in the function header
        - Define how many inputs and outputs are expected
    - Actual = variables (or literal values) used when you call a function

        ``` MATLAB
        maxVal = max(15,20)
        ```
    - 15 and 20 are actual parameters

- When a function is called, actual parameter values are assigned to the
    - formal parameter variable names in the function workspace

- This is why it doesn’t matter what the variable names are in the
    - function header, the values are assigned when the function call is made

### Variables


- What is a `variable` and why do we need variables?
    - Variable is a storage device for data
    - We need them so we can easily reference the data they hold
- Link it back to abstraction and defining functions that can work for any scenario • How do we define variables?

- `Assignment operator “=”`
- 
``` MATLAB
pig = 'Bacon, Chris P.';
```

- Talk about how to correctly (and incorrectly) use it

``` MATLAB
'Bacon, Chris P.' = pig;
```

- Make sure the variable is on the left hand side of the assignment operator

- Common Mistakes
    - 1. Not assigning output variables - “output argument and
        - maybe others not assigned during call to funcName” error
    - 2. Mis-typing a variable name - “undefined function or variable var” error
    - 3. Not in the right directory - “undefined function or variable funcName” error
    - 4. Any other common errors you can think of

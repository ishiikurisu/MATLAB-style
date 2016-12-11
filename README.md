# MATLAB Coding Style

This document suggests a MATLAB coding style. This file is directed to those
who code with me in the lab, but might serve for everyone out there.

Coding style
------------

- No whitespace at the end of the line.
- Use Unix style line breaks (LF only).
- Keep line lenghts under 80 characters.
- Use 4 spaces to indent code. Add indentation for each logic level but the function operator:
``` matlab
function a = ackermann(m, n)
% Computes the Ackermann function.
%
if m == 0
    a = n+1;
elseif and(m > 0, n == 0)
    a = ackermann(m-1, 1);
else
    a = ackermann(m-1, ackermann(m, n-1));
end
```
- For `while` loops, the counter variable must be declared just before the while keyword:
``` matlab
n = 0;
while n <= 10
    disp(n);
    n = n+10;
end
```
- If a line is not enough to write the whole statement, break it into meaningful places, 
like after an operator or separating a line for each function argument:
``` matlab
pyt = sqrt(x^2 + ...
           y^2);
set(handles.edit, ...
    'String', ...
    sprintf('This is worth %.2f$', ...
            pyt));
```
Keep LISP style indentation in this case for better legibility. Sometimes, it might be a 
good idea too to break the line before a mathematical operator, to give a more meaningful
sense to your code:
``` matlab
result = viscosity ...
       + shear ...
       - (acceleration * mass);
```
- Name variables and functions using camelCase, as it is Java after all.
- Name constants using UPPERCASE_SEPARATED_BY_UNDERSCORES.
- Add spaces after and before brackets in case they define an array or a cell.
This space is not needed when accessing data.
``` matlab
emptyCell = { };
someNumbers = [ 1 1 2 3 5 8 13 42 ];
someNumbers(5);
emptyCell{end+1} = 19;
```

General practices
-----------------

- Whenever possible, try to use MATLAB's own math functions. And try to make your own functions comply with their functions. This will make your script a lot more faster. Seriously.
- Make every function return something unless it is a procedure.

Module organization
-------------------

Regardless of language, we can define a module as a collection of code that tries to solve one problem. This problem can be broad or not, but the idea is to encapsulate this problem into small pieces so the user does not have to think about what is inside. With that in mind, there are some precautions that are considered good taste:

- A MATLAB module is a folder containing functions. So try to keep all your code into one folder. Each file must contain one function that solves one problem inside this bigger problem. If this function needs a helper function, really specific to that domain, then it can be appended to this same file; the outside scripts will not see this helper function. Unless it is desired that it appears somewhere else or it is used repeatedly, this helper should not have a script file for its own.
- Whenever possible, try to solve your problem using only one script file. Most solutions should be considered just another procedure to be included in someone else's code. This is not always the case, since some problems actually need user interfaces and the whatnot, but it can be really nice to just incorporate a single file to the codebase instead of a whole system.

One issue that I have come accross during this time working with this language is that there is considerable namespace pollution given MATLAB does not have any mechanisms to deal with it. Therefore some care is desired when work with them:

- Unless the given module is always used, do not incorporate it directly to MATLAB. Instead, for each script, run the `addpath` function with the module path. This will keep the current namespace organized. The same applies to the Java classpath.
- One thing to pay attention is that MATLAB does not add nested modules when a folder is inserted to its path. Therefore it might be a good idea to write a function to add the modules whithin for better incorporation.

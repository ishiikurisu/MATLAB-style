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
Keep LISP style indentation in this case for better legibility.
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

<!-- TODO Add practices -->

Module organization
-------------------

<!-- TODO Talk about module organization -->

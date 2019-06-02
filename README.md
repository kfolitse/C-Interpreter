# C-Interpreter
## A  C-based Interpreter for Arithmetic Expressions Language.

We build a small interpreter application for arithmetic Expression Langauge. The inputs of the application (Interpreter) 
are postfix format expressions. The application read one expression per ligne and output, for each expression, 
the prefix format expression ( Scheme syntax), the infix format expression (C syntax), the postfix expression
(Postscript syntax), and the value of the expression.

Exemple:

<p align="center">
EXPRESSION ? 33 44 + &nbsp; &nbsp; &nbsp; <==== User input <br>
Scheme: (+ 33 44) <br>
C: 33 + 44 <br>
Postscript: 33 44 add <br>
Result: 77
</p>

<p align="center">
EXPRESSION? 7 4 + 6 10 - * &nbsp; &nbsp; &nbsp;  <==== User Input <br>
Scheme:(* &nbsp; (+ 7 4) &nbsp (- 6 10)) <br>
C: (7+4)*(6-10) <br>
Postscript: 7 4 add 6 10 sub mul  <br>
Result: -44 <br>
</p>

<p align="center">  
EXPRESSION? 3 + 4  &nbsp; &nbsp; &nbsp;  <== user input <br>
ERREUR DE SYNTAXE DANS L’EXPRESSION: 3 + 4
</p>

<p align="center"> 
EXPRESSION? ^D &nbsp;&nbsp;&nbsp;       <== end of file
</p>

The sysntax of postfix expressions read by the application is defined by the following grammar:

<p align="center">
< expr > ::= < number > | < expr > < expr > < op > <br>
< op > ::= "+" | "-" | "*" | "/" <br>
< number > ::= < digit > { < digit > } <br>
< digit > ::= "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"
</p>

Spaces before and after any expressions < expr > are allowed.

Progarm specification:

- For each ligne, the programm must construct a dynamic AST(Abstract Syntax Tree) of the expression
and no limit should be put on the size of the expression. 
- The numbers could have any number of digits, and all the digits must be output in Scheme, C, and Postscript; but the 
computation of the value of the expression can be done with floating point number(type double).
- Use **malloc** function for memory allocation. The conversion to prefix, infix and postfix, as well as the computation of 
the value of the expression must be done by  walking through the AST.
- The program shall be robust in that it should detect and report any problem (wrong syntax, division by zero, or
any expectional circumstance). If a problem arises the program must output a consice error message 
including the expression that was read and the program should continue to the next expression
(ready to accept a new expression).
- Expressions can be arbitrary long and the program should not put any limit on the size of the expression a user can enter.
- It's important to avoid memory leaks and crazy pointers. 
- The infix syntax must use a minimum of parenthesis as possible.
Ex: output (1+4)*4*6, not (((1+4)*4)*6).
- The Input and output format must be respected as specified and and one must pay attention to white spaces 
the program might output.
- Only "stdio.h", "stdlib.h" and "string.h" should be used.

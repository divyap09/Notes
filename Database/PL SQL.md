It stands for Procedural Language extension of SQL.

It has both SQL statements and procedural statements. SQL statements are to access records of data, while procedural statements are used to process and control the flow of data. It contains the series of ordered steps that should flow to process the data.

Drawbacks of SQL:
<ul>
    <li>it doesn't allow looping and control statements</li>
    <li>doesn't allow code reusability (need to write insert, update and many everytime).</li>
    <li>cannot execute more than one statement at a time.</li>
</ul>
    
    
Advantages of PL/SQL:
1. supports SQL and object-oriented programming
2. better performance
3. higher productivity
4. high security and integration
5. portability (can shift from one Oracle db to another Oracle db)

PL/SQL Structure:

It is a blocked structure, programs are divided and written in logical code blocks.

Each block consists of 3 parts:
<ol>
    <li>DECLARE</li>
    <li>BEGIN</li>
    <li>EXCEPTION</li>
</ol>
<br />


Syntax Example: 
```    
DECLARE
 --declare variables, cursors, subprograms etc

BEGIN
 --perform all update, retrieval of data, apply logical statements.

EXCEPTION [optional block]
 --catches the exceptions raised during the execution in DECLARE and BEGIN blocks.
END;
/ 
```

Except these keywords, every statement should be enclosed with “;”.

It ends with “END;” command.

To display the output to the terminal,
```
dbms_output.put_line();
```

#### Declaring a variable:
```
[variable name] [datatype][size];
```

Eg. customer_id number(3);

```
[variable name] [datatype][size]:= [value]; // instead of := we can use “default”.
```

Eg. customer_id number(3) := 101;

cost number default 1000;


#### To declare a variable constant,
```
[variable name] constant [datatype][size] := [value];
```

If we try to change the value in the BEGIN block, it raises an error.

Comment Section:
<ul>
	<li>single line (use — i.e two dashes)</li>
	<li>multi-line (use /* code */)</li>
</ul>
    
    

#### Scope of variables:

The outer/main block variables can be used in the inner block, while inner block variables are not accessible for the outer block.

### Conditional Statements:

1. Simple IF Syntax:
```
IF [condition] THEN
   statement/code
END IF;
```

2. IF- ELSE Syntax:
```
IF [condition] THEN
  statement/code
ELSE
  statement/code
END IF;
```

3. IF-ELSIF-ELSE Syntax:
```
IF [condition] THEN
   statement
ELSIF [condition] THEN
   statement
ELSIF [condition] THEN
   statement
ELSE
   statement
END IF;
```

4. CASE Syntax:
```
CASE
WHEN [condition] THEN 
    statement
WHEN [condition] THEN
    statement
WHEN [condition] THEN
    statement
ELSE
    statement
END CASE;
```

### Looping Statements:

1. WHILE loop syntax:
```
WHILE [condition]
LOOP
  statements
  increment/decrement
END LOOP;
```

2. FOR loop syntax:
```
FOR [counter variable] IN [REVERSE] [from]..[to (inclusive)]
LOOP
  statements
END LOOP;
```

### Fetching data from Database:

We use,
```
SELECT [database variables] INTO [local variables] FROM [table name] WHERE [conditions];
```

For every database variable there must be a type-compatible variable declared in the DECLARE block. And the number of database variables should be equal to the declared variables.

%type:

When we don't know the type of database variables, we use,
```
[variable] [tablename].[column name]%type;
```

### Insert data using PL/SQL:

```
INSERT INTO [tablename](column names) VALUES (local variables);
```


These local variables should have values assigned to them or any default values, else it shows error.


### Anonymous block:

Blocks which don't have any name.

Unlike anonymous block, we can have blocks with names like procedures, function etc.


### Procedures:

It accepts values, process the data and return the value if required.

```
CREATE [OR REPLACE] PROCEDURE procedure_name(parameter MODE datatype[default expression],.. upto n)
AS
[variable datatype,.. upto n]
BEGIN
   statements
EXCEPTION
   exceptions
END procedure_name;
/
```

MODE is usually IN (read only), OUT (write only) and IN OUT (read or write).

<ol>
   <li> IN: caller supplies the value and we can't change it in the program.</li>
   <li> OUT: procedure sets the value and the calling program can read the value.</li>
   <li>IN OUT: the variable which can be read and update, and available to the calling program.</li>
</ol>
   
   
    
Calling a procedure:
```
procedure_name(parameters list);
```

Functions:

very similar to procedures but a function returns a value to the environment in which it is called.

Syntax:
```
CREATE [OR REPLACE] FUNCTION function_name(parameter MODE datatype[default expression],.. upto n)
RETURN datatype
AS
[variable datatype,.. upto n]
BEGIN
   statements

   RETURN expression;
EXCEPTION
   exceptions
END function_name;
/
```

Two ways of running a function:
```
select function_name(parameter list) from dual;
value := function_name(parameter list);
```

Exceptions:

an error condition during a execution of a program.

we catch such errors in the EXCEPTION block.

Two types of exceptions:
<ol>
	<li>system-defined</li>
	<li>user-defined</li>
</ol>
    

Syntax:
```
DECLARE
BEGIN
EXCEPTION
    WHEN exception THEN
       statements;
    WHEN OTHERS THEN
       statements;
END;
```

System defined examples:

    no_data_found (SQL code: 100)
    too_many_rows (SQL code:-1422)

User-defined exceptions:

- the exception must be declared and raised explicitly using EITHER or RAISE.

Syntax:
```
DECLARE
 other variables
 exception_variable EXCEPTION;
BEGIN
 IF condition THEN
  RAISE exception_variable;
 END IF;
 statements
EXCEPTION
 WHEN exception_variable THEN
  statements
END;
/
```


Packages:

It is a schema object that groups the similar type of PL/SQL types, items and sub programs like procedures and functions.

They can hold exceptions, variables, cursors, type declarations etc.

It has two parts:
<ol>
	<li>Specification</li>
	<li>Body</li>
</ol>
    

Advantages of packages:
<ul>
	<li>modularity</li>
	<li>easier application design</li>
	<li>information hiding</li>
	<li>better performance</li>
	<li>added functionality</li>
</ul>
    


Package specification tells the user what will it do rather than how it will do.

It contains only the program headers(type name_of_the_program (parameters list)) than the executable code.

Syntax:
```
CREATE OR REPLACE PACKAGE package_name
AS
 program_header1
 program_header2
 .
 .
 program_headern
END package_name;
/
```



Package body

It contains the executable statements that correspond to the headers in the package specification.

```	
CREATE OR REPLACE PACKAGE BODY package_name
AS
 program_header1
 program_header2
 .
 .
 program_headern
END package_name;
/
```

** package_name should be same as the specification.

Executing a package:
```
EXECUTE package_name.subprogram([variables]);
```

Records
it helps to work with the rows inside a PL/SQL program.
It can hold more than 1 piece if informtn as compared to a sclar datatype.

code is simple,clean and easy to maintian

declaration:
record_name tablename%rowtype;

to display: record_name.columnname
we change the value too by assigning := value to the above line
we can copy one record to another

user-defined record types:
syntax:
```
TYPE record_name IS RECORD(
variable datatype(size);
);
```

Cursors:
creates a memory area, known as context area, for processing an SQL statement, which contains all information needed for processing the statement.
PL/SQL controls the context area through a cursor. A cursor holds the rows (one or more) returned by a SQL statement. The set of rows the cursor holds is referred to as the active set.
we name cursors so that it could be refered to in a program to fetch and process the rows returned by the sql statement, one at a time.
    two types:

Two types:
<ol>
	<li>Implicit cursor (default cursor)</li>
	<li>Explicit</li>
</ol>



In implicit we have, %found, %notfound, %isopen, and %rowcount.

%found, is true when a row gets affected during DML commands (select into)
%notfound opposite to the above condition
%isopen always returns false, because oracle closes the SQL cursor automatically after executing SQL statement.
%rowcount returns no. of rows affected by an DML select into

Private SQl area, which the server allocated at runtime for each SQL statements.
if host program uses any variables in the SQL statements, the cursor also contains the memory addresses of these variables.


Steps for Explicit cursor:

```
declare CURSOR cursorname is select from tb;
open OPEN cursor name;
fetch one or more times fetch cursor_name INTO declred varaibles;
close CLOSE cursor_name;
```


Records:
composite data type with similar data of same datatype.

Most used terms in this:
index, 
element, 
sparse, 
method

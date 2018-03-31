# Coding Convention for C
Basically, the naming style of a variable or function follows camelCase, and the position of parentheses follows the BSD.  
```
camelVariable // camelCase

if (1) // BSD
{
    ...
}
```
  
follows BSD, but do - while is written as:
``` c
do
{
    ...
} while (1);
```
## 1. Function
If arrays are used as parameters to functions, using pointer.  
```c
void setValue(int* arr);
void setValue2(int** arr);
void setValue3(int*** arr);
```
  
## 2. const
Use const when you want to use a pointer that is never changed as a function parameter.  
``` c
void setValue(const int* value);
```
  
## 3. 메크로
Macros are written in all capital letters and are separated by _ when a sentence ends.  
``` c
#define THIS_IS_SAMPLE
```
  
## 4. enum
When you use an enum, you name it like E_Test and redefine to typedef.  
```c
typedef enum E_Test { ... } Test;
```

## 5. struct
When you use an struct, you name it like ST_Test and redefine to typedef.  
```c
typedef struct ST_Test { ... } Test;
```

## 6. 괄호의 표기
Control statements enclosed in parentheses are always enclosed in curly braces to indicate the exact range.  
### 6-1. if - else
``` c
if (1)
{
    ...
}
else
{
    ...
}
```
  
However, if you have few executable statements and need to handle multiple conditions It is also used as follows.  
```c
if      (value == 1) { printf("%d\n", value); }
else if (value == 2) { printf("%d\n", value); }
else if (value == 3) { printf("%d\n", value); }
else if (value == 4) { printf("%d\n", value); }
else if (value == 5) { printf("%d\n", value); }
else                 { printf("%d\n", value); }
```
  
## 7. switch - case
switch - Use case indentation once in case statement.  
You should also create a default value because unexpected exceptions can occur.  
``` c
switch (value)
{
    case 1:
        ...
        break;
    case 2:
        ...
        break;
    default:
        ...
        break;
}
```
  
However, if you have few executable statements and need to handle multiple conditions It is also used as follows.  
``` c
switch (value)
{
    case 1: ... break;
    case 2: ... break;
    case 3: ... break;
    default: ... break;
}
```
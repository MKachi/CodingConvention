# Coding Convention for C
기본적으로 변수나 함수의 명칭 작성 스타일은 카멜 표기법을 따르고 괄호의 위치는 BSD방식을 따릅니다.  
``` c
int camelVariable; // 카멜 표기법

if (1) // BSD
{
    ...
}
```
  
BSD괄호 표기를 따르지만 do - while은 다음과 같이 작성합니다.
``` c
do
{
    ...
} while (1);
```
## 1. 함수
함수의 매개변수로 배열이 사용될 경우 포인터로 작성합니다.  
```c
void setValue(int* arr);
void setValue2(int** arr);
void setValue3(int*** arr);
```
  
## 2. 함수 포인터
함수 포인터는 항상 typedef로 재정의해 사용합니다.  
``` c
typedef int(*Sample)(int, int);
```
  
## 3. const
함수의 매개변수로 변경될 일이 없는 포인터를 사용할 땐 const를 사용합니다.  
``` c
void setValue(const int* value);
```
  
또한 함수의 반환형이 변경되어서는 안된다면 함수의 반환값에 const를 사용합니다.  
``` cpp
int getValue() const;
```
  
## 4. define
define은 모두 대문자로 작성하며 한 문장이 끝나면 _를 사용해 구분합니다.  
``` c
#define THIS_IS_SAMPLE
```
  
## 5. enum
enum을 사용할 때에는 enum키워드를 적지않고 선언하기 위해 E_Test와 같이 이름을 붙이고 typedef로 이름을 재정의 해줍니다.  
```c
typedef enum E_Test { ... } Test;
```

## 6. struct
struct을 사용할 때에는 struct키워드를 적지않고 선언하기 위해 ST_Test와 같이 이름을 붙이고 typedef로 이름을 재정의 해줍니다.  
```c
typedef struct ST_Test { ... } Test;
```

## 7. 괄호의 표기
괄호로 묶는 제어문들은 정확한 범위를 나타내기 위해 항상 중괄호로 묶어 사용합니다.  
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
  
그러나 실행 구문이 적고 여러 조건을 처리해야 하는 경우  
다음과 같이도 사용합니다.  
```c
if      (value == 1) { printf("%d\n", value); }
else if (value == 2) { printf("%d\n", value); }
else if (value == 3) { printf("%d\n", value); }
else if (value == 4) { printf("%d\n", value); }
else if (value == 5) { printf("%d\n", value); }
else                 { printf("%d\n", value); }
```
  
## 8. switch - case
switch - case문을 작성할 때 case에는 들여쓰기를 한번 사용합니다.  
또한 예상치 못한 예외가 발생할 수 있으므로 반드시 default값을 작성합니다.  
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
  
실행 구문이 적고 여러 조건을 처리해야 하는 경우  
다음과 같이 사용합니다.  
``` c
switch (value)
{
    case 1: ... break;
    case 2: ... break;
    case 3: ... break;
    default: ... break;
}
```
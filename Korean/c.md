# Coding Convention for C
기본적으로 변수나 함수의 명칭 작성 스타일은 카멜 표기법을 따르고 괄호의 위치는 BSD방식을 따릅니다.  
```
camelVariable // 카멜 표기법

if (1) // BSD
{
    ...
}
```
## 1. 명명 규칙
### 1-1. 변수
변수는 기본적으로 소문자로 시작하고 한 문장이 끝나면 대문자로 시작합니다.
``` c
int testValue;
```
  
### 1-2. 함수
함수는 소문자로 시작하고 한 문장이 끝나면 대문자로 시작합니다.  
``` c
int getValue();
```

## 2. 함수
함수의 매개변수로 배열이 사용될 경우 인자의 값은 다음과 같이 작성합니다.  
```c
void setValue(int* arr);
void setValue2(int** arr);
void setValue3(int*** arr);
void setValue4(const int* arr); // 이 배열은 변경될 일이 없음
```
  
## 3. const
함수의 매개변수로 변경될 일이 없는 포인터를 사용할 땐 const를 사용합니다.  
``` c
void setValue(const int* value);
```
  
## 4. 메크로
메크로는 모두 대문자로 작성하며 한 문장이 끝나면 _를 사용해 구분합니다.  
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
### 7-1. if - else if - else
``` c
if (1)
{
    ...
}
else if (1)
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
## 7-2. for
``` c
for (int i = 0; i < 10; ++i)
{
    ...
}
```

## 7-3. while
``` c
while (1)
{
    ...
}
```

## 7-4. do - while
``` c
do
{
    ...
} while (1);
```


## 8. switch - case - default
switch - case - default 구문을 작성할 때에는 반드시 default값을 작성합니다.  
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
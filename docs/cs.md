# Coding Convention for C#
기본적으로 변수의 작성 스타일은 카멜 표기법을 따르고 괄호의 표기는 BSD방식을 따릅니다.  
class의 이름이나 메서드를 작성할 때에는 파스칼 표기법을 사용합니다.  
``` csharp
public class Test // 파스칼 표기법
{
    public void Add(int a /* 카멜 표기법 */, int b);
};

if (true) // BSD
{
    ...
}
```
  
BSD괄호 표기를 따르지만 do - while은 다음과 같이 작성합니다.
``` csharp
do
{
    ...
} while (true);
```
  

## 1. 괄호의 표기
괄호로 묶는 제어문들은 정확한 범위를 나타내기 위해 항상 중괄호로 묶어 사용합니다.  
``` csharp
if (true)
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
  
## 2. switch - case
switch - case문을 작성할 때 case에는 들여쓰기를 한번 사용합니다.  
또한 예상치 못한 예외가 발생할 수 있으므로 반드시 default값을 작성합니다.  
``` csharp
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
``` csharp
switch (value)
{
    case 1: ... break;
    case 2: ... break;
    case 3: ... break;
    default: ... break;
}
```
  
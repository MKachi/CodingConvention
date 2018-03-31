# Coding Convention for C++
기본적으로 변수나 함수의 명칭 작성 스타일은 카멜 표기법을 따르고 괄호의 위치는 BSD방식을 따릅니다.  
class의 이름을 작성할 때에는 파스칼 표기법을 사용합니다.  
``` cpp
class Test  // 파스칼 표기법
{ ... };

int camelVariable; // 카멜 표기법

if (true) // BSD
{
    ...
}
```
  
BSD괄호 표기를 따르지만 do - while은 다음과 같이 작성합니다.
``` cpp
do
{
    ...
} while (true);
```
## 1. 함수
함수의 매개변수로 배열이 사용될 경우 포인터로 작성합니다.  
``` cpp
void setValue(int* arr);
void setValue2(int** arr);
void setValue3(int*** arr);
```
## 2. 함수 템플릿
함수 템플릿은 템플릿 지시문을 위에 선언한 후, 그 밑에 함수를 작성합니다.
(typename 대신 class를 사용하는 것을 허용하지 않습니다.)
```cpp
template <typename T>
void print(const T& value);

template <>
void print(const string& value);
```
  
## 3. const
함수의 매개변수로 변경될 일이 없는 참조자나 포인터를 사용할 땐 const를 사용합니다.  
``` cpp
class Base;
void setValue(const Base& base);
void setValue(const int* value);
```
  
또한 함수의 반환형이 변경되어서는 안된다면 함수의 반환값에 const를 사용합니다.  
``` cpp
int getValue() const;
```
  
## 4. define
define은 모두 대문자로 작성하며 한 문장이 끝나면 _를 사용해 구분합니다.  
만약 define으로 함수 구문을 작성해야 한다면 그 대신 inline 함수를 사용합니다.  
``` cpp
#define THIS_IS_SAMPLE

inline int MAX(int a, int b)
{
    return a > b ? a : b;
}
```
  
## 5. enum
상수로 enum을 사용하지 않는다면 enum보단 enum class를 사용합니다.  
``` cpp
enum class A
{
    ...
};
```

## 6. class
클래스는 특별한 경우가 아니면 기본적으로 생성자, 소멸자, 복사 생성자, 이동 생성자를 기본적으로 작성합니다.  
``` cpp
class Sample
{
public:
    Sample();
    Sample(const Sample& rhs);
    Sample(Sample&& rhs);
    ~Sample();

};
```
  
## 6. 상속
상속 구문을 작성할 때 클래스를 선언한 뒤 줄을 내려 상속 구문을 작성합니다.  
또한 상속을 하는 클래스는 반드시 가상 소멸자로 작성해야 합니다.  
순수 가상함수를 override 할 때에는 override 키워드만 작성합니다.  
```cpp
class Base
{
public:
    Base();
    virtual ~Base();
    virtual void print() = 0;

};

class Children
    : public Base
{
public:
    Children();
    virtual ~Children();

    void print() override;

};
```
  
상속을 허용하지 않는 클래스나 메서드에는 final 키워드를 사용합니다.
``` cpp
class A final
{
public:
    A();
    ~A();

};

class Base
{
public:
    Base();
    virtual ~Base();
    virtual void print() { ... }
    
};

class Child
    : public Base
{
public:
    Child();
    virtual ~Child();
    void print() override final { ... }

};
```
  
## 7. nullptr & auto
### 7-1. nullptr
포인터에 대한 NULL값은 반드시 nullptr 키워드를 사용합니다.  
### 7-2. auto
auto 키워드는 변수의 타입을 판단하기 어렵거나 템플릿 함수의 반환 타입을 예측할 때만 사용합니다.  

## 8. 괄호의 표기
괄호로 묶는 제어문들은 정확한 범위를 나타내기 위해 항상 중괄호로 묶어 사용합니다.  
``` cpp
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
  
## 9. switch - case
switch - case문을 작성할 때 case에는 들여쓰기를 한번 사용합니다.  
또한 예상치 못한 예외가 발생할 수 있으므로 반드시 default값을 작성합니다.  
``` cpp
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
``` cpp
switch (value)
{
    case 1: ... break;
    case 2: ... break;
    case 3: ... break;
    default: ... break;
}
```
  
## 10. namespace
using namespace를 사용하지 마세요.  
cpp에 namespace를 사용하는 함수는 다음과 같이 작성합니다.  
``` cpp
// Header
namespace Sample
{
    inline int getValue() const;
}

// cpp
namespace Sample
{
    inline int getValue() const
    {
        return 0;
    }
}
```
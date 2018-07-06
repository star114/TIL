# knowledge-sharing

## Copy

### copy elision

* copy optimize 기법
    ```c++
    S s = S(); // -> S s(S()) (-> S s)
    ```
    * copy constructor 에 side effect 있는 동작을 넣어선 안된다. optimize 정도에 따라 동작이 달라질 수 있다.
* return value optimization
    ```c++
    S f() {
        if (...) {
            return S{};
        }
        return S(1,2);
    }
    S s = f();
    ```
* named return value optimization
    * 하나의 변수로 named value 를 선언해두면 return 이 하나든 두개든 잘 optimization 된다.
* rvo & nrvo

### copy assignment

선언 후 assign 하는건 모두 operator= 이 불리게 된다.

### copy constructor 가 delete

copy elision 에서 최적화 전 시점에서 semantic 체크에 걸려 컴파일 에러가 난다.

## Static

### internal linkage

* .cc .cpp source file
    * translation unit
* .o file
    * 하나의 translation unit 으로 만들어진 object file
* library
    * object file 들을 link 를 통해 하나의 library 로 만듬.

#### visibility

* internal linkage <-> external linkage
* 외부 에서 볼 수 없음 : internal linkage
* 볼 수 있음 : external linkage

### storage duration

* automatic storage duration
    * variable 이 보고 있는 scope 이 끝나면 destructor 가 불린다.
* static storage duration
    * program
* thread_local storage duration
    * thread
    * 각 thread 의 stack 의 첫번째 영역에 할당됨.
* dynamic storage duration
    명시적 소멸자가 불릴 때

#### uninitialized data / initialized data 로 나뉘는 이유 (elf 포맷?)

* binary 에 사이즈만 적혀 있으면 되니까 (uninitialized data 의 경우)
* initialized data 는 사이즈 와 초기값들 정보가 다 필요
* string 데이터는 initialized data 에 들어 갑니다. (null terminated)

#### static storage duration

namespace 안에 선언된 변수, 함수 안의 static 변수 등..

### static member

### static thread safe

* static storage duration 에서 thread safe c++11 부터는 thread safe 함. (vc++2015 에는 버그 있었음.)
    * main thread 에서부터 초기화 되어 있으므로
* singleton 의 경우 접근시 초기화

### static initialize

* 선언된 순서대로 초기화
* 선언되지 않은 값은 0으로 생각
* (!) Static member initialize 하는 함수에서는 static 변수에 접근 하지 마라.

## String

### string literal lifetime

* string data 는 initialized data 에 들어가지만 순서는 보장되지 않음.
* 같은 스트링이라도 다른 주소 일 수 있다. (같은 주소에 있다는 스펙은 없음.)
* string을 automatic storage 에 선언하고 cstring 을 넣으면 initialized data 에서 copy 를 해야 함. 표준에서는 string 의 c_str 함수가 constant 타임을 보장해야 해서 copy on write는 허용하지 않는 최적화임.

### pointer vs array

* array 는 stack 에 저장됨. (가변길이 배열을 허용하지 않음.)
* 리턴할 때 유의해야 함.

### string literal

(!) 인접한 string token 은 서로 붙여버린다.

### string_literals (c++14)

```c++
using namespace std::string_literals;
std::string s1 = "abc\0\0def";
std::string s2 = "abc\0\0def"s;
```

s2는 null character 까지 포함됨.

### user definded literals

_ (underscore) 로 시작하는 경우만 define 가능

### ltt::string::c_string static function

## Covariance

### object slice

```c++
Base b2 = d1; // object slice
Derived d2 = b1; // compile error
```

### reference

```c++
Base& b2 = d1;
Derived& d2 = b1; // compile error //d2.d 를 정의할 수 없어서
```

### template parameter

#### vector with reference

reference 를 vector 의 member 로 사용할 수 없다.

#### covariance

일반적인 template parameter 에서는 covariance 나 contravariance 모두 지원하지 않는다.

## inline

## variadic template

## c++ 17

## c++ core guidelines

[c++ core guidelines link](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)

## tip

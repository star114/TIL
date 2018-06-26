# covariant-return-type

[More C++ Idioms/Covariant Return Types](https://en.wikibooks.org/wiki/More_C%2B%2B_Idioms/Covariant_Return_Types)

## Motivation

```c++
class Base {
public:
    virtual Base * clone() const {
        return new Base(*this); 
    }
};
class Derived : public Base {
public:
    virtual Base * clone() const override {
        return new Derived(*this); 
    }
};
Derived *d1 = new Derived();
Base * b = d1->clone();
Derived *d2 = dynamic_cast<Derived *>(b);
if(d2) {
    // Use d2 here.
}
```

상속 받는 함수의 리턴타입이 base클래스의 포인터인 경우, derived 클래스에서 이 함수를 호출하면, derived 가 아닌 base의 포인터를 리턴함.
clone 함수를 보면, derived 클래스는 derived 클래스 인스턴스를 생성하여 이를 리턴하고 싶으나 base 포인터가 리턴되어 이를 다시 derived 로 dynamic cast 를 해야 하는 경우가 생길 수 있다. 

## Solution

```C++
class Base {
public:
    virtual Base * clone() const {
        return new Base(*this); 
    }
};
class Derived : public Base {
public:
    virtual Derived * clone() const override {
        return new Derived(*this); 
    }
};
Derived *d1 = new Derived();
Derived *d2 = d1->clone();
if(d2) {
    // Use d2 here.
}
```

Covariant Return Type 에 의해 virtual function 의 return type이 base 클래스의 포인터라면, 이를 상속받는 derived 클래스에서 base 의 포인터가 아닌 자신의 포인터를 리턴하여도 정상적으로 함수 상속이 이루어질 수 있다.

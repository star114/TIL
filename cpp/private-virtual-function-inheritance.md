# private-virtual-function-inheritance

```
#include <iostream>

class Base {
public:
    virtual ~Base() = default;
    void test() { testInternal(); }
private:
    virtual void testInternal()
    {
        std::cout << __PRETTY_FUNCTION__ << std::endl;
    }
};
class Derived : public Base {
public:
    virtual ~Derived() = default;
private:
    void testInternal() override
    {
        std::cout << __PRETTY_FUNCTION__ << std::endl;
    }
};
int main()
{
    std::shared_ptr<Base> a = std::make_shared<Derived>();
    a->test();
    return 0;
}
```

>> Output:
>> virtual void Derived::testInternal()

private non virtual 혹은 member variable 은 Derived에서 볼 수 없으나, private virtual funtion의 상속에서 Derived 는 Base 의 이 함수를 볼 수 있고  상속이 가능하다!

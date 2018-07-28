# visitor

## C++

[Visitor Design Pattern in C++](https://sourcemaking.com/design_patterns/visitor/cpp/2)

### implementation

1. Add an accept(Visitor) method to the "element" hierarchy
2. Create a "visitor" base class w/ a visit() method for every "element" type
3. Create a "visitor" derived class for each "operation" to do on "elements"
4. Client creates "visitor" objects and passes each to accept() calls

### visitor vs tree traversal

#### visitor

visitor pattern 은 tree traversal logic 이 아니라 object 들의 action 을 정의하는 하나의 방식이다.
각각의 object 들이 특정 action 에서 어떻게 동작할 것인지 visitor class 에 모두 정의해 주어야 한다.

#### tree traversal

3가지 order의 traversal 이 존재한다.

1. preorder
2. postorder
3. inorder

#### visitor 와 tree traversal

tree 구조의 object 들의 visitor pattern 을 만들 경우 함께 쓰일 가능성이 많다.

### visitor vs polymorphism

object 의 action 을 구현하는 다양한 방식들이 있을 수 있다.

1. object 의 type 을 정의하고 switch case 를 통한 처리 (object 를 받는 외부 함수로 정의)
2. visitor pattern 이용 (상속 구조의 모든 object 는 accept 함수가 구현되어야 한다.)
3. polymorphism (virtual function call)

개인적으로는 1 < 3 < 2 로 우선순위를 두고 있다.

#### modern c++ (c++11, c++14, c++17, c++20...) 의 철학

free function 을 standard 에서 점점 선호하고 functional 의 기능을 제공하려 노력하고 있다.

이러한 움직임 속에서 object 는 data 자체와 그와 직접 연관된 interface 만 제공하는 것을 선호하는 것으로 해석되고,
object 의 action 은 visitor 로써, object 밖에 존재하는 것을 추구하는 것으로 보인다.

이는 지극히 개인적인 견해이다.

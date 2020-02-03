# enumeration-declaration

## definition

[An enumeration is a distinct type whose value is restricted to a range of values (see below for details), which may include several explicitly named constants ("enumerators"). The values of the constants are values of an integral type known as the underlying type of the enumeration.](https://en.cppreference.com/w/cpp/language/enum)

## scoped vs unscoped?

### unscoped

```c++
enum name { enumerator = constexpr , enumerator = constexpr , ... } // (1)
enum name : type { enumerator = constexpr , enumerator = constexpr , ... } // (2) (since C++11)
enum name : type ; // (3) (since C++11)
```

### scoped

```c++
enum struct|class name { enumerator = constexpr , enumerator = constexpr , ... } //(1)
enum struct|class name : type { enumerator = constexpr , enumerator = constexpr , ... } //(2)
enum struct|class name ; //(3)
enum struct|class name : type ; // (4)
```

## std::underlying_type

### what is underlying_type?

```c++
template <typename T>
struct underlying_type;
```

* If T is a complete enumeration type, provide a member typedef `type` that names the underlying type of T.
* Otherwise,
    * `until c++20`
        * undefined behavior.
    * `since c++20`
        * If T is not enumeration type, there's no a member typedef `type`.
        * Otherwise, program is ill-formed.

### helper types

```c++
template< class T >
using underlying_type_t = typename underlying_type<T>::type;
```

### notes

Each enumeration type has an underlying type, which can be
1. Specified explicitly (both scoped and unscoped enumerations)
2. Omitted, in which case it is int for scoped enumerations or an implementation-defined integral type capable of representing all values of the enum (for unscoped enumerations)

```c++
enum e1 {}; // std::underlying_type<e1>::type == unsigned
enum class e2 {}; // std::underlying_type<e2>::type == int
```
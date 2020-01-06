# string-view

## What is string view?

References to strings are very common in C++ programs,
but often the callee doesn't care about the exact type of the object that owns the data.
3 things generally happen in this case:

1. The callee takes const std::string& and insists that callers copy the data if it was originally owned by another type.
2. The callee takes two parameters—a char* and a length
    (or just char* and assumes 0-termination)—and reduces the readability and safety of calls and loses any helper functions the original type provided.
3. The callee is rewritten as a template and its implementation is moved to a header file.
    This can increase flexibility if the author takes the time to code to a weaker iterator concept,
    but it can also increase compile time and code size, and can even introduce bugs if the author misses an assumption that the argument's contents are contiguous.

## Examples

``` cpp
// caller
string goodCase = "hi";
func(goodCase); // do not copy.
func("bad"); // it constructs new string object and copy this c string

// callee
void func(const string& str) {
    // do something
}
```

``` cpp
// caller
func("bad"); // it doesn't construct new string object. use string_view with null terminated c string

// rewritten callee
void func(string_view str) {
    // do something
}
```

## References

* [string view paper](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3762.html)
* [string view cppreference](https://en.cppreference.com/w/cpp/string/basic_string_view)

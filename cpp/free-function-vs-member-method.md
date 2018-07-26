# free-function-vs-member-method

[cppreference iterator library](https://en.cppreference.com/w/cpp/iterator#)

## free-function

```cpp
for (auto itr = std::begin(v); itr != std::end(v); ++itr) {};
```

## member-method

```cpp
for (auto itr = v.begin(); itr != v.end(); ++itr) {};
```

## examples

* std::begin
* std::end

(cpp 17?)
* std::data
* std::emtpy
* std::size

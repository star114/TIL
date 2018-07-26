# data

## std::vector::data

[cppreference-vector-data](https://en.cppreference.com/w/cpp/container/vector/data#)

```
T* data() noexcept; // (since C++11)
const T* data() const noexcept; // (since C++11)
```

Returns pointer to the underlying array serving as element storage. The pointer is such that range [data(); data() + size()) is always a valid range, even if the container is empty (data() is not dereferenceable in that case).

### Parameters

(none)

### Return value

Pointer to the underlying element storage. For non-empty containers, the returned pointer compares equal to the address of the first element.

### Complexity

Constant.

### Notes

If size() is 0, data() may or may not return a null pointer.

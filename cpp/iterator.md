# iterator

## types

iterator, cost\_iterator, reverse\_iterator, const\_reverse\_iterator

## implementation

be carefule to implement "begin, end, rbegin, rend"
* const member method should return const\_iterator or const\_reverse\_iterator

```
// begin
iterator begin() noexcept;
const_iterator begin() const noexcept;

// end
iterator end() noexcept;
const_iterator end() const noexcept;

// cbegin
const_iterator cbegin() const noexcept;

// cend
const_iterator cend() const noexcept;

// rbegin
reverse_iterator rbegin() noexcept;
const_reverse_iterator rbegin() const noexcept;

// rend
reverse_iterator rend() noexcept;
const_reverse_iterator rend() const noexcept;

// crbegin
const_reverse_iterator crbegin() const noexcept;

// crend
const_reverse_iterator crend() const noexcept;
```

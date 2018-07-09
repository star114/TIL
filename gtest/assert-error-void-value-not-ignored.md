# assert-error-void-value-not-ignored

> ERROR :
> In file included from /usr/include/gtest/gtest.h:57.0,
> gtest.cpp: In Function 'int main(int, char\*\*)':
> gtest.cpp:12:3: error: void value not ignored as it ought to be
>   ASSERT\_THROW(throw my_exp(), my_exp);

This is assumption.

*ASSERT\_ macros should be used in the function which returns void.*

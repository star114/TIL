# vim-filename-modifiers

현재 작업 중인 파일 이름과 관련한 Vim 기능들이 있습니다. 우선 기본적으로 %는 현재 파일 이름을 나타냅니다.

즉, "ptime/query/plan_generator/dml_search/rewrite" 에서 "../qo_normalizer.cc"를 열었다고 했을 때
%는 "../qo_normalizer.cc" 가 됩니다.

% 뒤에 붙는 modifier를 이용해 이를 수정할 수 있습니다.

## 자주 사용하는 modifiers

:p, :h, :t, :r, :e 가 있습니다.

* :p는 해당 이름을 root부터 시작하는 fullpath로 만들어줍니다.
* :t와 :h는 각각 directory separator(리눅스에서는 /) 를 이용해 split 한 것의 가장 마지막과 나머지 부분. 즉, 수정하고 있는 파일 이름과 경로를 표현하기 위한 것인데, 이를 조합해서 사용할 수 있습니다.
    * 예를 들어 위의 상황에서 "%:h"를 하면 ".."이 되고 "%:t"를 하면 "qo_normalizer.cc"가 되는데, "%:p:h"는 "/.../ptime/query/plan_generator/dml_search", "%:p:h:h"는 ""/.../ptime/query/plan_generator", "%:p:h:t는 "dml_search"가 됩니다.
* :e와 :r은 :t와 :h의 동작을 extension separator(.)를 이용해서 한다고 생각하시면 됩니다.
    * 따라서 위의 상황에서 "%:e"는 "cc", "%:r"은 "../qo_normalizer"가 됩니다.
* 이를 ":t"와 ":h" 조합해서 사용할 수도 있는데 이때 ":t"와 ":h"는 반드시 ":r"이나 "e"보다 앞에 와야 합니다.
    * 예를 들어 "%:t:r"는 "qo_normalizer"가 됩니다.

## Points

이를 이용해서 작업 디렉토리를 옮기거나 다른 파일을 열 수 있습니다.

* 예를 들어 cc 파일에서 헤더 파일을 열고 싶으면, ":e %:r.h"를 하면 되고,
* 현재 작업 디렉토리를 지금 열려 있는 파일의 경로로 옮기고 싶으면, ":cd %:h"를 하면 됩니다.

:h, :t, :r, :e 는 각각 head, tail, root, extension의 약자라는 것을 생각하면 조금 더 쉽게 외울 수 있습니다.

## 더 자세히..

```
vim --cmd "help filename-modifiers"
```

를 통해서 더 자세한 내용을 확인할 수 있습니다.

## Tl;dr.

```
ptime/query/plan_generator/dml_search/rewrite> vim ../qo_normalizer.cc
```

* % -> ../qo_normalizer.cc
* %:p -> /full/path/to/ptime/query/plan_generator/dml_search/qo_normalizer.cc
* %:h -> ..
* %:p:h -> /full/path/to/ptime/query/plan_generator/dml_search
* %:p:h:h -> /full/path/to/ptime/query/plan_generator
* %:e -> cc
* %:r -> ../qo_nomralizer
* %:t:r -> qo_nomralizer
* %:p:r -> /full/path/to/ptime/query/plan_generator/dml_search/qo_nomralizer
* %:p:t:r -> qo_nomralizer

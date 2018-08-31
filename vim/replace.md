# replace

[replace using regular expressions](https://stackoverflow.com/questions/10336609/is-it-possible-to-use-find-and-replace-on-a-wildcard-string-in-vim#)

`fooValueBar => fooValueBar = Value + ValueOld`

`:%s/foo\(\w\+\)Bar/& = \1 + \1\Old/`

* \w\+ finds one or more occurences of a character. The preceeding foo and following Bar ensure that these matched characters are just between a foo and a Bar.
* \(...\) stores this characters so that they can be used in the replace part of the substitution.
* & copies what was matched
* \1 is the string captured in the \(....\) part.

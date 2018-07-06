# TIL

Today I Learned

A collection of concise write-ups on small things I learn day to day across a
variety of languages and technologies. These are things that don't really
warrant a full blog post.

_12 TILs and counting..._

---

### Categories

* [Apple](#apple)
* [Conference](#conference)
* [Cpp](#cpp)
* [Effective-cpp](#effective-cpp)
* [Git](#git)
* [Gtest](#gtest)

---

### Apple

- [mac-os-mojave-ios-12-public-beta](apple/mac-os-mojave-ios-12-public-beta.md)

### Conference

- [kodebox-code-chain-connect](conference/kodebox-code-chain-connect.md)
- [openstack-upstream-training](conference/openstack-upstream-training.md)

### Cpp

- [covariant-return-type](cpp/covariant-return-types.md)

### Effective-cpp

- [ITEM 47. 타입에 대한 정보가 필요하다면 특성정보 클래스를 사용하자](effective-cpp/47.md)

### Git

- [case-insensitive](git/case-insensitive.md)
- [git-config](git/git-config.md)
- [git-reflog](git/git-reflog.md)
- [how to check the changes in merge commit](git/merge-commit-changes.md)
- [path-git-work-tree-git-dir](git/path-git-work-tree-git-dir.md)
- [simple-commands](git/simple-commands.md)

### Gtest

- [gtest-command](gtest/gtest-command.md)

## Usage

How to use very useful script "createReadme.py"

To auto-generate the README.md file, you can run
    ./createReadme.py > README.md

If you are using git, you can install this script as a pre-commit git hook so
that it is autogenerated on each commit.  Use the following command:
    cd .git/hooks/ && ln -s ../../createReadme.py pre-commit && cd -

The script is from [jima80525/til-collective](https://github.com/jima80525/til-collective)

## Other TIL Collections

* [Today I Learned by Hashrocket](https://til.hashrocket.com)
* [jbranchaud/til](https://github.com/jbranchaud/til)
* [jwworth/til](https://github.com/jwworth/til)
* [thoughtbot/til](https://github.com/thoughtbot/til)

## License

&copy; 2018 Shin Heesik

This repository is licensed under the MIT license. See `LICENSE` for
details.

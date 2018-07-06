# insert-comma-as-delimeter

## accumulate

```c++
vector<string> x = {"1", "2", "3"};
string s = std::accumulate(std::begin(x), std::end(x), string(),
        [](string &ss, string &s) {
            return ss.empty() ? s : ss + "," + s;
        });
```

## iteration

```c++
vector<string> x = {"1", "2", "3"};
string s;
for (auto itr = x.begin(); itr != x.end(); ++itr) {
    if (itr != x.begin()) {
        s += ",";
    }
    s += *itr;
}
```

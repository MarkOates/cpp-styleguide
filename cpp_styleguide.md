## C++ StyleGuide


### Default Arguments

Unlike inline definitions and declarations which include spaces, default arguments should not include spaces surrounding their assignment operators `=`:

```cpp
// correct:
bool get_duck_cuteness(duck_t type, bool default_cuteness=true);

// incorrect:
bool get_duck_cuteness(duck_t type, bool default_cuteness = true);
```

The same applies for default arguments in class declarations:

```cpp
class Duckling
{
private:
   bool is_cute;

public:
   Duckling(bool is_cute=true);  // <- correct
   ~Duckling();
};
```



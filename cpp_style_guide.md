## C++ Style Guide

### Listing Header Files

With one exception, header files should always be listed in alphabetical order without grouping.  Files that are deeper in a directory tree should appear closer to the top.  The absolute minimum number of required header files should be included, and forward-declarations are preferable over include files when possible.

```cpp
#include <barlib/foobar/baz.h>
#include <barlib/barlib.h>
#include <iostream>
#include <sstream>
#include <vector>
```

The only exception to this rule occurs for `.cpp` source files which implement an interface defined by a `.h` file.  In this case, that header file should appear at the top of the rest of the `#include`s, and should be separated by a blank line.

in `myclass.cpp`:
```cpp
#include <myclass.h>

#include <barlib/barlib.h>
#include <foolib/bazlib.h>
#include <iostream>
#include <sstream>
```

For more context on this rule, see http://llvm.org/docs/CodingStandards.html#include-style.

### Default Arguments

Default arguments should not include spaces surrounding their assignment operators `=`:

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

### Class Definitions

```cpp
class ClassName
{
private:
   // enums
   enum possible_values
   {
      VALUE_UNDEF = 0,
      POSSIBLE_VALUE_1,
      POSSIBLE_VALUE_2,
      VALUE_MAX,
   };

   // static constants
   // static variables
   int next_id;
   // static functions

   // internal functions (not for public exposure)
   int __internal_function();

   // member variables variables (initial values declared in the initialization list)
   int parameter;

public:
   // constructors, destructor
   ClassName(int parameter);
   ~ClassName();

   // set_* functions (or other mutation functions)
   bool set_parameter(int parameter);

   // get_* functions (non mutating getters for direct parameter values)
   int get_parameter() const;

   // state querying functions (non-mutating, non direct parameter queries)
   bool is_parameter(int parameter) const;

   // operators
   bool operator==(const ClassName &other) const;

   // static pool collection functions (will need to find a new pattern for this)
   static bool add_member();
   static bool remove_member();
   static bool destroy_member();
   static bool find_member();
};
```

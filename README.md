# C++ PROGRAMMING GUIDE
> This is a personal note. I don't guarantee trueness of the information below.
### 1) Treat compiler warnings as error
Compilers are product of hundreds of smart people. Hence, we shouldn't ignore the compiler warnings even though they have false positive results. You can use the CMake commands below to enable all compiler warnings and treat them as error.

``` cmake
target_compile_options(app PRIVATE -Werror)
target_compile_options(app PRIVATE -Wall)
```

### 2) Make variables constant if possible
Reading code becomes easy if unchanged variables are marked as `const` (even better `constexpr`)

### 3) Functions must be small but not tiny
Any function should have a single purpose, and it should be small. If a function exceeds 100 line, or it's [cognitive-complexity](https://clang.llvm.org/extra/clang-tidy/checks/readability/function-cognitive-complexity.html) exceeds 70, then there is something wrong with software design. As mentioned in [Goodhart's law](https://en.wikipedia.org/wiki/Goodhart%27s_law),
> That every measure which becomes a target becomes a bad measure ...

do not make these measures (number of lines or cognitive-complexity) as your target. If functions become smaller than they needed to be then every function call add extra complexity to follow code. For instance, it is easier to follow two function than four function. Sometimes having more number of lines is better than to have two more functions.
> a() > b()

> a() > b() > c() > d()

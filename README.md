# cheatsheet

## Git basics
- 'git add .' - updates the file with all its changes
- 'git commit =m "message"' - saves a snapshot on my PC
- 'git push' = uploads my commits to GitHub so they're actually visible
- 'git clone <url>' - downlaods a repo from GitHub onto my PC

## SSH
- 'ssh-keygen -t ed25519' - makes a key pair so GitHub trusts my PC
- 'cat ~/.ssh/id_ed25519.pub' - prints my public key so I can copy it into GitHub Settings
- 'ssh -T git@github.com - tests if my key actually works



# C++ basics

## Libraries
- collections of pre-compiled code that developers reuse to avoid rewriting code from scratch outside of the basic ones included in the core C++
- `#include <library>` at the very top of the file brings in a library or extra functionality to a program
- std is a namespace that contains the contents or files that come from standard libraries (like `cout`, `string`, `vector`)
- `std::` - most built-in stuff (like `cout`, `string`, `vector`) lives in the `std` namespace, so technically you write `std::cout`; while you need it for standalone things like `cout` that come from std, you only use it once for variable elements to call them; for example `std::string str = "hello";` but not for `str.empty()`
- `using namespace std;` - lets you skip typing `std::` every time; common for small projects and in classes, but for larger projects and professional use that may use many libraries outside the standard, to avoid confusing the compiler it is good to write it each time
- Common ones:
  - `<iostream>` - for basic input/output (`cin`, `cout`)
  - `<string>` - for the `string` type
  - `<vector>` - for the `vector` type
  - `<cmath>` - math functions (`sqrt`, `pow`, etc.)
  - `<algorithm>` - useful tools like `sort()`, `find()`

## Functions
- a block of reusable code that performs a specfic task, many of these make up complex programs
- '[return type] [function title] ([declare input variables]);` - function header
    - return type - what you want the function to return (int, string, array, etc.) or void, used when you change or execute something in the progrma but don't need a return value.
    - function title - the name of the function for you to call it within the program
    - input varaibles - the variables that go into the function and are needed for an output
- `int add(int a, int b)
   {
        return a + b;
   }`
    - a function named `add`, takes two ints, returns an int
- `void printHello() { }` - `void` means it returns nothing
- **Passing arguments - 3 ways:**
  - `void f(int x)` - pass by VALUE: the function gets a COPY, changes inside don't affect the original
  - `void f(int &x)` - pass by REFERENCE: the function can actually change the original variable
  - `void f(const int &x)` - pass by CONST REFERENCE: efficient like a reference (no copy made), but can't be changed — the standard choice for passing big things (like vectors or strings) into a function that only needs to read them

## Comments
- `// text` - single-line comment, ignored by the compiler
- `/* 
        text 
   */`                  
   - multi-line comment

## Data types
**int**
- a whole number, no decimals
- 32 bits = 4,294,967,296 possible values total
  - **signed** (default): -2,147,483,648 to 2,147,483,647 (positive and negative);
  - **unsigned**: 0 to 4,294,967,295 (positive only, no negatives)
- `int x = 5;` - declares and initializes
- `x = 10;` - changes the value later (no `int` needed once it already exists)

**double / floating-point number**
- numbers WITH decimals
- `double` = more precision, uses 8 decimal places (use this by default), `float` = less precision, smaller and uses 4 decimal places; meant to optimize memory, cache efficiency, and execution speed if needed
- `double price = 19.99;`

**char**
- a single character, always in single quotes
- `char grade = 'A';`

**bool**
- true or false only
- `bool isRunning = true;`

**string**
- text (multiple characters), always in double quotes
- needs `#include <string>` at the top of the file
- `string name = "Ryder";`
- `name + "!"` - strings can be joined ("concatenated") with `+`
- `name.length()` or `name.size()` - returns the total number sof characters in the string.
- `name.empty()` - returns true if the string has nothing in it, its length is 0; typically used in if statements
- `name.clear()` - erases all elements from the string, making it empty

## Arrays
- a fixed-size list of values, all the same type - size can't change once created
- `int scores[5];` - makes an array that holds 5 ints (empty for now)
- `int scores[5] = {90, 85, 77, 92, 88};` - makes it and fills it at once
- `scores[0]` - gets the FIRST item (arrays start counting at 0, not 1 - this trips everyone up at first)
- `scores[2] = 100;` - changes the 3rd item
- going past the last index (e.g. `scores[5]` on a 5-item array) doesn't error - it just reads garbage memory. Be careful.

## Vectors
- like an array, but it can GROW or SHRINK while the program runs
- needs `#include <vector>`
- `vector<int> nums;` - makes an empty vector of ints
- `nums.push_back(5);` - adds 5 to the end
- `nums.size()` - how many items are in it right now
- `nums[0]` - access items the same way as arrays
- use vectors by default over arrays unless the size is truly fixed and known

## Loops
- `for (int i = 0; i < 10; i++) { }` - runs a set number of times; `i` counts 0 to 9 here
- `while (condition) { }` - runs as long as the condition stays true (could run 0 times)
- `do { } while (condition);` - same as while, but always runs AT LEAST once
- `for (int n : nums) { }` - "range-based for" - walks through every item in an array/vector automatically, `n` is each item in turn

## Conditionals
- `if (condition) { } else if (condition) { } else { }` - runs one branch based on true/false
- `&&` = AND (both must be true), `||` = OR (either can be true)
- `switch (value) { case 1: ... break; default: ... }` - alternative to a long if/else chain when checking one variable against many exact values

## Scope
- anything declared inside `{ }` (a function, a loop, an if-block) only exists inside those braces - it's gone once you exit
- variables declared OUTSIDE any function ("global") can be accessed anywhere in the file - generally avoid these unless there's a good reason, they get messy fast
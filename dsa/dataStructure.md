# MultiSet
**Multiset** (`std::multiset`):
`multiset` is a C++ container from the Standard Template Library (STL) that:

1. Stores elements in sorted order - automatically maintains ordering
2. `Allows duplicates` - unlike set, you can have multiple copies of the same value
3. Provides logarithmic time operations - insert, delete, and search are `O(log n)`
4. Implemented as a balanced binary search tree - typically a red-black tree
5. Can access smallest with `begin()` and largest with `prev(end())`


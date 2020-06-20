## Introduction

Data structure `map` is implemented by a binary search tree (BST), so it keeps the order sorted by keys. `unordered_map` is implemented by hash functions, so the order of its elements is random. 

## Map

## Unordered_Map

### Basic
```
#include <iostream>
#include <unordered_map>

int main() {
    std::unordered_map<char, int> mymap;
    mymap['a'] = 1;
    mymap['b'] = 10;
    mymap['c'] = 100;

    for (auto it : mymap)
        std::cout << it.first << " " << std::endl;
}
```

### Methods

* Indexing
```
std::cout << mymap['a'];
//or
std::cout << mymap.at('a');
```

* Add a new item
```
mymap.inset(make_pair('d', 1000));
```

* Find an item by key
```
// if (mymap.count('b') > 0)
if (mymap.find('b') == mymap.end())
    std::cout<< "Not found" << std::endl;
else
    //Do something
```

* Remove an item by key
```
mymap.erase('a');
```

* Clear all items in the map
```
mymap.clear();
```

* Swap two maps
```
mymap.swap(yourmap)
```
* Iterate
```
for (auto it : mymap)
    // key => it.first
    // val => it.second

for (std::unordered_map<char,int>::iterator it = mymap.begin(); it != mymap.end(); it++)
    // key => it->first
    // val => it->second
```
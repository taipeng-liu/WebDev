## Description

In computer science, `string` is usually a representation of an array of `char`. 

For example, "Hello" is a `string`, and 'H' is a `char`. "taipeng2" is a `string`, 't' is a char and 2 is a number.

You may have noticed that a `string` is often referred with `""`, and a `char` is used with `''`. Although in some languages (e.g., Python) `''` can also be used to a `string`, in the following discussion we use `""` to represent a `string`.

## Initialization

C doesn't have a key word `string`, so we use an array of `char` instead:

```
char c = 'a';
char *str1 = "hello world";
//or
char str2[] = "hello world";
```

In C++:
```
char c = 'a';
string str = "hello world";
```


In Python:
```
c = 'a'
str = "hello world"
```

## Length of string

C++:
```
int len = str.length();
```
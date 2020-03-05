# std::string

https://www.learncpp.com/cpp-tutorial/4-4b-an-introduction-to-stdstring/  

**string** : collection of sequential characters 

**string literals** : placed between double quotes "string literal" , or single quotes 'string literal'

 

in c++ 

* string is **not built in data type** to language
* its part of **standard library std::string**

###### to use 

* ```c++
  #include <string>
  ```

  

* create string variable using std::string

  ```c++
  std::string myName;
  ```





###### Simple program to demonstrate std::string

**file name:** string_demo1.cpp

```c++
// Program to demonstrate std::string in c++
// Mar 2020

#include <iostream>
#include <string>

int main() {
	// declare a string. observe std::string. 
	// std  --> standard namespace
	// uniform initialization of string variable to a string literal.
	// Observe that string literal is placed in double quotes
	std::string myName{ "Rajesh1" }; 

	std::cout << "uniform initialization --> myName= " << myName << std::endl;

	// Assignment operation just like normal variable. 
	// Observe that string literal is placed in single quotes
	myName = 'Rajesh2';

	std::cout << "after assignment operation --> myName= " << myName << std::endl;

	// program executed successfully. return status code 0
	return 0;

}
```

  output:

```
uniform initialization --> myName= Rajesh1  

after assignment operation --> myName= Rajesh2 
```


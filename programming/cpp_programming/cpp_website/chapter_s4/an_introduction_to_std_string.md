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

```c++
uniform initialization --> myName= Rajesh1  
after assignment operation --> myName= Rajesh2 
```



**Note:**

Numbers in quotes (either single or double)  --> string   , not number

```c++
// 45 is treated as string. not number --> not integer
std::string myIntAsString{"45"};

// 45.55  is treated as string. not number --> not float
std::string myFloatAsString{"45.55"}; 
```



###### Read string from user input : std::cin   --> avoid

```c++
#include <iostream>
#include <string>

int main() {
	// declare a string variable
	// Not initialized
	std::string myName;

    // myAge is declared as string
	std::string myAge;

	// Read user input using std::cin 
	// Note: avoid. 
	// why ?? std::cin --> returns characters up to first white space
	//                 --> any other characters --> next extraction
	//   eg: John Doe   --> John is returned
	//                  --> Doe is returned for next std::cin

	// John is read here
	std::cout << "Enter full name: ";
	std::cin >> myName; 

	// Doe is read here
	std::cout << "Enter age: ";
	std::cin >> myAge;

	std::cout << "myName=" << myName << std::endl;
	std::cout << "myAge=" << myAge << std::endl;

	return 0;
}
```

output: 

```
Enter full name: John Doe 
Enter age: myName=John         
myAge=Doe
```



if myAge is declared as **int**. no other changes. observe the output. 

```c++
#include <iostream>
#include <string>

int main() {
	// declare a string variable
	// Not initialized
	std::string myName;

    // myAge is declared as int.
	int myAge;

	// Read user input using std::cin 
	// Note: avoid. 
	// why ?? std::cin --> returns characters up to first white space
	//                 --> any other characters --> next extraction
	//   eg: John Doe   --> John is returned
	//                  --> Doe is returned for next std::cin

	// John is read here
	std::cout << "Enter full name: ";
	std::cin >> myName; 

	// Doe is read here
	std::cout << "Enter age: ";
	std::cin >> myAge;

	std::cout << "myName=" << myName << std::endl;
	std::cout << "myAge=" << myAge << std::endl;

	return 0;
}
```

output: 

```
Enter full name: John Doe  
Enter age: myName=John   
myAge=0 
```

**Explanation:**

* when we use ">>" operator to extract string from cin 
  * operator returns characters up to first whitespace
  * other characters after whitespace are left inside cin , waiting for next extraction
* John Doe
  * John extracted first --> assigned to myName
  * Doe is after whitespace. so it's assigned to myAge. 
  * Never asked to enter age. 


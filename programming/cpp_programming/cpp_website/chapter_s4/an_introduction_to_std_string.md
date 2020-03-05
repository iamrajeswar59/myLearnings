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





### Simple program to demonstrate std::string

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



### Read string from user input : std::cin   --> avoid

**file name:** string_demo2.cpp

```c++
#include <iostream>
#include <string>

int main() {
	// declare a string variable
	// Not initialized
	std::string myName{};

    // myAge is declared as string
	std::string myAge{};

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

**file name:** string_demo2.cpp

```c++
#include <iostream>
#include <string>

int main() {
	// declare a string variable
	// Not initialized
	std::string myName{};

    // myAge is declared as int.
	int myAge{};

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

### std::getline(std::cin,string_variable_name);

* Read full line of text input in to a string
* two parameters
  * first: std::cin()
  * string variable

**file name**: string_demo3.cpp

```c++
// use std::getline() to read full text from user

#include <iostream>
#include <string>

int main() {

	std::cout << "Enter full name:";
	std::string fullName{};
	std::getline(std::cin, fullName);

	std::cout << "Enter your age:";
	std::string age{};
	std::getline(std::cin, age);

	std::cout << "fullName= " << fullName<<std::endl;
	std::cout << "age= " << age << std::endl;

	return 0;
}
```

output:

```
Enter full name:John doe
Enter your age:23
fullName= John doe
age= 23
```

### std::cin and std::getline() together  --> avoid

* May cause unexpected behavior
* What should happen:
  * first: ask user to pick 1 or 2
  * second: ask user to enter name
* what will happen:
  * first: user is asked to pick 1 or 2
  * it wont wait for entering name
  * print the final message and exits
* why?
  * cin not only captures (1 or 2), it also captures newline
  * when user enters 2: cin gets "2\n"
  * it extracts 2 to variable choice, "\n" is still stuck in input stream
  * when std::getline() wants to read name --> "\n" is already in stream. so it considers it as empty string. 
  * not what is intended 

```c++
#include <iostream>
#include <string>

int main() {
	std::cout << "Pick 1 or 2";
	int choice{};
	std::cin >> choice;

	std::cout << "enter full name";
	std::string fullName{};
	std::getline(std::cin, fullName);

	std::cout << "Hello, " << fullName << " , you picked " << choice << "\n";


	return 0;
}
```

output:

```
Pick 1 or 2: 1
enter full nameHello,  , you picked 1
```



#### Is there a solution? yes. 

* After reading a value with **std::cin**, remove newline from stream
* its good idea to remove extra newline using 

```
std::cin.ignore(32767,'\n'); // ignore up to 32767 characters until a \n is removed
```

**file name:** string_demo4.cpp

```c++
#include <iostream>
#include <string>

int main() {
	std::cout << "pick 1 or 2: ";
	int choice{};
	std::cin >> choice;

	std::cin.ignore(32767, '\n'); //ignore up to 32676 characters until a \n is removed

	std::cout << "enter your name=";
	std::string name;
	std::getline(std::cin, name);

	std::cout << "name=" << name << ", you picked " << choice << std::endl;

	return 0;
}
```

output: 

```
pick 1 or 2: 2
enter your name=john doe
name=john doe, you picked 2
```

if we keep std::cin.ignore() directly after std::cin , extra "\n" newline is removed from stream and program will work as expected. 

**What is 32767 in std::cin.ignore?**

* That tells std::cin.ignore() , how many characters to ignore up to
* largest signed value to fit in signed integer on all platforms (2 byte signed int)



* **technically correct way**

  * ```c++
    #include <ulimits>
    ```

  * ```c++
    //ignore unlimited characters until a \n is removed
    std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
    ```

    

  * Most of the time, we don't need to ignore more than a line or two of buffered input --> practical purposes: 36767 suffice

##### Will the same problem happens for a repeated std::cin? no. 

*  no

```c++
#include <iostream>

int main() {

	std::cout << "enter number 1:";
	int var1{};
	std::cin >> var1;

	std::cout << "enter number 2:";
	int var2{};
	std::cin >> var2;

	std::cout << "var1= "<< var1 << std::endl;
	std::cout << "var2= "<< var2 << std::endl;

	return 0;
}
```

output: 

```
enter number 1:1
enter number 2:2
var1= 1
var2= 2
```



#### Appending strings 

* "+" concatenation operator: 

**file name:** string_concatenation1.cpp

```c++
#include <iostream>
#include <string>

int main() {
	std::string a{ "45" };
	std::string b{ "11" };

	//concatenate string a,b
    // 45 and 11 are strings, not numbers so they are not added, but concatenated. 
	std::cout << "a+b= " << a + b << "\n";

	//concatenate string "a" and string literal "volts"
	a += " volts";
	std::cout << "a= " << a<<std::endl;

	return 0;
}
```

output:

```
a+b= 4511
a= 45 volts
```

#### string length

* std::string --> member function : string_name.length()
* not length(string_name)

**file name:** string_length1.cpp

```c++
// String length

#include <iostream>
#include <string>

int main() {
	std::string myName{ "John Doe" };

	// use string_name.length() member function of std::string
	std::cout << "myName= " << myName << ", length= " << myName.length() << std::endl;

	std::cout << "type(length() function)=" << typeid(myName.length()).name() << std::endl;

	return 0;
}
```

output: 

```
myName= John Doe, length= 8
type(length() function)=unsigned int
```



**problem statement:** 

user input: name, age

output: age / "number of letters in name"

**file name**: string_problem_set1.cpp

```c++
// user input: name, age
// tell user how many years they have lived for each letter in their name
// count spaces as letter

#include <iostream>
#include <string>

int main() {
	std::cout << "enter your name: ";
	std::string name{};
	//read a full line of text in to line
	std::getline(std::cin, name);

	//age needs to be an integer
	std::cout << "enter your age: ";
	int age{};
	std::cin >> age;

	//get number of letters in name
	// static cast unsigned int output of length() function in to int
	int num_of_letters{ static_cast<int>(name.length()) };
	//convert int in to double to avoid integer division
	double agePerLetter{ static_cast<double>(age) / num_of_letters };

	std::cout << "you have lived " << agePerLetter << " years for each letter in your name. \n";

	return 0;
}
```

output:

```
enter your name: John Doe
enter your age: 48
you have lived 6 years for each letter in your name.
```


## Abstraction in C++ ##
In the active project, daily the code grows due to lots of developer working on same repo. So, we need the abstractions to handle the complexity and inter operation ability. Abstractions may require at functions, class, structure level. Main advantage of C++I s that, offers very low cast abstraction with minimal performance concern. 

Let take a counting operation of data and let me represent how abstraction is helps in C++. 
Here we can compare a C and C++ level of programs to represent the abstractions and benefits. 

#### C Program: ####
```c
struct ActiveEmployee {
    const char* grade;
    ActiveEmployee* nextPtr;
    int getCount(ActiveEmployee* listOfEmployees) {
      int count=0;
      ActiveEmployee* itr=listOfEmployees;
      while(itr != NULL) {
        if(strcmp(itr->grade,"Engineer") == 0)
          count++;
        itr=itr->nextPtr;
      }
      return count;
    }
}
```
So, Now will can check about C++ approach to get count of active Employees. 

```cpp
int getCount(const std::list<ActiveEmployee> listOfEmployees) {
  return std::count(listOfEmployee.begin(),listOfEmployees.end(),"Engineer");
}
```
Let observe both the code, in C raw pointer used to iterate the list and programer need to code increment of each iteration and makes a const comparision to increment next memory address of variable ``` ActiveEmployee```. 
But in case of C++, no need to find the memory increment, use the data structure abstraction ```std::list<ActiveEmployee>``` and ```std::count``` interface.

Some rules or some useful guidelines need to follow to make class interfaces.
- Class should follow the deep copy method or avoid the copy of class object. If class having any heap allocation, it might give wrong/bad access of memory if it failed in copying. 
  ```cpp
  class BankAccount {
    public:
        auto set_loanInterest(
        

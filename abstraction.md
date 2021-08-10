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
    private:
        float m_loanInterest;
    public:
        auto set_loanInterest(float loanInterest) {
                m_loanInterest=loanInterest;
        }
        auto get_loanInterest() {
                return m_loanInterest;
        }
   };
   
   class OfficeAccount: public BankAccount {
       //Defined for office use
   }
   
   ```
   Now, programer need to add new loan account and attach to existed account. So will create a new loan class and trying to use existed account details. 
   ```cpp
   class PersonalLoan {
        private:
            std::shared_ptr<BankAccount> m_account;
            float m_loanAmount;
        public:
            PersonalLoan(std::shared_ptr<BankAccount> acc, float loanAmount) : m_account{acc}, m_loanAmount{loanAmount} {
                std::cout<<"\n [Log]: Creating Personal Loan Account ";
            }
            
            auto& getAccount() { 
                return m_account;
            }
    };
    ```
     Now another programmer wants to use loan accounts to set new interest rates based on type of loan. It might create a problem. Please check the below code.
     
     ```cpp
     auto loan1=PersonalLoan{std::shared_ptr<OfficeAccount>(),1.2};
     auto loan2=loan1;
     loan2.getAccount()->set_loanInterest(1.5); // This will create same interest rates for all the loans, bcz BankAccount shared accross loan object
     ```
     If new programmer wants to use the PersonalLoan class, he/she can find another approach or intimate the programer by avoiding the copying object. 
     Now, PersonalLoan class needs to be avoid the copy feature. Let make it :)
     
     ```cpp
   class PersonalLoan {
        private:
            std::shared_ptr<BankAccount> m_account;
            float m_loanAmount;
            PersonalLoan(const PersonalLoan&) = delete;
            auto operator=(const PersonalLoan& b) -> PersonalLoan& = delete;
        public:
            PersonalLoan(std::shared_ptr<BankAccount> acc, float loanAmount) : m_account{acc}, m_loanAmount{loanAmount} {
                std::cout<<"\n [Log]: Creating Personal Loan Account ";
            }
            
            auto& getAccount() { 
                return m_account;
            }
    };
    ```
                
        

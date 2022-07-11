# Chapter 3 Day 2 Quests Answers

## 1. Explain why we wouldn't call changeGreeting in a script.

### changeGreeting modifies the state which is done in a transaction. A script can only view the state, NOT modify it. 

## 2. What does the AuthAccount mean in the prepare phase of the transaction?

### AuthAccount allows for access/modifications to the storage of an account when the transaction is signed in prepare phase of the transaction. The confirmation ensures the user approves of the transaction and wants to continue.

## 3. What is the difference between the prepare phase and the execute phase in the transaction?

### The prepare phase in the transaction is the phase where data is viewed, whereas the execute phase of the transaction is the phase where the data is modified.

## 4. This is the hardest quest so far, so if it takes you some time, do not worry! I can help you in the Discord if you have questions.

- Add two new things inside your contract:
  - A variable named myNumber that has type Int (set it to 0 when the contract is deployed)
  - A function named updateMyNumber that takes in a new number named newNumber as a parameter that has type Int and updates myNumber to be newNumber

``` cadence
pub contract HelloWorld {

    pub var greeting: String
    pub var myNumber: Int

    pub fun changeGreeting(newGreeting: String) {
        self.greeting = newGreeting
    }

    pub fun updateMyNumber(newNumber: Int) {
        self.myNumber = newNumber
    }

    init() {
        self.greeting = "Hello, World!"
        self.myNumber = 0
    }
}
```

- Add a script that reads myNumber from the contract

``` cadence
import HelloWorld from 0x01

pub fun main(): Int {
    return HelloWorld.myNumber
}
```
![Screen Shot 2022-07-11 at 4 56 13 PM](https://user-images.githubusercontent.com/104539205/178365550-91087922-543c-4239-b8d1-615d280f4814.png)

- Add a transaction that takes in a parameter named myNewNumber and passes it into the updateMyNumber function. Verify that your number changed by running the script again.
``` cadence
import HelloWorld from 0x01

transaction(myNewNumber: Int) {

  prepare(signer: AuthAccount) {}

  execute {
    HelloWorld.updateMyNumber(newNumber: myNewNumber)
  }
}
```
![Screen Shot 2022-07-11 at 5 00 45 PM](https://user-images.githubusercontent.com/104539205/178366145-38cc646a-a5b5-48a2-a0e0-3a856f7d50d7.png)

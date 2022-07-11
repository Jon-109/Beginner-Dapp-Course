# Chapter 3 Day 1 Quests Answers

## 1. Deploy a contract to account 0x03 called "JacobTucker". Inside that contract, declare a constant variable named is, and make it have type String. Initialize it to "the best" when your contract gets deployed.
``` cadence
pub contract JacobTucker {

    pub var is: String

    init() {
        self.is = "the best"
    }
}
```

## 2. Check that your variable is actually equals "the best" by executing a script to read that variable. Include a screenshot of the output.
``` cadence
import JacobTucker from 0x03

pub fun main(): String {
    return JacobTucker.is
}
```
![Screen Shot 2022-07-11 at 4 28 39 PM](https://user-images.githubusercontent.com/104539205/178361632-3ddd270c-9de3-4c32-b7a3-db6ab5caa617.png)


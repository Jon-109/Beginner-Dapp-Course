# Chapter 3 Day 3 Quest Answers

## 1. Create a new smart contract in Cadence that has at least the following two things:
- A variable to hold a value (like a number or a piece of text)
- A function to change that variable

``` cadence
pub contract HelloWorld2 {

    pub var insult: String

    pub fun changeInsult(newInsult: String) {
        self.insult = newInsult
    }

    init() {
        self.insult = "you are dog water kid"
    }
}
```

## After, deploy that contract to the same testnet account you generated today.

## 2. Send a screenshot of you reading the variable from your new contract using the Flow CLI
<img width="682" alt="Screen Shot 2022-07-11 at 5 52 04 PM" src="https://user-images.githubusercontent.com/104539205/178371974-aee818de-1350-405c-8df7-57e03aea0773.png">

## 3. Send a screenshot of you changing the variable from your new contract using the Flow CLI
<img width="648" alt="Screen Shot 2022-07-11 at 5 53 03 PM" src="https://user-images.githubusercontent.com/104539205/178372073-471f391e-8e9d-4abc-8b21-65ee7a703dc7.png">

## 4. Send a screenshot of you reading your changed variable from your new contract using the Flow CLI
<img width="647" alt="Screen Shot 2022-07-11 at 5 53 17 PM" src="https://user-images.githubusercontent.com/104539205/178372090-0c5a1aca-34f1-4feb-bd3e-525a4a2be6cf.png">

## 5. Go to https://flow-view-source.com/testnet/. Where it says "Account", paste in the Flow address you generated and click "Go". On the left hand side, you should see your "HelloWorld" contract and your new contract. Isn't it so cool to see them live on Testnet? Then, send the URL to the page.
https://flow-view-source.com/testnet/account/0x08722b123ca9a185

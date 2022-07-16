# Chapter 5 Day 1 Quests Answers

## 1. List all the possible transaction status codes and what each of them mean.

### 0 - Pending, 1 - Pending, 2 - Finalizing, 3 - Executing, 4 - Sealed

## 2a. What does setTimeout do?

### setTimeout sets a timer which executes specified code when the timer is over. It takes in two parameters - code/function and a delay. The delay is set as a parameter in milliseconds. 

## 2b. How would we change our code if we wanted the txStatus variable to reset back to its original state after 5 seconds?

### We could change 2000 to 5000 like the following: setTimeout(() => setTxStatus('Run Transaction'), 5000);

## 3. What does the fcl.tx(transactionId).subscribe(res => {...}) function do?

### First we use a flow client library (fcl) function .tx() that allows for status updates and it takes the object of res and gives the status of the transaction by using the .subscribe() function and in our code it places that status to the txStatus variable.

## 4. Make at least 3 changes to the styling of the application. It can be anything (part of this quest is being creative!). List the 3 changes and point them out in a screenshot.

### 1. Change current greeting to be clear on the page by adding "Current Greeting: " then adding the currentGreeting in the contract.
### 2. Change the default button to say change greeting so it is more clear what the button does.
### 3. Changed the names and discord to myself 
### 4. Brought the title and everything up by decreasing the margin-top of .title in Home.module.css.
### 5. Made the box smaller by decreasing min-height of .main in Home.module.css.
![Screen Shot 2022-07-16 at 6 30 15 PM](https://user-images.githubusercontent.com/104539205/179375015-bc955a05-bc38-4c1c-9b2a-cbc7bf8ddf8d.png)

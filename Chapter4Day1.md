# Chapter 4 Day 1 Quest Answers

## 1. How did we get the address of the user? Please explain in words and then in code.

### First we imported the flow client library into the app which allows for people to log into popular flow wallets and it also connects the app to the testnet. After importing it, users can then sign in to access their wallets which then gives us the user account address. 

### Coding Step 1: Creating config.js file to integrate Flow Discovery and connect to testnet
``` cadence
import { config } from "@onflow/fcl";
import * as fcl from "@onflow/fcl"

fcl.config({
  "app.detail.title": "Emerald Dapp",
  "app.detail.icon": "https://placekitten.com/g/200/200" //placeholder pic i got from flow docs
})

config()
  .put("accessNode.api", "https://rest-testnet.onflow.org/") // This connects us to Flow TestNet
  .put("discovery.wallet", "https://fcl-discovery.onflow.org/testnet/authn/") // Allows us to connect to Blocto & Lilico Wallet
```

### Coding Step 2: Import Flow Client Library into Navigation Component so Users can use it to log in and out (i was going to do a bunch of seperate steps but figured adding the file with comments would suffice)
``` cadence 
import * as fcl from "@onflow/fcl"; //Import Flow Client Library into Navigation Component so Users can use it to log in and out
import "../flow/config.js"; //import config.js file to connect to the testnet
import { useState, useEffect } from 'react';
import styles from '../styles/Nav.module.css'; //imports styles from Nav module

export default function Nav() {
    const [user, setUser] = useState({ loggedIn: false }); //sets variable for user and also a sets default value for the setUser variable of NOT logged in

    useEffect(() => { //this function runs every time whatever event is in the [] brackets. in this case empty brackets means a page refresh will trigger this function
        fcl.currentUser.subscribe(setUser); //ensures the user variable retains its value even if the page is refreshed.
      }, [])
      
    function handleAuthentication() {
        if (user.loggedIn) { //if user is loggin in, then log them out
            fcl.unauthenticate(); // logs the user out
        } else { //if user is logged out, then bring up screen to allow then so log in
            fcl.authenticate(); // logs the user in
        }
    }

  return (
    <nav className={styles.nav}> //gives it the style detailed in styles/Nav.module.css
        <h1>Emerald DApp</h1> //Title on top of navigation
        <button onClick={handleAuthentication}>{user.loggedIn ? user.addr : "Log In"}</button> //button that displays the user account address when logged in or a "log in" button if not logged in and also when clicked it runs a handleAuthentication function to log the user in/out
    </nav>
  )
}
```



## 2. What do fcl.authenticate and fcl.unauthenticate do?

### In general fcl.authenticate logs a user in and fcl.unauthenticate logs a user out. Behind the scenes when fcl.authenticate is called a simple screen will pop up on the users end that will enable them to log in to popular Flow wallets using the Flow Discovery UI that we can use since we imported the Flow client library and integrated the Flow Discovery and its wallets/services in the app (more specifically in the config.js file).

## 3. Why did we make a config.js file? What does it do?

### We make a config.js file to integrate Flow Discovery which allows for people to log into popular flow wallets thanks to the Discovery UI and also connects the app to the testnet.

## 4. What does our useEffect do?

### The useEffect function is structed as useEffect(() => {x}, [y]). Whatever is in the {} braces will happen every time whatever event is in the [] brackets. In our case the [] brackets ar empty which means a page refresh will trigger this function. Kinda gives me the vibe of "ill do x when y occurs"  yeah such a vibe bro

## 5. How do we import FCL?

### First we install the dependency that enables us to integrate Flow Client Library into the app by typing the following code into the terminal of the project directory. 
``` cadence
npm install @onflow/fcl
```
### We then import it into the files that utilize it by inserting at the top of the files 
``` cadence 
import * as fcl from "@onflow/fcl";
``` 
### Now the Flow Client Library is imported and ready to be used.

## 6. What does fcl.currentUser.subscribe(setUser); do?

### It watches for changes to setUser and ensures the setUser variable retains its value.

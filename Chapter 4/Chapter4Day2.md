# Chapter 4 Day 2 Quests Answers

## 1. Instead of console logging the result after the script executes, I want you to:
-Make a new variable named greeting using useState
-Set the greeting variable to the response of the script call
-Create a <p> tag after the <div className={styles.flex}> tag
-Put the greeting variable inside of that <p> tag. This will make the result of your script show on your webpage! It should look something like this:
 ![image](https://user-images.githubusercontent.com/104539205/178602615-0f9ca672-e0e4-4f3e-83a4-0157de1225c0.png)
### My screen below:
![Screen Shot 2022-07-15 at 10 38 42 PM](https://user-images.githubusercontent.com/104539205/179337680-99dabdb4-dfd8-48a5-8a3d-531e845c5eba.png)

## 2a. I deployed a contract called SimpleTest to an account with an address of 0x6c0d53c676256e8c. I want you to make a button that, when clicked, executes a script to read the number variable from that contract. If you're curious, you can see the contract here: https://flow-view-source.com/testnet/account/0x6c0d53c676256e8c/contract/SimpleTest
### My code below in index.js
``` cadence
  import Head from 'next/head'
import styles from '../styles/Home.module.css'
import Nav from '../components/Nav.jsx';
import { useState, useEffect } from 'react';
import * as fcl from "@onflow/fcl";

export default function Home() {
  const [newGreeting, setNewGreeting] = useState('');
  const [greeting, setGreeting] = useState(''); //Make a new variable named greeting using useState
  const [number, setNumber] = useState('');

  function runTransaction() {
    console.log("Running transaction!");
    console.log("Changing the greeting to: " + newGreeting);
  }

  async function executeScript() {
    const response = await fcl.query({
      cadence: `
      import HelloWorld from 0x08722b123ca9a185 
  
      pub fun main(): String {
          return HelloWorld.greeting
      }
      `,
      args: (arg, t) => [] 
    })

    console.log("Response from our script: " + response);

    setGreeting(response); //Set the greeting variable to the response of the script call
  } 

  async function executeScript2() {
    const response = await fcl.query({
      cadence: `
      import SimpleTest from 0x6c0d53c676256e8c 
  
      pub fun main(): Int {
          return SimpleTest.number
      }
      `,
      args: (arg, t) => [] // ARGUMENTS GO IN HERE
    })

    setNumber(response)
  }

  useEffect(() => {
    executeScript()
  }, [])

  return (
    <div>
      <Head>
        <title>Emerald DApp</title>
        <meta name="description" content="Created by Emerald Academy" />
        <link rel="icon" href="https://i.imgur.com/hvNtbgD.png" />
      </Head>

      <Nav />

      <main className={styles.main}>
        <h1 className={styles.title}>
          Welcome to my <a href="https://academy.ecdao.org" target="_blank">Emerald DApp!</a>
        </h1>
        <p>Supppppppp</p>

        <div className={styles.flex}>
          <button onClick={runTransaction}>Run Transaction</button>
          <input onChange={(e) => setNewGreeting(e.target.value)} placeholder="Hello, Idiots!" />
        </div>
        <p>{greeting}</p> 
        <div>
          <button onClick={executeScript2}>Read Number</button>
          <p>{number}</p>
        </div>
      </main>
    </div>
  )
}
  ```
  ![Screen Shot 2022-07-15 at 10 46 30 PM](https://user-images.githubusercontent.com/104539205/179337849-9301a145-fb9e-4c4c-b07d-5de184adae08.png)

  
## 2b. Then, I want you to remove the button, and make the script execute every time the page refreshes.
  ``` cadence
  import Head from 'next/head'
import styles from '../styles/Home.module.css'
import Nav from '../components/Nav.jsx';
import { useState, useEffect } from 'react';
import * as fcl from "@onflow/fcl";

export default function Home() {
  const [newGreeting, setNewGreeting] = useState('');
  const [greeting, setGreeting] = useState(''); //Make a new variable named greeting using useState
  const [number, setNumber] = useState('');

  function runTransaction() {
    console.log("Running transaction!");
    console.log("Changing the greeting to: " + newGreeting);
  }

  async function executeScript() {
    const response = await fcl.query({
      cadence: `
      import HelloWorld from 0x08722b123ca9a185 
  
      pub fun main(): String {
          return HelloWorld.greeting
      }
      `,
      args: (arg, t) => [] 
    })

    console.log("Response from our script: " + response);

    setGreeting(response); //Set the greeting variable to the response of the script call
  } 

  async function executeScript2() {
    const response = await fcl.query({
      cadence: `
      import SimpleTest from 0x6c0d53c676256e8c 
  
      pub fun main(): Int {
          return SimpleTest.number
      }
      `,
      args: (arg, t) => [] // ARGUMENTS GO IN HERE
    })

    setNumber(response)
  }

  useEffect(() => {
    executeScript()
  }, [])

  useEffect(() => {
    executeScript2()
  }, [])

  return (
    <div>
      <Head>
        <title>Emerald DApp</title>
        <meta name="description" content="Created by Emerald Academy" />
        <link rel="icon" href="https://i.imgur.com/hvNtbgD.png" />
      </Head>

      <Nav />

      <main className={styles.main}>
        <h1 className={styles.title}>
          Welcome to my <a href="https://academy.ecdao.org" target="_blank">Emerald DApp!</a>
        </h1>
        <p>Supppppppp</p>

        <div className={styles.flex}>
          <button onClick={runTransaction}>Run Transaction</button>
          <input onChange={(e) => setNewGreeting(e.target.value)} placeholder="Hello, Idiots!" />
        </div>
        <p>{greeting}</p> 
        <div>
          <p onClick={executeScript2}></p>
          <p>The number from the contract is: {number}</p>
        </div>
      </main>
    </div>
  )
}
  ```
  ![Screen Shot 2022-07-15 at 10 50 13 PM](https://user-images.githubusercontent.com/104539205/179337974-2eb33a18-d8d0-416c-b1e6-9808d8317207.png)

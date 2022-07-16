# Chapter 4 Day 4 Quests Answers

## 1. I deployed a contract called SimpleTest to an account with an address of 0x6c0d53c676256e8c. I want you to make a button that, when clicked, sends a transaction to change the number variable from that contract. 
![Screen Shot 2022-07-16 at 5 18 08 PM](https://user-images.githubusercontent.com/104539205/179373546-ec5c4399-547b-4232-9d74-24275b1d0980.png)
![Screen Shot 2022-07-16 at 5 19 06 PM](https://user-images.githubusercontent.com/104539205/179373559-aa60b687-21a2-4529-9d85-f2acd9a2c95b.png)

## 2. Immediately after you send the transaction, wait for the transaction to be "Sealed" just like we did today. Then, call a script to read the number from the contract. Console log the result.
![Screen Shot 2022-07-16 at 5 23 53 PM](https://user-images.githubusercontent.com/104539205/179373639-6ae048ca-c427-45f6-9d26-6e485c9a8cdb.png)

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
  const [newNumber, setNewNumber] = useState('');

  async function runTransaction() {
    const transactionId = await fcl.mutate({
      cadence: `
      import HelloWorld from 0x08722b123ca9a185
  
      transaction(myNewGreeting: String) {
  
        prepare(signer: AuthAccount) {}
  
        execute {
          HelloWorld.changeGreeting(newGreeting: myNewGreeting)
        }
      }
      `,
      args: (arg, t) => [
        arg(newGreeting, t.String)
      ],
      proposer: fcl.authz,
      payer: fcl.authz,
      authorizations: [fcl.authz],
      limit: 999
    })
  
    console.log("Here is the transactionId: " + transactionId);

    await fcl.tx(transactionId).onceSealed();
    executeScript();
  }

  async function numberTransaction() {
    const transactionId = await fcl.mutate({
      cadence: `
      import SimpleTest from 0x6c0d53c676256e8c
  
      transaction(number: Int) {
  
        prepare(signer: AuthAccount) {}
  
        execute {
          SimpleTest.updateNumber(newNumber: number)
        }
      }
      `,
      args: (arg, t) => [
        arg(newNumber, t.Int)
      ],
      proposer: fcl.authz,
      payer: fcl.authz,
      authorizations: [fcl.authz],
      limit: 999
    })

    await fcl.tx(transactionId).onceSealed();
    executeScript2();
    console.log("Here is the transactionId: " + transactionId);
    console.log("The current number from the contract is: " + newNumber)
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

    setGreeting(response); //Set the greeting variable to the response of the script call
    //console.log("Response from our original script: " + response);
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

  async function executeScript3() {
    const response = await fcl.query({
      cadence: `
    pub fun main(a: Int, b: String, c: UFix64, d: Address, e: Bool, f: String?, g: [Int],h: {String: Address}): String {
      return b
    }
    `,
    args: (arg, t) => [
      arg("2", t.Int),
      arg("butthole", t.String),
      arg("5.0", t.UFix64),
      arg("0x6c0d53c676256e8c", t.Address),
      arg(true, t.Bool),
      arg(null, t.Optional(t.String)),
      arg([1, 2, 3], t.Array(t.Int)),
      arg(
        [
          { key: "FLOAT", value: "0x2d4c3caffbeab845" },
          { key: "EmeraldID", value: "0x39e42c67cc851cfb" }
        ], 
        t.Dictionary({ key: t.String, value: t.Address })
      )
    ]
    })
    console.log("Chp4Day3 Quest Script: " + response);
  }

  useEffect(() => {
    executeScript()
    executeScript2()
    executeScript3()
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
          <p>The number from the contract is: {number}</p>
        </div>
        <div className={styles.flex}>
          <button onClick={numberTransaction}>Change Number</button>
          <input onChange={(e) => setNewNumber(e.target.value)} placeholder="Enter Number" />
        </div>
      </main>
    </div>
  )
}
```

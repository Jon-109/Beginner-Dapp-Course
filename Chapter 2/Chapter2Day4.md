# Chapter 2 Day 4 Quest Answers

## 1. Change the printHello function to be called runTransaction.

``` cadence
function runTransaction() {
  console.log("Hello there! Jacob is soooooo much cooler than me.")
}
```

## 2. Change the "Hello" text inside the button to "Run Transaction".

``` cadence
<button onClick={runTransaction}>Run Transaction</button>
```

## 3. Inside the runTransaction function, add some code to console log your newGreeting variable to the developer console.
``` cadence
function runTransaction() {
  console.log(newGreeting)
}
```

## 4. Go back to your webpage, type something into the input box, and press "Hello". Open your developer console and you will see some thing being printed!
``` cadence
import { useState } from 'react';
import Head from 'next/head'
import styles from '../styles/Home.module.css'
import Nav from '../components/Nav.jsx'

export default function Home() {
  const [newGreeting, setNewGreeting] = useState('');

  function runTransaction() {
    console.log(newGreeting)
  }

  function printGoodbye() {
    console.log("Goodbye")
  }

  return (
    <div className={styles.container}>
      <Head>
        <title>Emerald DApp</title>
        <meta name="description" content="Created by Emerald Academy" />
        <link rel="icon" href="https://i.imgur.com/hvNtbgD.png" />
      </Head>

      <Nav />

      <main className={styles.main}>
        <h1 className={styles.title}>
          Welcome to my <a href="https://www.google.com" target="_blank">Emerald DApp!</a>
        </h1>
        <p>Sup my dudes</p>

        <div className={styles.flex}>
          <button onClick={runTransaction}>Run Transaction</button>
          <input onChange={(e) => setNewGreeting(e.target.value)} placeholder="Hello, Idiots!" />
        </div>
       
      </main>
    </div>
  )
}
```

![Screen Shot 2022-07-11 at 3 31 24 PM](https://user-images.githubusercontent.com/104539205/178352830-0b5ae482-3e5f-496e-836f-3fa54a6b42da.png)

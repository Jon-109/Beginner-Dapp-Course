# Chapter 2 Day 3 Quests Submission

## 1. In this part, we will be adding another button and changing up some styling.

- Wrap the button tag we added inside of a div. Add a className called styles.flex to that div. Make sure the button is inside of it.
- Then, add another button inside the div tag and put "Goodbye" inside of it.
- In ./styles/Home.module.css, add a new style for the "flex" class, and inside of it, add one line: display: flex.
- Your page should now look like this:
![image](https://user-images.githubusercontent.com/104539205/178342052-a62ebbcf-797e-49d7-9aa5-c43439065a4d.png)

### Answer:
``` cadence
<div className={styles.flex}>
  <button onClick={printHello}>Hello</button>
  <button>Goodbye</button>
</div>
```
![Screen Shot 2022-07-11 at 2 38 21 PM](https://user-images.githubusercontent.com/104539205/178344688-f05f28be-e92b-416d-b143-1d8c7631cb41.png)
![Screen Shot 2022-07-11 at 2 40 41 PM](https://user-images.githubusercontent.com/104539205/178345118-da760005-be8a-493b-ac77-fdad651c5a48.png)

## 2. Now we're going to add an action to your new button.
- To your second button, add an onClick handler and call a function named printGoodbye.
- Define a new function called printGoodbye under the printHello function
- Make it console.log "Goodbye"

### Answer:

``` cadence
import Head from 'next/head'
import styles from '../styles/Home.module.css'

export default function Home() {
  function printHello() {
    console.log("Hello there! Jacob is soooooo much cooler than me.")
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

      <main className={styles.main}>
        <h1 className={styles.title}>
          Welcome to my <a href="https://www.google.com" target="_blank">Emerald DApp!</a>
        </h1>
        <p>Sup my dudes</p>

        <div className={styles.flex}>
          <button onClick={printHello}>Hello</button>
          <button onClick={printGoodbye}>Goodbye</button>
        </div>
       
      </main>
    </div>
  )
}
```
![Screen Shot 2022-07-11 at 2 43 28 PM](https://user-images.githubusercontent.com/104539205/178345536-3c893162-1708-4274-8a24-087b22276885.png)

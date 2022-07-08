# Chapter 2 Day 2 Quests Submission 

## 1. Change the color of "Emerald DApp" to whatever color you want

``` cadence 
.main {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.title {
  font-size: 50px;
}

.title a {
  color: #e83535;
  text-decoration: none;
}
```
![Screen Shot 2022-07-08 at 3 23 27 PM](https://user-images.githubusercontent.com/104539205/178065205-68105075-44ae-4fc8-bc72-898cdf52dcc9.png)


## 2. Change the font size of the title
``` cadence 
.main {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.title {
  font-size: 75px;
}

.title a {
  color: #e83535;
  text-decoration: none;
}
```
![Screen Shot 2022-07-08 at 3 24 33 PM](https://user-images.githubusercontent.com/104539205/178065315-2eca9698-3209-4837-b1e2-f88648a97aec.png)
(it's bigger i promise)

## 3. Change the "Emerald DApp" link to a different link (this means messing with the <a> tag)

  ``` cadence
  import Head from 'next/head'
import styles from '../styles/Home.module.css'

export default function Home() {
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
      </main>
    </div>
  )
}
  ```
  
  ![Screen Shot 2022-07-08 at 3 26 09 PM](https://user-images.githubusercontent.com/104539205/178065507-e330c9d3-c90e-405b-874b-a44ba2b01e10.png)
^^ proof it worked lol
  
## 4. Inside of your <main> tag, add a <p> tag and put whatever text you want in it. The box model will look like this:
![image](https://user-images.githubusercontent.com/104539205/177877946-1924849f-2445-4fbf-bd19-f955bae7ff40.png)
  
  ``` cadence
  
      <main className={styles.main}>
        <h1 className={styles.title}>
          Welcome to my <a href="https://www.google.com" target="_blank">Emerald DApp!</a>
        </h1>
        <p>Sup my dudes</p>
      </main>
  ```
  ![Screen Shot 2022-07-08 at 3 29 27 PM](https://user-images.githubusercontent.com/104539205/178065918-63a2a704-5dc6-4606-9930-79f8b08d6754.png)

## 5. Go to the .main class and add this line: flex-direction: column. Watch what it does! Take a screenshot of your changes (both the code and the result) and upload it to your quests
``` cadence 
  .main {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
```
  
  ![Screen Shot 2022-07-08 at 3 30 40 PM](https://user-images.githubusercontent.com/104539205/178066052-b65abd2b-0a77-45d9-be7e-e1dab966096e.png)

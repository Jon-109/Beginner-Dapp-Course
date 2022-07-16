# Chapter 4 Day 3 Quests Answers

## 1. Write a function that executes a script with all the Cadence types that we reviewed today. Call the script when the page refreshes. Return something random from the Cadence script, and console log it to prove to me your script actually worked.
``` cadence

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


```
![Screen Shot 2022-07-16 at 4 07 48 PM](https://user-images.githubusercontent.com/104539205/179371941-0434b37c-7176-4f74-99f1-ffd5eff97222.png)

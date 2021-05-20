# Geny Commands

Geny is a command based system, that means that every main functions can be called with a command

A command in Geny looks like this :

```javascript
    // in shorthand
    "openWin:about"
```

```javascript
    // in longhand
    {
        opcode: "openWin",
        args: {
            win: "about"
        }
    }
```

these two commands have the same result, but are used in different ways,
 - one is short, meaningful and easy to write, but can handle only one text argument
 - the other one is extensible, can contains a lot of different information, but is really verbose

These two way of executing commands are complementary, one isn't better than the other

So, what a command is used for ?

Mostly to let every part of Geny communicate and making function call

E.g. : When the Game Master want to roll a dice, he presses a button that call a function that send a command to the API, that looks like this :

```javascript
    // in longhand
    {
        opcode: "newOrder",
        args: {
            to: [
                
            ]
            cmd: {
                opcode: "rollDice",
                args: {
                    min: 1,
                    max: 100,
                    result: 94
                }
            }
        }
    }
```

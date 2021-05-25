# A Command-Based System

---

Geny is a command-based system, that's means that every main functions can be called with a "command"

## Command Principle

What's considerated as "main function" is a bit obscure, but it's like `openWin`, `rollDice` or `playSound`, it's an action (open, roll, play) and a complement (win, dice, sound) a command has to serve one goal and only. If you want to create a package and use commands, It's advised to check out **Style Guide!! add chap**

A command in Geny looks like this :

```json
// in shorthand
"openWin:about"
```

```json
// in longhand
{
    "opcode": "openWin",
    "args": {
        "win": "about"
    }
}
```

As you can see, there is two way of write a command, they have the same result, but are used for different purpose :
 - one is **short**, meaningful and easy to write, but can **handle only one** text argument
 - the other one is **extensible**, can contains a lot of different information, but is **really verbose**

These two way of executing commands are complementary, one isn't better than the other

### What's Inside

A command needs an **`opcode`**, for operation code, it tells what operation it is. It's a short string like `rollDice` or `toggleCmdPannel`
And for some command (a majority) it contains `args`, another top-level key to specify some details about the operation it the `win` argument for `openWin`, or `result` for `rollDice`

The arg key is up to the command, each commands have their own arg requirements

## For what usage

The main purpose of this system is to let ways to communicate between clients, it's easier to transfer, verify and execute a text based *function call*, it's a clean and formatted way to call function. It's also waaay better than passing "Geny.function({..})" as text through network and execute with eval, because it's ugly and .. eval

For example : when the Game Master want to roll a dice :

- He presses a key that calls `Geny.execute("askDice"})`
- `askDice` asks what dice would the game master throw (min and max), when it's done, it choose a random number and it sends a command `newOrder` to the API through network containing `rollDice`
- API execute `newOrder` and does API stuffs
- API get back to all clients (Master (**m**) and Viewer (**v**)) with the command `rollDice`
- Clients execute `rollDice` and shows rolling dice on screen

The `newOrder` command looks like this :

```json
{
    "opcode": "newOrder",
    "args": {
        "cmd": {
            "opcode": "rollDice",
            "args": {
                "min": 1,
                "max": 100,
                "result": 94
            }
        }
    }
}
```

## Two Formats

As said earlier there is two way of writing commands, the short one, and the long one

Each has pros and cons, here is the chapter to talk about these

### Shorthand Command

Example :

```json
"openWin:preferences"
```

```json
"rollDice:76"
```

```json
"askSound"
```

As you can see, even with low capability, you can already use it in a lot of context, you can use it with normal format, `opcode:arg` where arg can be a string or numeric (still a string of course) or even no arguments

The regex used for validation is this one : `/^[A-z]+(:[A-z0-9]+)?$/`

So :
 - Have to contain an opcode (only ascii letters)
 - Can contains a `:` but if so :
    - It needs to also contains an argument (any alphanumeric string)

### Longhand Format

The longhand format is the other command format

Example :

```json
{
    "opcode": "playSound",
    "args": {
        "channel": 0,
        "path": "/assets/packages/core/soundBoard/sounds/joyful_tavern.mp3"
    }
}
```

```json
{
    "opcode": "showText",
    "args": {
        "text": "L´innocence n´existe pas, il n´y a que des degrés de culpabilité."
    }
}
```

There is only one top level key needed : it's `opcode` and `arg`, the last one can be omitted if command doesn't needs it

This is, as shown, in a JSON format for transfer, storage, and in a JS object when executed

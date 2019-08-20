
# Shell scripting


A shell script is a computer program designed to be run by the interpreter, be it UNIX-like shell of the operating system or for example node. It often uses other programs to work together


---

## Features:
- useful for automation
- does not have a GUI
- batch jobs
- does not neccessary require user interaction 

---


## Piping

`cat file1.js file2.js | sort | uniq `


---

```shell=
#!/bin/bash
DIR=$(pwd)
cd ~/git
REPOS="abulafa buslonbus creocodicem crianonim.github.io echoserver fac-calculator game-gra kajet ktos listonosz ocki rozmowa rozmowa-ui screept tytubka learningGitHub"
for REPO in $REPOS; do

    if [ ! -d ~/git/$REPO ]; then
        echo "REPOSITORY $REPO doesn't exitst locally. Will clone";
        git clone "git@github.com:crianonim/${REPO}.git" ~/git/"$REPO"
    else
        echo "GIT PULL/PUSH repo $REPO"
        cd "$REPO"
        git pull
        git push
        cd ~/git
    fi
done;
cd "$DIR"

```

---


# What does the program do?

<!-- take stdoutput from tape, and process it using our formatter file. -->
- The program takes standard output (stdout) from tape.
- It then formats the data, making it easily readable and (maybe) aesthetically pleasing. It can do things such as tally passed, failed and total tests, print ASCII art and change the font and background colours.
- It then prints the formatted data to the terminal.

---

# Stdin consumes inputs
 
 "Generally standard input, referred to as "stdin", comes from the keyboard but it also allows you take standard input from a file."


--- 



## keyboard input 


```
node index.js

```


--- 


## file redirection 

```
index.js < file1.txt
```


--- 


## pipe output from other process 

```
tape test.js | node index.js
``` 

---

# How our program tallies passing and failing tests 

- We have initialised a readline interface which reads the input as a stream from process.stdin
```javascript=
const rl = readline.createInterface({
  input: process.stdin,
  terminal: false
});
```

---


- The readline interface emits a 'line' event whenever it finishes reading a line from the input stream
- we have set up an 'event listener' for this event

---

```javascript=
rl.on('line',(lineStr)=>{
    // console.log(lineStr);
    if (lineStr.startsWith("ok")  ){
        passedCount+=1;
        testCount+=1;
    } else if (lineStr.startsWith("not ok")){
        failedCount++;
        testCount++;
    }
})
```

- This checks if the line starts with 'ok' or 'not ok' and updates the passed/ failed/ total counters accordingly

---

- the `rl.on()` function is asynchronous, so any code after it will not wait for the stream to finish.
- we should only output once the stream closes
```javascript=
rl.on('close',()=>{
    if (failedCount){
        console.log(cowsay.say({T:"U",e:"XX",text:`NOOOOOOOB
${failedCount} Failed!`}));
        console.log()
    } else {
        console.log(cowsay.say({e:"OO",text:"GOOOOOOOD"}));
        console.log("All passed");
    }
    console.log(`TESTS Passed:${passedCount}, Failed:${failedCount}, Total:${testCount}`)
})
```

---

# Node Shell

![](https://i.imgur.com/zXiuAjC.gif)

## What is Shell Scripting

---

writing things on a seashell :D

![](https://i.imgur.com/brKEjJu.jpg)

(its actually writing custom commands to be used in your terminal)

### What is a shell

Simply put, the shell is a program that takes commands from the keyboard and gives them to the operating system to perform. In the old days, it was the only user interface, but now we have GUIs as well.

### Shell scripts

A shell script is a computer program designed to be run by the interpreter, be it UNIX-like shell of the operating system or for example node.

In the simplest terms, a shell script is a file containing a series of commands. The shell reads this file and carries out the commands as though they have been entered directly on the command line.

A distinct feature of a shell script is that it does not provide GUI, it runs 'in the shell', and can be invisible (and often is), often not requiring any interaction after initial setup.

They can use the standard output and input to interact with files and other processes (that can be shell scripts)

#### piping
There is a tradition in UNIX world to create small programs that do one thing, and do that thing very well. You then script them together in a shell script to achieve complex functionality:

`cat file1.js file2.js | sort | uniq `

Concatenates the file1.js file2.js into one text then pipes that to `sort` that sorts the lines alphabetically and then passes that to `uniq` eliminates duplicating lines

### What can it be useful for

#### Creating shortcuts
You can create a script that contains other commands with some presets, maybe some setup so it would be enough to run a shell script and have the whole functionality there

#### Batch jobs
You can create a script with series of commands that need to be performed sequentially. Ie. Download files, compress them, save them in remote backup

#### Automation
You might want to have some commands run at specific times of the day or when some events happen and not require user interaction




## Test Output Formatter Steps

## 1. Take output from tape
```
# Description for your test
ok 1 just testing everything works
# Simple values, number, strings, booleans
ok 2 should be equal
ok 3 should be equal
ok 4 should be equal
# Complex values - objects and arrays
ok 5 should be equivalent
ok 6 should be equivalent
# Truthy and falsy
ok 7 should be truthy
ok 8 should be falsy
ok 9 should be falsy
# Async testing
ok 10 should be equal
ok 11 should be equal
# Error handling
ok 12 should throw
ok 13 should be equal

1..13
# tests 13
# pass  13

# ok
```

using the | command automatically passes the output from tape as the input for our formatter file

```
test: "tape test.js | node output-formatter.js"
```

```
test: node test.js | tap-spec
```

add this to package.json under scripts

## 2. Process this text and prettify it

1. Number of passing tests
2. Number of failing tests
3. display which tests are failing
4. display cute ascii art



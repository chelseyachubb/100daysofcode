# 100daysofcode
I'm creating this to document my work on 100 days of code.

I'll be using the following tools:
- [Code Academy](http://codeacademy.com)
- [Zappy](https://zapier.com/zappy)

### Day 6 The terminal	

I've used the terminal/command line in quite a few roles, but my knowledge of the terminal is very minimal. I basically only have known how to do the exact things I needed to do, such as checking DNS records using DIG, like this:

![dig](https://cdn.zappy.app/56c4bfd683d25601683952e93b91b75a.png)

That said, I've found it super useful so I was excited to dive into the terminal/command line for today's code academy lesson. The coolest thing I learned today is how much flexibility you actually can get by using the commandline. You can write scripts, automate tasks, create directories, and *most* importantly, it's green and black so it *feels* like you're Keanu Reeves in the Matrix. Okay maybe not but whatever.

The first thing I learned was to use the shell prompt, a simple $. If I wanted to then give a command to look at all the folders in the directory I am in at any given time, and list them, I would use the command 

$ ls 

If we wanted to then print the working directory , easy, 

pwd

If you want to navigate through directories, you can use cd, change directory. So if I were in my documents and wanted to navigate to pictures I could use 
cd pictures

When I pass a file or directory into a command in the terminal, similar to what I learned in passing specific values through in Javascript, it's called an argument. You can _literally_ browse all of your files and create organized directories _right_ through the terminal. This is what I've needed all of my life. ORGANIZATION!

all you use is pwd to confirm where you are, and cd to change directories. 

Then it gets better. 

touch

Touch will create a file. 

So if I am in a specific directory aka folder, and I want to create a txt file called hello, 

touch hello.txt

![hello.txt](https://cdn.zappy.app/873bafbe41d9a703c39ed5b267c3b870.png)

Nifty, right!? 

The touch command creates a new file in the directory, it'll take the filename as the argument and then create an empty file. Stellar. 

And that's really what I worked on today, short and sweet, the five most common commands in the Terminal:

- pwd outputs the name of the current working directory.
- ls lists all files and directories in the working directory.
- cd switches you into the directory you specify.
- mkdir creates a new directory in the working directory.
- touch creates a new file inside the working directory.


### Day 5: Magic Eight Ball

Today was short and sweet, I used some of the concepts I've learned so far to create a magic eight ball! This was one of the codeacademy challenges. Here's what I came up with: 

```javascript
let userName = ''
if (userName) {
  console.log `Hello ${userName}`
} else {
  console.log('Hello!')
};
const userQuestion = 'Will I lose something this weekend?';
console.log(userQuestion);
const randomNumber = Math.floor(Math.random()*8);
console.log(randomNumber);
let eightBall = '';

switch(randomNumber) {
  case 0:
  console.log('It is certain');
  break;
  case 1:
  console.log('It is decidedly so')
  break;
  case 2:
  console.log('Reply hazy, try again')
  break;
  case 3:
  console.log('Signs point to yes')
  break;
  case 4:
  console.log('Cannot predict now')
  break;
  case 5:
  console.log('Yeah Yeah, it aint gonna happen')
  break;
  case 6: 
  console.log('Signs point to yes')
  break;
  case 7: 
  console.log('Signs point to WHY ARE YOU TRUSTING A MAGIC EIGHT BALL')
  break;
  case 8:
  console.log('nope.never.not gonna happen.')
  break;
default:
  console.log('Do not count on it')
}

```

Today was not so much about learning so much as it was about practicing and digesting. I felt like I have started to get the concepts and especially like switch statements probably because I understand them. I had a bit of fun with this one!


### Day 4: Scope

Today I spent time learning more than building, which is good. I'm building on concepts I've learned by learning more, so I guess technically I _am_ building. I already have a lot of familiarity with scope, so I felt this was a breeze. Global scope means a variable is declared _outside_ of a function, and can be accessed by any code in the program. For example, 

```javascript
const city = 'New York City';
const logCitySkyline = () =>{
  let skyscraper = 'Empire State Building';
    return 'The stars over the ' + skyscraper + ' in ' + city;
}
console.log(logCitySkyline())
```
city is a global variable. Simple Enough. It seems like you would want to just make everything global, but alas, _code isnt that simple!_. I learned a ton about good practice and scope pollution. 

I learned to recreate an example of _bad_ scope, here:
``` javascript
let num = 50;//we've declared a global variable here

const logNum = () => {
  num = 100; //see. this is reassigning the 50 to 100, but its a global variable. this can make the code funky.
  console.log(num);
};

logNum(); 
console.log(num); 
```

As well as good scope, _here_, because it declares the variables inside the function and reassigns them, rather than declaring a global variable and then declaring that same variable with a different value inside of the function:

```javascript
const logVisibleLightWaves = () => {
  let lightWaves = 'Moonlight';
	let region = 'The Arctic';
  if(region === 'The Arctic'){
    let lightWaves='Northern Lights'
    console.log(lightWaves);
};
```
I spent the rest of my hour of code _learning_ and reviewing the previous days concepts, since the two projects I did the two previous days have weighed on me heavily. Before I jump into coding tomorrow, I want to review, rewrite and continue to digest the following topics:
- Conditionals
- Functions 
- Scope
- Variables
- Error Handling


### Day 3: Sleep Debt Calculator

For day 3 I built a program that took my actual sleep per night and my ideal sleep per night and calculated if I am getting enough sleep. After doing most of the same work yesterday, today I felt way more confident and was able to write this on the second try! The only issue I experienced was syntax, I had a rogue { that I could not spot for the life of me. Thanks to JS hint, I was able to find it a bit more quickly, but the below program takes each nights hourly sleep, then it takes my ideal sleep per week. It then calculates if I am getting enough, too much, or not enough sleep, and if not enough sleep it outputs my sleep debt. I'm rocking 15 hours of sleep debt this week, per usual.

``` javascript
const getSleepHours = day =>{
switch(day){
  case 'monday':
    return 7
    break;
  case 'tuesday':
    return 6
    break;
  case 'wednesday':
    return 6
    break;
  case 'thursday':
    return 8
    break;
  case 'friday':
    return 10
    break;
  case 'saturday':
    return 10
    break;
  case 'sunday':
    return 7
    break;
  default:
  return 7
}
};
const getActualSleepHours = () =>
 getSleepHours('Monday') +
 getSleepHours('Tuesday') + 
 getSleepHours('Wednesday') + 
 getSleepHours('Thursday') + 
 getSleepHours('Friday') + 
 getSleepHours('Saturday') + 
 getSleepHours('Sunday');

const getIdealSleepHours = () => {
  idealHours = 8
  return idealHours * 8
}

const calculateSleepDebt = () =>{
  actualSleepHours = getActualSleepHours()
  idealSleepHours = getIdealSleepHours()
  if (actualSleepHours === idealSleepHours) {
    console.log('You got the perf amount of sleep!')
} else if (actualSleepHours > idealSleepHours){
  console.log('you got a lil too much sleep') 
}
  else {
  console.log('you did not get enough sleep, your sleep debt is'+(actualSleepHours - idealSleepHours));
  }
}
console.log(calculateSleepDebt());
```


## Day 2: Rock, Paper, Scissors

For day 2, I am applying what I've learned about basic js api, functions, and conditional statements to create a game of rock, paper, scissors.


Our code will break the game into four parts:
1.  Get the user’s choice.
2. Get the computer’s choice.
3. Compare the two choices and determine a winner.
4. Start the program and display the results.

Here are the rules:
The possible outcomes are:  
- Rock destroys scissors
- Scissors cut paper
- Paper covers rock
- If there’s a tie, then the game ends in a draw

### Get the user's choice

First I need to get the users choice, so I create a function that takes user input, called 'getUserChoice'. Since a user might type in all caps, no caps, or capitalized, I want to make sure things are consistent, so I use the .toLowerCase() method to make sure the entire word is in lower case. I also want to check that the user actually input rock or paper or scissors, so I check to make sure they did and output an error if they did not

```javascript
const getUserChoice = userInput => {
  userInput = userInput.toLowerCase();// make it consistently all lowercase
  if (userInput === 'rock' || userInput === 'paper' || userInput === 'scissors') { //make sure the input is rock/paper/scissors
    return userInput
  } else {
    console.log('Error. Please type rock paper or scissors') //if it's not rock/paper/scissors output error message

  }
}
```

I can test to make sure this code is correct by trying the following:

``` javascript
console.log(getUserChoice('paper')); //this tests to make sure paper is properly output, and in lowercase
console.log(getUserChoice('testing')); //this tests to make sure the error message appears
```

### Get Computer's Choice

Next I need to get a computer choice. To do this, I can use a combination of Math.random(), Math.Floor() and switch or if else statements. First I'll start by declaring a function called getComputer Choice, and then I will use Math.random()* 3, to get a number between 1-3. I multiply by 3 because Math.random will return a number between 0 and .99, and I use Math.floor because I want an even number between 1 and 3, not 1.2343545 for example. 

``` javascript
const getComputerChoice = () => {
    const randomNumber = Math.floor(Math.random()* 3);
}
```
Now that I have the random number, I need to determine whether the number is equal to rock, paper or scissors. I _could_ achieve this with an if/else but I could also make it slightly cleaner using a switch statement, like this:
``` javascript
const getComputerChoice = () => {
  const randomNumber = Math.floor(Math.random()* 3);
  switch(randomNumber) {
    case 0 : 
      return 'rock';
      break;
    case 1: 
      return 'paper';
      break;
    case 2: 
      return 'scissors';
      break;
  }
};
```
I can test this by using console.log, like this:

``` javascript
console.log(getComputerChoice());
```

To see that I get a value of paper,rock or scissors. 

### Determining who won

So far I've set the stage for the user's choice, and the computers choice, and the next part is to compare them. This is the part I struggled on most. I was following if else statements all the way up until they were nested. I was trying to compare too many values at once. In other words, I was trying to take every scenario and nest it, instead of simplifying. So I took a little bit of space away from the problem and read up on nested ifs and it turns out it's relativly simple. 

If the user has rock and the computer has paper, the computer wins, otherwise, the user wins. There's only two options. This was a major facepalm but here was my resulting code;

```javascript
const determineWinner = (userChoice,computerChoice) => {
  if (userChoice === computerChoice) {
    return 'Tie game!'
  } 
  if(userChoice === 'rock') {
    if(computerChoice === 'paper') {
      return 'Sorry, computer won' //if the first and second condition are true, return 'you computer won' otherwise, return 'you won'
    } else {
      return 'congrats, you won!';
    }
  }
  if(userChoice === 'paper') {
    if(computerChoice === 'scissors') {
      return 'Computer won!'
    } else {
      return 'You won!'
    }
  }
  if (userChoice === 'scissors') {
    if(computerChoice === 'paper') {
      return 'You won!' 
      } else {
        return 'Computer won wah wah!'
      }
    }
  };
```

### Putting all the pieces together

The last part I had to complete was to create a function called playGame, which logs what the user and computer threw, as well as who won. Here's the final bit:
```javascript
const playGame = () => { //declaring the function
   const userChoice = 
getUserChoice('scissors'); //setting users choice to scissors
   const computerChoice = 
getComputerChoice(); //getting computer choice using the code created earlier
   console.log('You threw: ' + userChoice); //logging users choice
   console.log('The computer threw:' + computerChoice);// logging computers choice
   console.log(determineWinner(userChoice, computerChoice)); //logging winner!
};

playGame(); //initiating game
```

Here's the final code for the full game: 
``` javascript
const getUserChoice = userInput => {
  userInput = userInput.toLowerCase();// make it consistently all lowercase
  if (userInput === 'rock' || userInput === 'paper' || userInput === 'scissors'|| userInput === 'bomb') {
    return userInput;
  } else {
    console.log('Error. Please type rock paper or scissors')

  }
};

const getComputerChoice = () => {
  const randomNumber = Math.floor(Math.random()* 3);
  switch(randomNumber) {
    case 0 : 
      return 'rock';
      break;
    case 1: 
      return 'paper';
      break;
    case 2: 
      return 'scissors';
      break;
  }
};

const determineWinner = (userChoice,computerChoice) => {
  if(userChoice === 'bomb'){
    return 'hot dang, it\'s a bomb, you win!'
  }
  if (userChoice === computerChoice) {
    return 'Tie game!'
  } 
  if(userChoice === 'rock') {
    if(computerChoice === 'paper') {
      return 'Sorry, computer won'
    } else {
      return 'congrats, you won!';
    }
  }
  if(userChoice === 'paper') {
    if(computerChoice === 'scissors') {
      return 'Computer won!'
    } else {
      return 'You won!'
    }
  }
  if (userChoice === 'scissors') {
    if(computerChoice === 'paper') {
      return 'You won!' 
      } 
        else {
        return 'Computer won wah wah!'
      }
    }
  };
const playGame = () => {
   const userChoice = 
getUserChoice('bomb');
   const computerChoice = 
getComputerChoice();
   console.log('You threw: ' + userChoice);
   console.log('The computer threw:' + computerChoice);
   console.log(determineWinner(userChoice, computerChoice));
};

playGame();
```

### Learnings:

1. Following along is not the same thing as understanding. I got all the way to this project by following along, but once I put it into action, I didn't understand. This made me go back several times and figure out the why behind each function and code block.
2. Breaks are important. Take small bite sized chunks and then learn about those, and then use those like little legos to build.
3. Starting from Scratch is exhausting! 

## Day 1 : Functions

I'm starting a bit in the middle of my learning journey, so my first day will reflect that pretty heavily. So far I've been working on Codeacademy's Create a Backend App with JS, [here](https://www.codecademy.com/learn/paths/create-a-back-end-app-with-javascript).
Here's what I'm covering today:
- Parameters 
- Arguments
- Default Parameters
- Return
- Helper Functions
- Arrow Functions
- Concise Body Arrow Functions

Codeacademy provides super helpful 'cheatsheets', here's the functions cheatsheet for my lessons today [Functions](https://www.codecademy.com/learn/paths/create-a-back-end-app-with-javascript/tracks/bapi-javascript-conditionals-and-functions/modules/learn-javascript-functions/cheatsheet)

Functions are just reusible blocks of code that performs a specific task. For example:

```javascript
function greetWorld() {
  console.log('Hello, World!');
}
```
I also learned _bad_ practice, aka hoisting. I'm sure I'll make this mistake a few times, but we shouldn't be calling a function before it's defined. So for example, calling console log before the function is not great. 

```javascript
console.log(greetWorld()); //this is bad practice!

function greetWorld() {
consol.log('Hello World!');
}
```

That's pretty basic code. But we can also add parameters. Parameters allow the function to accept input, and act like variables within a function. This allows you to call a function over and over with different inputs. I'm a visual learner, so mapping things out like this helps:

![Parameters](https://cdn.zappy.app/463810aea70a426ab8294016d7eee43e.png)

Then, we'll pass through an argument, which is the specific values or variables passed to the function, for example:

```javascript
calculateArea(10,6);
```
Return
I don't quite grasp return. What I do understand is that by default a function runs the code but then...still results in the value as undefined..unless you use return? What I understand is that unless you use return, the function will run but won't output the correct information. I'm spending a bit more time reading on return to ensure I really grasp this one.

For a boring way to practice, I created a function to detect how many cells are in a specific Google Sheet. Say I have 4 rows and 5 columns:
![sheets]:(https://cdn.zappy.app/7757d593befe499d63744bc66bad78fa.png)

I could count by hand, or I could use this function:

```javascript
function cellCount(rows,columns){
  return rows * columns
}
const numOfcells = cellCount(5, 4);
console.log(numOfCells);
```

What if each Cell had the value 100, and I wanted to calculate the value of all cells combined? I could use a helper function for that! 

``` javascript
function cellCount(rows, columns) {
  return rows * columns;
}
function valueOfCells(rows,columns){
  return cellCount(rows,columns)*100
}
const totalValue = valueOfCells(5,4);
console.log(totalValue)
```

I also learned about Function expressions, which are an alternative way to define a function. So for example like this:
![function expression](https://cdn.zappy.app/ed16c2fdacc1e2e2d29caffe1e9652e2.png)

Instead of this:
![function](https://cdn.zappy.app/6a6fb6b82176c5dfc7e7345fbab91c10.png)

And then we can get even more concise by using arrow functions, like this:  


![function arrows](https://cdn.zappy.app/6a7fe0daaa2fa4f796cc5387216e56a4.png)

This is pretty basic, and a lot of simple learnings here, without a lot of building, but writing it out is helping it stick, so I'm very excited for DAY 2! 

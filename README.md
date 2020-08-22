# 100daysofcode
I'm creating this to document my work on 100 days of code.

I'll be using the following tools:
- [Code Academy](http://codeacademy.com)
- [Zappy](https://zapier.com/zappy)
- [Glitch](https://glitch.com)

Here's my twitter @chelseyachubb


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
For a boring way to practice, I created a function to detect how many cells are in a specific Google Sheet. Say I have 4 rows and 5 columns:
![sheets]:(https://cdn.zappy.app/7757d593befe499d63744bc66bad78fa.png)

I could count by hand, or I could use this function:

'''javascript
function cellCount(rows,columns){
  return rows * columns
}
const numOfcells = cellCount(5, 4);
console.log(numOfCells);
```

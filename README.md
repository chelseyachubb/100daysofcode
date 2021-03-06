# 100daysofcode
I'm creating this to document my work on 100 days of code.

I'll be using the following tools:
- [Code Academy](http://codeacademy.com)
- [Zappy](https://zapier.com/zappy)

**Please note that this is my 100 days of Code, and anything in here may be incorrect or subject to..be able to be done better. This is my journey ya'll**

### Day 15 - Mini-Linter Project

I took a bit of a hiatus from 100 days of code, but not necessarily from code, as Ive been working internally on some projects with my technical mentor, so I might argue that I likely did _more_ code but wrote about it less. That said, I'm picking it back up because writing about what you do helps think through why you're doing what you're doing! Today I created a mini-linter, to practice iterating over an array!

First I was given the following:
```javascript
let story = 'Last weekend, I took literally the most beautiful bike ride of my life. The route is called "The 9W to Nyack" and it actually stretches all the way from Riverside Park in Manhattan to South Nyack, New Jersey. It\'s really an adventure from beginning to end! It is a 48 mile loop and it basically took me an entire day. I stopped at Riverbank State Park to take some extremely artsy photos. It was a short stop, though, because I had a really long way left to go. After a quick photo op at the very popular Little Red Lighthouse, I began my trek across the George Washington Bridge into New Jersey.  The GW is actually very long - 4,760 feet! I was already very tired by the time I got to the other side.  An hour later, I reached Greenbrook Nature Sanctuary, an extremely beautiful park along the coast of the Hudson.  Something that was very surprising to me was that near the end of the route you actually cross back into New York! At this point, you are very close to the end.';

let overusedWords = ['really', 'very', 'basically'];

let unnecessaryWords = ['extremely', 'literally', 'actually' ];
```
eek. in order to iterate over it, I need the story to be in array form first! I can do that by creating an array called storyWords, like this:
```javascript
let storyWords = story.split(' ');
```
To make sure I did it right, I always use console.log,
```javascript
let storyWords = story.split(' ');
console.log(storyWords);
```

![storywordarray](https://cdn.zappy.app/4ac53fbe5b25370e49547bdf13e6a764.png)

Right on! 

Next, let's log the total words before we iterate over the array using the uneccessaryWords and overusedWords. To do that I'd just update my console.log(storyWords) to:

```javascript
console.log(storyWords.length);
```

Wala, 188 words!

Now, if I want to know how many times I used the words really, basically and very, I could do something like this:
```javascript
let story = 'Last weekend, I took literally the most beautiful bike ride of my life. The route is called "The 9W to Nyack" and it actually stretches all the way from Riverside Park in Manhattan to South Nyack, New Jersey. It\'s really an adventure from beginning to end! It is a 48 mile loop and it basically took me an entire day. I stopped at Riverbank State Park to take some extremely artsy photos. It was a short stop, though, because I had a really long way left to go. After a quick photo op at the very popular Little Red Lighthouse, I began my trek across the George Washington Bridge into New Jersey.  The GW is actually very long - 4,760 feet! I was already very tired by the time I got to the other side.  An hour later, I reached Greenbrook Nature Sanctuary, an extremely beautiful park along the coast of the Hudson.  Something that was very surprising to me was that near the end of the route you actually cross back into New York! At this point, you are very close to the end.';

let overusedWords = ['really', 'very', 'basically'];

let unnecessaryWords = ['extremely', 'literally', 'actually' ];

let storyWords = story.split(' '); 
// console.log(storyWords);
//console.log(storyWords.length)

let betterWords = 
storyWords.filter(function(word){
return !unnecessaryWords.includes(word)
})

let reallyCount = 0
let veryCount = 0
let basicallyCount = 0

for (word of storyWords){
  if (word === 'really') {
    reallyCount += 1
  } else if (word === 'very'){
    veryCount += 1
  } else if (word === 'basically'){
    basicallyCount += 1
  }
}


console.log('You used really '+reallyCount+' times')
console.log('You used basically '+basicallyCount+' times')
console.log('You used very ' +veryCount+' times')
```
The output?  

![reallyverybasically](https://cdn.zappy.app/67c11b90726104c4e573778e70e725c7.png). 

Cool.  

Then, if I wanted to count sentences, I could create a function to iterate over how many words end in a period, or exclamation point, because in looking at the paragraph there are no question marks. Here's how I could achieve that:

```javascript
let story = 'Last weekend, I took literally the most beautiful bike ride of my life. The route is called "The 9W to Nyack" and it actually stretches all the way from Riverside Park in Manhattan to South Nyack, New Jersey. It\'s really an adventure from beginning to end! It is a 48 mile loop and it basically took me an entire day. I stopped at Riverbank State Park to take some extremely artsy photos. It was a short stop, though, because I had a really long way left to go. After a quick photo op at the very popular Little Red Lighthouse, I began my trek across the George Washington Bridge into New Jersey.  The GW is actually very long - 4,760 feet! I was already very tired by the time I got to the other side.  An hour later, I reached Greenbrook Nature Sanctuary, an extremely beautiful park along the coast of the Hudson.  Something that was very surprising to me was that near the end of the route you actually cross back into New York! At this point, you are very close to the end.';

let overusedWords = ['really', 'very', 'basically'];

let unnecessaryWords = ['extremely', 'literally', 'actually' ];

let storyWords = story.split(' '); 
// console.log(storyWords);
//console.log(storyWords.length)

let betterWords = 
storyWords.filter(function(word){
return !unnecessaryWords.includes(word)
})

let reallyCount = 0
let veryCount = 0
let basicallyCount = 0

for (word of storyWords){
  if (word === 'really') {
    reallyCount += 1
  } else if (word === 'very'){
    veryCount += 1
  } else if (word === 'basically'){
    basicallyCount += 1
  }
}

let sentenceCount = 0

for(word of storyWords) {
  if(word[word.length - 1] ==='.' || word[word.length - 1] === '!') {
    sentenceCount += 1
  }
}
console.log(sentenceCount);

```

...and the answer issss 12 which I also tested by literally manually counting, boom! 

Finally, to return the betterWords in a string without the unnecessary words, I could write something like this:
```javascript
let story = 'Last weekend, I took literally the most beautiful bike ride of my life. The route is called "The 9W to Nyack" and it actually stretches all the way from Riverside Park in Manhattan to South Nyack, New Jersey. It\'s really an adventure from beginning to end! It is a 48 mile loop and it basically took me an entire day. I stopped at Riverbank State Park to take some extremely artsy photos. It was a short stop, though, because I had a really long way left to go. After a quick photo op at the very popular Little Red Lighthouse, I began my trek across the George Washington Bridge into New Jersey.  The GW is actually very long - 4,760 feet! I was already very tired by the time I got to the other side.  An hour later, I reached Greenbrook Nature Sanctuary, an extremely beautiful park along the coast of the Hudson.  Something that was very surprising to me was that near the end of the route you actually cross back into New York! At this point, you are very close to the end.';

let overusedWords = ['really', 'very', 'basically'];

let unnecessaryWords = ['extremely', 'literally', 'actually' ];

let storyWords = story.split(' '); 
// console.log(storyWords);
//console.log(storyWords.length)

let betterWords = 
storyWords.filter(function(word){
return !unnecessaryWords.includes(word)
})

let reallyCount = 0
let veryCount = 0
let basicallyCount = 0

for (word of storyWords){
  if (word === 'really') {
    reallyCount += 1
  } else if (word === 'very'){
    veryCount += 1
  } else if (word === 'basically'){
    basicallyCount += 1
  }
}

let sentenceCount = 0

for(word of storyWords) {
  if(word[word.length - 1] ==='.' || word[word.length - 1] === '!') {
    sentenceCount += 1
  }
}

var joinWords = betterWords.join();
var finalWords = joinWords.replace(/,/g,' ')
console.log(finalWords)
```

This was one of the challenges I enjoyed most, just because I could see how it would be super helpful to create a linter, either in regular writing, ie papers, emails, books, etc, or in code. I dug it!

That's it for today, here's the final paragraph:
![final](https://cdn.zappy.app/d2f2d40b77ae218d073a05103b5cccc5.png)

### Day 14 Iterators... 

This joke is getting old but again, I practiced iterators! In this code I basically used the prompts to ensure I was using the right method each time for the right scenario using their commented out text, like this:

```javascript
const cities = ['Orlando', 'Dubai', 'Edinburgh', 'Chennai', 'Accra', 'Denver', 'Eskisehir', 'Medellin', 'Yokohama'];

const nums = [1, 50, 75, 200, 350, 525, 1000];

//  Choose a method that will return undefined
cities.forEach(city => console.log('Have you visited ' + city + '?'));

// Choose a method that will return a new array
const longCities = cities.filter(city => city.length > 7);

// Choose a method that will return a single value
const word = cities.reduce((acc, currVal) => {
  return acc + currVal[0]
}, "C");

console.log(word)

// Choose a method that will return a new array
const smallerNums = nums.map(num => num - 5);

// Choose a method that will return a boolean value
nums.every(num => num < 0);
```
It's not much to look at but using the right methods was time consuming and required a ton of attention to detail and remembering things I learned two days ago, on my part, so I am happy with progress on that! 

### Day 13...ITERATORS!

Fitting that I would have to do this lesson again! Today I am spent time reading back over the iterator lesson, I wasn't quite ready to move on. Nothing new to report here but just a repetition of yesterday's lessons. 

### Day 12 Iterators!

The word iterate just makes me _feel_ smarter so I already have that going for me. Today I created another secret message, aka Hello World, by using the .map method.

When .map() is called on an array, it takes an argument of a callback function and returns a new array, then I used the join function to join the array, to output HelloWorld. Atleast that is what I think this does!

```javascript
const animals = ['Hen', 'elephant', 'llama', 'leopard', 'ostrich', 'Whale', 'octopus', 'rabbit', 'lion', 'dog'];

// Create the secretMessage array below
const secretMessage = animals.map(animal => animal[0]);

console.log(secretMessage.join(''));
```

I also learned about filter, which is similar to map, only, like it suggests, it filters and returns only specific elements within the array. 

For example, I filtered out favorite words for any words >7 characters long with the below code:

```javascript

const favoriteWords = ['nostalgia', 'hyperbole', 'fervent', 'esoteric', 'serene'];

const longFavoriteWords = favoriteWords.filter(word => {
  return word.length > 7;
})
console.log(longFavoriteWords)
```

I also learned to use the index method to figure out where a string falls in an array. For example, if we have the array ['hippo', 'tiger', 'lion', 'seal', 'cheetah', 'monkey', 'salamander', 'elephant'];
 and I need to know where elephant falls in the array, I could use the below code, which would return 7, which makes sense because the index starts at 0.

```javascript
const animals = ['hippo', 'tiger', 'lion', 'seal', 'cheetah', 'monkey', 'salamander', 'elephant'];

const foundAnimal = animals.findIndex(num => {
  return num === 'elephant';
});
console.log(foundAnimal)
```

I could get even fancier and find just the first animal starting with S by using the below

```javascript
const startsWithS = animals.findIndex(animal => {
  return animal[0] === 's' ? true : false;
});

```

Today I was a little burnt out, so I am calling it good there and reviewing! 

### Day 11 Higher Order Functions

Today was a doozy. Today I worked on Higher Order Functions, which are basically a function that either accepts functions as parameters, returns a function, or both. My brain is on fire. 

The one cool way that it brought it all together was by explaining that we as humans make a whole lot of assumptions, and we cannot assume a computer knows something abstract. Like, for example, when I say bake in a conversation about making a cake, you probably understand exactly what I mean. A computer does not know what bake is by default, or share our common language. So when I say I baked a cake, you know I preheated the oven, prepared the cake, inserted the cake, and then removed the cake and let it cool. A computer can't possibly get that! For this reason, with computers, we have functions, which are how we accomplish abstraction, or rather, the concept of dealing with ideas vs events.

For example, if I say count to three. You know what I mean but in code, we could tell a computer how to count to three like this:

```javascript
for (let i = 1; i<=3; i++) {
  console.log(i)
}
};
```
Cool. I kind of get that! So I moved on to the whole picture aka creating a higher order function, which I _kinnddd_ of get. 


The below code first has a function that checks whether 2+2 = 4, one millllion times because Code Academy instructed me to do this. Then, I declared a function, addTwo which is num + 2. 

The next bit of code is a higher-order function, timeFuncRuntime(). It takes in a function as an argument. Then, it saves a starting time, invokes the callback function, records the time after the function was called, and returns the time the function took to run by subtracting the starting time from the ending time. This was all extremely complicated for me, so I am reviewing with more practice as I basically followed baby step by baby step exactly what Code Academy instructed me to do. That said, here was what I was able to work out:

```javascript 
const checkThatTwoPlusTwoEqualsFourAMillionTimes = () => {
  for(let i = 1; i <= 1000000; i++) {
    if ( (2 + 2) != 4) {
      console.log('Something has gone very wrong :( ');
    }
  }
};

const addTwo = num => num + 2;

const timeFuncRuntime = funcParameter => {
  let t1 = Date.now();
  funcParameter();
  let t2 = Date.now();
  return t2 - t1;
}

const time2p2 = timeFuncRuntime(checkThatTwoPlusTwoEqualsFourAMillionTimes);

const checkConsistentOutput = (func, val) => {
    let firstTry = func(val);
    let secondTry = func(val);
    if (firstTry === secondTry) {
        return firstTry;
    } else {
        return 'This function returned inconsistent results';
    }
};
checkConsistentOutput(addTwo,2);

```
The cool thing I'm learning about higher order functions is that it allows you to write code that is quite complex, but able to be easily debugged, reused and understandable for we humans. Functions can still be worked with the same way we work with other variables. While I enjoy that functions can be passed into other functions as parameters, creating a much wider range of capabilities, I full on _do not get it_. I'm going to let this sink in, and practice this exact Code Academy lesson again tomorrow, and perhaps the following few days until it clicks, but it will click, eventually.


### Day 10 WHALE TALK! 

Today I used my knowledge of loops, and nested loops to complete a code academy project called Whale Talk!

There are a few simple rules for translating text to whale language:

There are no consonants. Only vowels excluding “y”.
The u‘s and e‘s are extra long, so we must double them in our program.

```javascript
let input = 'turpentine and turtles';
const vowels = ['a', 'e', 'i', 'o', 'u'];
const resultArray = [];
for (let i = 0; i < input.length; i++){
  for (let j = 0; j < vowels.length; j++){
    if (input[i] === vowels[j]){
      resultArray.push(vowels[j]);
      if (input[i] === 'e' || input[i] === 'u'){
        resultArray.push(input[i])
      }
    }
  }
};
  console.log(resultArray.join('').toUpperCase());
```

###  Day 9 LOOPS! 

Today I looped so hard I froze my computer and now here we are..completely restarting my writeup for 100 days of code day 9. Fun! Today I learned about the for loop and wrote a program to compare social media followers of two people, and then output the mutual followers. 

In the below code I have created two arrays, one for Bob's followers, and one for Tina's followers. I then created a third empty array for mutual followers.

Then, in the for loop, I take Bob's followers and compare them to Tinas followers, and if there is a match, I push the value to the mutualFollowers array.

```javascript
const bobsFollowers = ['chels','mitch','wes','lou'];
const tinasFollowers = ['chels','mitch','elissa'];
const mutualFollowers = [];
for (let i = 0; i < bobsFollowers.length; i++) {
  for (let j = 0; j < tinasFollowers.length; j++) {
    if (bobsFollowers[i] === tinasFollowers[j]) {
mutualFollowers.push(tinasFollowers[j]);
    }
  }
};
console.log(mutualFollowers)
```

TLDR Today I learned basics of loops, why repeating them manually is the literal worst, how to use the for loop, looping in reverse, looping through arrays, and nested loops! Tomorrow I shall dive into while loops, do while loops and the break keyword to wrap up this weeks lesson.


### Day 8: Array Project, Secret Message

Since I learned a TON about arrays yesterday, today I'm testing my learning by doing my Code Academy Project. 

To start the project I'm given the following: 

```javascript
let secretMessage = ['Learning', 'is', 'not', 'about', 'what', 'you', 'get', 'easily', 'the', 'first', 'time,', 'it', 'is', 'about', 'what', 'you', 'can', 'figure', 'out.', '-2015,', 'Chris', 'Pine,', 'Learn', 'JavaScript'];
```

First on my list of instructions, is to remove the last item in the array. We can use the pop method to do this, like this:

```javascript
let secretMessage = ['Learning', 'is', 'not', 'about', 'what', 'you', 'get', 'easily', 'the', 'first', 'time,', 'it', 'is', 'about', 'what', 'you', 'can', 'figure', 'out.', '-2015,', 'Chris', 'Pine,', 'Learn', 'JavaScript'];

secretMessage.pop();
```

The output will now be: 
 ['Learning', 'is', 'not', 'about', 'what', 'you', 'get', 'easily', 'the', 'first', 'time,', 'it', 'is', 'about', 'what', 'you', 'can', 'figure', 'out.', '-2015,', 'Chris', 'Pine,', 'Learn'];
 
Next, I needed to add two separate strings to the end of the array; to and Program. I can use push to do this, so now we have:

```javascript
let secretMessage = ['Learning', 'is', 'not', 'about', 'what', 'you', 'get', 'easily', 'the', 'first', 'time,', 'it', 'is', 'about', 'what', 'you', 'can', 'figure', 'out.', '-2015,', 'Chris', 'Pine,', 'Learn', 'JavaScript'];

secretMessage.pop();

secretMessage.push('to','Program');
```
The result?  ['Learning', 'is', 'not', 'about', 'what', 'you', 'get', 'easily', 'the', 'first', 'time,', 'it', 'is', 'about', 'what', 'you', 'can', 'figure', 'out.', '-2015,', 'Chris', 'Pine,', 'Learn', 'to','Program'];

Next we want to replace easily, with right.

To do that we could use splice, for example:
```javascript
secretMessage.splice(7, 1,'right')
```

The above takes index 7 which is easily, removes 1 item from the array then replaces with right. Next, we need to remove the first item of the array, to do that we can use shift, like this:
```javascript
secretMessage.shift();
```
To recap, here's what we have so far:
```javascript
let secretMessage = ['Learning', 'is', 'not', 'about', 'what', 'you', 'get', 'easily', 'the', 'first', 'time,', 'it', 'is', 'about', 'what', 'you', 'can', 'figure', 'out.', '-2015,', 'Chris', 'Pine,', 'Learn', 'JavaScript'];

secretMessage.pop();
secretMessage.push('to','Program');
secretMessage.splice(7, 1,'right');
secretMessage.shift();
console.log(secretMessage)
```
The output is 
!array(https://cdn.zappy.app/0d04017937d283d4d03ef48b65d375f1.png)

Cool. Let's speed up a bit! 

Next we'll use a method to remove get, right, the, first, time, and replace them with only one string: know

wala! Here's the full code:

```javascript
let secretMessage = ['Learning', 'is', 'not', 'about', 'what', 'you', 'get', 'easily', 'the', 'first', 'time,', 'it', 'is', 'about', 'what', 'you', 'can', 'figure', 'out.', '-2015,', 'Chris', 'Pine,', 'Learn', 'JavaScript'];

secretMessage.pop();
secretMessage.push('to','Program');
secretMessage.splice(7, 1,'right');
secretMessage.shift();
secretMessage.unshift('Programming');
secretMessage.splice(6,5,'know')
console.log(secretMessage.join())
```

The end result? 

Programming is not about what you know, it is about what you can figure out. -2015, Chris Pine, Learn to Program


 
### Day 7: Arrays

Arrays are my final lesson in the CodeAcademy Javascript refresher course I'm taking, so Im excited but also _I hate arrays_. I don't even know why I hate arrays, they seem really useful, but for whatever reason I am constantly confused. My guess is that this comes from the issues I experience with line items, but I'm certain similar to Facebook Lead ads, this is something that is simple _once you know_ how it works! 

An array in simple terms is an object that holds a list of values. For example, creating an array containing a grocery list might look like this:
```javascript
let groceryList = ['pizza', 'nuggets', 'mac n cheese'];

console.log(groceryList);

```

The entire array is everything within the brackets, and each individual item is called an element.

The output would look something like this:   
![groceries](https://cdn.zappy.app/04d98f76233ea4bd7332b081173d4cb4.png)

Cool, that literally seems like a piece of cake. Arrays can store any strings, booleans, and numbers which is pretty neat. I'm starting to see how these are cool. You can create an array by literally just wrapping the values in brackets, like this:
```javascript
const hobbies = ['painting','hiking','yoga'];

console.log(hobbies)
```
The above looks _slightly_ different from the first array. That's because the array above is an array literal whereas the first array was a variable, meaning, I could declare a whole new set of NYR. I won't though, because I don't believe in NYR.

Buckle up, we're reaching the part where I get confused, aka the Index. Each element in an array has a numbered position. This is known as the index. For example, in the hobbies array, the index is as follows, because an index starts with 0:  


![hobbiesss](https://cdn.zappy.app/81fb06a8f339d3332f552ee60bfee5c7.png)

You can access the individual elements like this, for example, which would return painting:  


```javascript
console.log(hobbies[0]);
```

Then if you wanted to change one of the hobbies in the list, for example change painting to woodworking, I could do this:


```javascript
let hobbies = ['painting','hiking','yoga'];
hobbies[0] = 'woodworking'
console.log(hobbies);
```

I could see how arrays are pretty useful now and this lesson definitely did not make me afraid of them any more which is cool. Alas tho, I also learned some things to make working with them easier!

I introduce to you..the push method! Push would let us add more items to the end of the array or 'list' as I call it. If we want to remove items, we just use pop. So if I have a chore list, and I add laundry but I'm like..nah I am good I'm going to _not_ do the laundry, I would use push to add then pop to remove! Here's what that looks like:
```javascript
let chores = ['fold clothes','make bed', 'be a human'];
chores.push('do laundry');
console.log(chores);
chores.pop();
console.log(chores);
```

Neato!

It gets CRAZIER! You can also use .join(), .slice(), .splice(), .shift(), .unshift(), and .concat() 

Arrays can be kind of confusing IMO but I minimally appreciate them. TLDR here's what I learned:

-  Arrays are lists that store data in JavaScript.
-  Arrays are created with brackets [].
-  Each item inside of an array is at a numbered position, or index, starting at 0.
-  You can access one item in an array using its index, with syntax like: myArray[0].
-  You can also change an item in an array using its index, with syntax like myArray[0] = 'new string';
-  Arrays have their own methods, including .push() and .pop(), which add and remove items from an array,
-  Variables that contain arrays can be declared with let or const. Even when declared with const, arrays are still mutable. However, a variable declared with const cannot be reassigned.
-  Arrays mutated inside of a function will keep that change even outside the function.
-  Arrays can be nested inside other arrays._oof_
- To access elements in nested arrays chain indices using bracket notation, like this array[1][3]for example.

Thats enough arrays for today.

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

- **pwd** outputs the name of the current working directory.
- **ls** lists all files and directories in the working directory.
- **cd** switches you into the directory you specify.
- **mkdir** creates a new directory in the working directory.
- **touch** creates a new file inside the working directory.


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

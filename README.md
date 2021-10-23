# Date Regex

This repo serves as a quick breakdown and tutorial for a regular expression (regex) that validates input date values. We will go over three of the most common formats used throughout the world in this breakdown. These formats include (mm/dd/yyyy) | (dd/mm/yyyy) | (yyyy/mm/dd). If you wish to explore more regex examples, check out this link for the [20 most common regular expressions used](https://regexland.com/most-common-regular-expressions)

## Summary


We have three date formats that we will be examining, these three are:
* (mm/dd/yyyy) ```/^(0[1-9]|1[0-2])/(0[1-9]|[12][0-9]|3[01])/\d{4}$/```
* (dd/mm/yyyy) ```/^(0[1-9]|[12][0-9]|3[01])/(0[1-9]|1[0-2])/\d{4}$/```
* (yyyy/mm/dd) ```/^\d{4}/(0[1-9]|1[0-2])/(0[1-9]|[12][0-9]|3[01])$/```

For the sake of simplicity, I am going to be referring to the format (mm/dd/yyyy) throughout this readMe unless specified otherwise. We will breakdown each of the regex components so you will have an understanding of what is being described in the expression as well as being able to modify the regex to make it fit your needs.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)

## Regex Components

### Anchors
There are two types of anchors:
* ```^``` ex: ```^The``` string that starts with "The"
* ```$``` ex: ```end$``` string that ends with "end"
  * You can combine the two to find a string with an exact match. ex: ```^The end$``` 

The ```^``` at the beginning and the ```$``` at the end are there to validate the format of the input date. In our example, these anchors are placed at the beginning and end of our regex, which allows the regex to check to see if the input format follows (mm/dd/yyyy). You can change the format by switching the order inside the anchors. <br>
For example: <br>
```/^\d{4}/(0[1-9]|1[0-2])/(0[1-9]|[12][0-9]|3[01])$/``` would check (yyyy/mm/dd) <br>
```/^(0[1-9]|[12][0-9]|3[01])/(0[1-9]|1[0-2])/\d{4}$/``` would check (dd/mm/yyyy) <br>
Notice the anchors do not move, only the contents within the anchors.

### Quantifiers
* ```*``` ex: ```abc*``` string that has "ab" followed by zero or more "c"('s)
* ```+``` ex: ```abc+``` string that has "ab" followed by one or more "c"('s)
* ```?``` ex: ```abc?``` string that has "ab" followed by zero or one "c"
* ```{ }``` ex: ```abc{5}``` string that has "ab" followed by five "c"'s
The only quantifier being used in our date regex is for the input year. The snippet ```{4}``` follows imediataely after the character class ```\d```, which means the expression is checking for four digits after our input day ```(0[1-9]|[12][0-9]|3[01])```.

### Grouping Constructs
In our example, there are two instances of grouping constructs. Grouping is accomplished by placing paranthesis around the values you wish to group. Looking at our example ```/^(0[1-9]|1[0-2])/(0[1-9]|[12][0-9]|3[01])/\d{4}$/``` you can see that the groups are formed around the month itself, and the day of the month, respectively.

### Bracket Expressions
We have several bracket expressions seen in our regex, all of which are used to check if the value of an input character matches the stated range of numbers. For example in the snippet ```[1-9]``` the expression is looking for a matching string that has a character from 1-9.


### Character Classes
* ```\d``` character is a digit
* ```\w``` character is a word character (alphanumeric plus underscore)
* ```\s``` character is whitespace
* ```.``` any character
The only character class being used in our example is the ```\d```. This is checking for a single character that is a digit. ```\d{4}``` in our example is validating a four digit year.

### The OR Operator
OR operators consist of ```[ ]``` and ```|```. There are several OR operators being used in our regex. In this snippet for checking the input month ```(0[1-9]|1[0-2])```, you can see two sets of brackets containing an array of numbers. The first set is checking for a value of ```0``` on the first input character and then a number that falls bewtween ```[1-9]``` for the second input character. Then you see the OR operator ```|``` which will trigger if the first entered character is not a "0". For example, if the input month is "11", the OR operator will be executed and the set to right of ```|``` will be used to check for a matching value. In this case "11" would be a valid input.

## Author
Tommy Jobin | [Github](https://github.com/LoopySquare)

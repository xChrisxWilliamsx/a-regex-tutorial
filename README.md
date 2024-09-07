## A Regex Tutorial ♥
<strong>Regex, short for regular expression, is a powerful tool for searching and manipulating text by defining patterns. It allows you to find, match, and replace text based on specific rules. Lets take a deep dive into the interesting and fun world that is regex!</strong>

## Summary
In this tutorial we will breaking down a regex snippet into its identifying components and reviewing their concepts.
<br>
The regex we will be using throughout this tutorial is `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`.
<br>
This regex is matching an email, lets hop into deciphering what is going on!

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [Decipher](#decipher)


## Regex Components
> Lets remember, the regex we will be explaining is `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
  
### Anchors
Regex Anchors are the characters `^` and `$` which define the beginning and end of a match.
<br>
The `^` anchor defines the start of your match where the characters will follow after.
<br>
The `$` anchor defines the end of your match which will exit the match at the end of your desired string.  
<br>
Lets see if we have these in our example!
<br>
/<mark><strong>^</strong></mark>([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})<mark><strong>$</strong></mark>/
<br>
AWESOME! It looks like we have the `^` at the very beginning of our regex and the `$` at the end.
<br>
Lets see what else we can find in our regex.

### Quantifiers
Quantifers define a number of characters or expressions to match.
<br>
There are a few Quantifiers in regex, lets take a look at them:
<br>
* `*` Matches the preceding characters 0 or more times.
* `+` Matches the preceding characters 1 or more times.
*  `?` Matches the preceding characters 0 or 1 times.
*  `{v}` Matches the exact length of the preceding characters.
*  `{v, }` Matches at least the length of the preceding characters.
*  `{v, c}` Matches the length of the preceding characters between the two integer values.
*  <strong>By Default, typically, quantifiers are greedy and my do some weird stuff, like match with whitespace when that was not the desired outcome.  You can add the `?` special character to the end of your quantifier to make them not greedy.  Fun fact!</strong>
<br>
Now that that fun stuff is out of the way, lets take a peek to see if we have any quantifers in our regex snippet.
<br>
Bingo! Looks like we found a few - /^([a-z0-9_\.-] <mark><strong>+</strong></mark>)@([\da-z\.-]<mark><strong>+</strong></mark>)\.([a-z\.]<mark><strong>{2,6}</strong></mark>)$/
<br>
So what we are saying is, match an occurance <strong>1 or more times</strong> of [a-z0-9_\.-] and of [\da-z\.-] as well as any occurance of [a-z\.] with a charachter value <strong>betwen 2 and 6</strong>.
<br>
As we go throught this tutorial we will be explaining what more of these characters define! 

### Grouping Constructs
Regex groups can allow you to target specific parts of your matches by bundling them up into convenient groups.  The overall match is group 0, then group 1, group 2, from left to right for as many as you need.  When used in conjunction correctly with some code these can be targeted and stored into arrays.  
<br>
Regex grouping identifiers are ``(`` and `)`.  Wrap these parentheses around your desired regex that you would like to segment into a group.
<br>
These do pop up in our nifty regex snippet here /^<mark><strong>(</strong></mark>[a-z0-9_\.-]+<mark><strong>)</strong></mark>@<mark><strong>(</strong></mark>[\da-z\.-]+<mark><strong>)</strong></mark>\.<mark><strong>(</strong></mark>[a-z\.]{2,6}<mark><strong>)</strong></mark>$/
<br>
Lets keep going! 

### Bracket Expressions
A regex bracket expression is a list of characters enclosed by `[` and `]`. It matches any single character in that list. If the first character of the list is the caret `^`, then it matches any character not in the list.
<br>
Bracket expressions can consists of one or more expressions: ordinary characters, collating elements, collating symbols, equivalence classes, character classes, or range expressions.
<br>
This enables you to add in a wide range of parameters with the `[` and `]` brackets to allow you to match with your desired outcome.  
<br>
We do see these pop up in our regex snippets here /^(<mark><strong>[</strong></mark>a-z0-9_\.-<mark><strong>]</strong></mark>+)@(<mark><strong>[</strong></mark>\da-z\.-<mark><strong>]</strong></mark>+)\.(<mark><strong>[</strong></mark>a-z\.<mark><strong>]</strong></mark>{2,6})$/
<br>
What this is saying is, whatever expression is in side of these brackets filter through and match with any of the same results.  
<br>
At the end of this tutorial I will decode this regex snippet into plain english to better assist with expanding the knowledge of regex.
<br>
Lets see what Character Classes have in store for us!

### Character Classes
There are several character classes in regex.  Their main focus is to distinguish between characters, special characters, digits, white space, and can act as parameters, possibly among other things.
<br>
I will list a few character classes for you however for a more indepth break down please visit:
<br>
[MDN WEB DOCS Regex Character Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Character_classes)
* `\w` defines any character or digit withing a-z 0-9(`\W` when capitalized it matches anything that is not within its normal functionality)
* `\d` defines any digit between 0-9(`\D` when capitalized it matches anything that is not within its normal functionality)
* `a-z` defines any character between a-z (could be case sensitive depending on where this is being used so may need to use `A-Z` to target capital letters.  Safe bet to add these together such as `A-Za-z`)
* `\s` defines a match with any whitespace(`\S` when capitalized defines any non-whitespace)
* `.` This is a wild card.  This matches any single character expect for any thing that stops it from filtering.  This one can add more matches than intended so use with care.(when used with `\` to make `\.` it just means a period.  It turns some character classes into literal expersions. 
<br>
As expected we do see this all over our regex snippet.  This is more or less the bulk of the brain power to find our matches.
<br>
We see it in our regex snippets here /^([<mark><strong>a-z0-9_\.-</strong></mark>]+)@([<mark><strong>\da-z\.-</strong></mark>]+)\.([<mark><strong>a-z\.</strong></mark>]{2,6})$/
<br>
We will go more indepth later on in this tutorial in regards to what this is doing so stay tuned! 

### The OR Operator
Regex OR Operators can decipher if something may or may not be apart of a match.  The two operators that come to mind go as follows:
* `|` The vertical bar states if something or one of another thing may be a valid match such as it may either be a or b / a | b
* `?` The question mark or operator states zero or more of the proceeding value may be in the match.  It may or may not have a consecutive row of the digits within 0-9 / \d?
<br>
I do not believe we have any OR Operators in our regex snippet.  If I am wrong please feel free to reachout to me! My GitHub account listed below.
<br>
Now lets have some fun with Flags!  Unfortunetly Dr. Sheldon Cooper won't be here for this Fun With Flags..

### Flags
There are a few regex flags to date however I will list what I believe to be the main two.  For more information on flags please visit:
<br>
[JavaScrpt.info](https://javascript.info/regexp-introduction)
<br>
* `g` This is a global flag.  This will scrape all provided information for a match. Without this you may only get a return of one match result.  
* `i` This is a case-insensitive flag.  This will seach for all instances of your parameters whether or not they are capitalized.  
<br>
Just like the OR Operators, I do not see any flags in our regex snippet.
<br>
Lets take a peek at Regex Character Escapes!

### Character Escapes
Character Escapes are characters that are not easily translated into their literal form however play a big role with the functionality in created further parameters for your regex to filter through the desired data.
<br>
For more information and details on specific please go to:
<br>

[MDN WEB DOC Character Escapes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_escape)
<br>
There shouldn't be any character escapes in our regex snippet but again if I am missing anything please let me know! 

### Decipher
OK! Given the infomation we have learned, lets decipher this:
* Given our regex snippet `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
* We say: I would like to use regex to return some data back. I would like to group this data together with the first instance of our match being called group 0 and any further matches would be adding another group. Lets start by targeted the start of our match parameters by using `^`.  I then want to return my second group with could contain any amount and in any order of a through z, zero through nine and could include an underscore, a period, and a hyphen.  This is where we state `([a-z0-9_\.-]`.  We need to match with one or more instance of this which we define this with `+`.  We then say right after that new group 1 we need to have the at symbol `@`.  This is literal experssion we literally need to have the at symbol there for it to be a match. Then after the at symbol we want to find our third group, group 2, which will include any digit of zero through nine followed by any letters between a-z and it should include either a period or a hyphen.  We need to match with one or more instance of this.  This is stated by including `([\da-z\.-]+)`.  After that is should have a period which is defined by using `\.`. Almost done! Then our last group I want to match anything with a-z, could include a period.  It also needs to be between two and six characters long.  This is defined by adding `([a-z\.]{2,6})`. Lastly I want to stop the length of our search by using `$`

## Author
<p>If you made it to the end, thank you so much for taking the time to read through this regex tutorial.
<p>If you would like to see my other works please visit:
<br>
 
[xChrisxWilliamsx GitHub](https://github.com/xChrisxWilliamsx)

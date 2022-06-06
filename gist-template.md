# Regex Tutorial 


## Summary
Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
Anchors inform us that the engine's current position in the string matches a determined location, so for example, the start of the string/line, or the end of a string/line.

Example:
/^ signifies the beginning of the expression.
/$ signifies the end of the expression.



### Quantifiers
Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found. 

Example:
The fat cat ran down the street.
It was searching for something to feast on.

(*) matches the previous element 0 or more times.
    re* matches anything that has r and all the e's that follow it if there are any. If not, just the r itself. 

(+) matches the previous element 1 or more times.
    e+ matches e, but matches at least 1 or more.
    + means to match as many e's in a row. 

(?) matches the previous element 0 or 1 time.
    a? means that it's optional, so optionally, it will get the a character. 
    ea? will get the character e, and if there's an a, it's also going to match that. 
    Whatever is before the ? is going to be optional. 

w{4} matches the previous element exactly 4 times.
    {4} inside the curly brace, you can set the minimum and maximum amount of characters. 
    match any four digits in a row.

w{4,} matches the previous element 4 or more times.
    {4,} match any four digits in a row.

w{4,5} matches the previous element between 4 and 5 times.
    {4,5} matches any set of characters that are between four and five long. 



### OR Operator
OR Operator is a like boolean. It matches the expression before or after the |. It tests in order and looks for this or that. 

Example:
The fat cat ran down the street.
It was searching for something to feast on.

(t|The) checks for either lower case t or the entire word 'The'.

### Character Classes
Character classes matches a character from a specific set. 

Example: 
The fat cat ran down the street.
It was searching for something to feast on.

[fc] inside the square bracket, you can put any characters 
     you want to match and it's saying match any of the characters inside of it. 

[^fc] the carrot will match any character that's not in 
      the set.

[a-z] matches a character in the range 'a' to 'z' that are 
      in lower case

[.at] will match the f, c and e, fat, cat, eat. It will 
      match any character except a new line/linebreak. 

[A-Z] matches a character in the range 'a' to 'z' that are
      in upper case. 

\w means to match any word characters/letters. 

\W means to match anything that are not characters/letters.

\s means it will match and form of white space.

\S means it will match anything that is not a white space.

\p means it will match a character in the specified 
   unicode category .

\d means to match any digit 0-9.

\D means to match anything that is not a digit.




### Flags

Example:
There are several flags you can use to alter the Regex behavior. Flags may be appended to the end of a regex literal or they may be specified as the second argument to the Regex constructor. 

g - global continues to find matches after the first 

i - ignore case, insensitive. It makes the entire expression case
    insensitive. /[a-z]/i is the same as /[a-zA-Z]/

m - multi-line. It only affects the behavior of ^ and &. They match not    
    only at the beginning and the end of the string, but also at start/end of line.
    let str = `1st place: Winnie
    2nd place: Piglet
    3rd place: Eeyore`;

    console.log( str.match(/^\d/gm) ); // 1, 2, 3

    with the m, only the first digit is matched 

    console.log( str.match(/^\d/gm) ); // 1

u - unicode. It switches on Unicode mode for regexes. Makes the expression 
    assume individual characters as code points, not code units, and thus match 32-bit characters as well.

y - sticky searching. Makes the expression start its searching from the 
    index indicated in its lastIndex property.

    var str = "Cats love cats, and we love cats."
    "Cats love cats, and we love cats."
    This will match all three cats.

    var exp = /cats/igy;
    exp.lastIndex = 4;
    "Cats love cats, and we love cats."
    With lastIndex specified, now if exp searches over str it will match the second and third 'cats'.
    This is because it appears at index 0, whereas the expression exp is sticky and starts searching at index 4.
    

### Grouping and Capturing
Capturing groups are a way to treat multiple characters as a single unit. They are created by placing the characters to be grouped inside a set of parentheses. For example, the regular expression (dog) creates a single group containing the letters "d" "o" and "g". The portion of the input string that matches the capturing group will be saved in memory for later recall via backreferences.


### Bracket Expressions
Bracket expressions can be used to match a single character or collating element.

[]     matches any single character within the brackets.

[]%    matches the string inside the brackets before the %.

[^]    matches any string that has not a letter from within the brackets.

[abcd] matches any character in the square brackets.
       [nN] [oO] matches no, nO, No, and NO.
       [0-9] matches any four-digit string.
       [ab3-5] matches any decimal digit.

[a-d]  matches any character in the range of characters separated by a  
       hyphen. 
       ^[A-Za-z]+$ matches any string that contains only upper and lowercase characters.
       \[[0-9 ]*\] matches an opening square bracket, followed by any digits or spaces, followed by a closed bracket.

[^abcd] matches any character except those in the square brackets or in 
 [^a-d] the range of characters separated by a hyphen.
        [^0-9] matches any string that does not contain any numeric characters.

[.ab]   matches a multi-character collating element.
        [.ch.] matches the multi-character collating sequence ch.

[=a=]   mataches all collating elements with the same primary sort order 
        as that element, including the element itself. 
        [=e=] matches e and all the variants of e in the current locale.
        

### Greedy and Lazy Match


### Boundaries


### Back-references


### Look-ahead and Look-behind


### Author
Hanna L. GWU Coding Bootcamp 2022

GitHub: https://github.com/hlee92
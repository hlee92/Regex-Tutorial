# Regex Tutorial 
<br></br>

## **Matching an Email: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/**
<br></br>

## Summary
Regex, short for regular expression, is a sequence of characters that defines a specific search pattern in text. Regex can be used to find certain patterns of characters or to find and replace a character or sequence of characters within a string in code or search algorithms. 

This tutorial takes a deeper dive into how regex functions by breaking down each part of the expression and explaining what it does.
<br></br>

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [OR Operator](#or-operator)
- [Flags](#flags)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)
- [Author](#author)
<br></br>

## Regex Components
<br></br>

## **Anchors**

Anchors inform us that the engine's current position in the string matches a determined location, so for example, the start of the string/line, or the end of a string/line.

Example:
/^ signifies the beginning of the expression.
/$ signifies the end of the expression.
<br></br>

## **Quantifiers**

Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found. 

The + operator is a quantifier in this regex which connects the users email name + email service + .com. Another quantifier is {2,6} which will match a range of 2-6 characters for character set [a-z\.]

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
<br></br>

## **Character Classes**

Character classes matches a character from a specific set. 
The character class in this expression is \d which matches a single character that falls within 0-9. It will match '4' and not '44'.

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
<br></br>

## **Grouping and Capturing**

Capturing groups are a way to treat multiple characters as a single unit. They are created by placing the characters to be grouped inside a set of parentheses. For example, the regular expression (dog) creates a single group containing the letters "d" "o" and "g". The portion of the input string that matches the capturing group will be saved in memory for later recall via backreferences.

There are three capturing groups in this expression. The first one is 
([a-z0-9_\.-]+) which matches the user email name. The second is 
([\da-z\.-]+) which matches the email service. The last one is 
([a-z\.]{2,6}) which captures the .com.
<br></br>

## **Bracket Expressions**

Bracket expressions can be used to match a single character or collating element. 
Bracket expression for email verification includes the character sets of [a-z0-9_\.-], which matches any letter a-z and is case sensitive. 
It wil also match character 0-9 and matches the characters "_", "-", and "."; [\da-z\.-] which is matching a single digit 0-9, and character within a-z (case sensitive), and the characters "-" and "."; [a-z\.] which matches any character a-z (case sensitve) and the character ".".

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
<br></br>

## **Greedy and Lazy Match**

Greedy mode of quantifiers matches the longest possible string. 
The lazy mode of quantifiers is an opposite to the greedy mode. It means: “repeat minimal number of times”.

Since this expression has the + quantifier, it will match as many times as possible giving back as needed. {} is another greedy quantifier when matching {2,6} for the last capture group. 
<br></br>

## **OR Operator**

OR Operator is a like boolean. It matches the expression before or after the |. It tests in order and looks for this or that. 

Example:
The fat cat ran down the street.
It was searching for something to feast on.

(t|The) checks for either lower case t or the entire word 'The'.
<br></br>

## **Flags**

Example:
There are several flags you can use to alter the Regex behavior. Flags may be appended to the end of a regex literal or they may be specified as the second argument to the Regex constructor. 

g - global continues to find matches after the first 

i - ignore case, insensitive. It makes the entire expression case
    insensitive. /[a-z]/i is the same as /[a-zA-Z]/

m - multi-line. It only affects the behavior of ^ and &. They match not only at the beginning and the end of the string, but also at start/end of line.
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


## **Boundaries**

The (\b) is an anchor like the caret (^) and the dollar sign ($). It matches a position that is called a “word boundary”. The word boundary match is zero-length.
Simply put, the word boundary \b allows you to carry the match the whole word using a regular expression.
<br></br>

## **Back-references**

Back-references are regular expression commands which refer to a previous part of the matched regular expression. Back-references are specified with backslash and a single digit (' \1 '). 
The part of the regular expression they refer to is called a sub-expression, and is designated with parentheses.
<br></br>

## **Look-ahead and Look-behind**

Sometimes we need to find only those matches for a pattern that are followed or preceded by another pattern.
There’s a special syntax for that, called “lookahead” and “lookbehind”, together referred to as “lookaround”.
<br></br>

## **Author**

Hanna L. GWU Coding Bootcamp 2022

GitHub: https://github.com/hlee92
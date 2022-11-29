# Character Name Validation

Describing how to assemble a regular expression to set up validation of restrictions for a player's in game character name.

## Summary

Below is the regex function in question 

```/^[A-Z][a-zA-Z'-]{0,13}[a-z] [A-Z][a-zA-Z'-]{0,13}[a-z]$/```

it will be checking for the following requirements:

- First and last names each begin with an uppercase character
- First and last names can only contain lower letters, uppercase letters, ', and - 
- there is a singular space between the first and last name
- First and last names must be at least 2 but no more than 15 characters long
- First and last names must end in a lowercase character

Examples of matches:
```
LeBron JaMes
An-thony Da'vis
Ru Wb
```



## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Bracket Expressions](#bracket-expressions)
- [Author](#author)


## Regex Components

### Anchors

The anchors used are ```^``` which signifies the beginning of the name and ```$``` which signifies the end of the string. ```^``` matches the specifications following it and ```$``` the ones preceding it.

In this example they ensure that the character requirements between them are satisfied, containing the first name, space, and last name.

- for example: 
    - ```^A``` matches ```A``` and ```A goose```
    - ```ose$``` matches ```A goose```

### Quantifiers

Quantifiers define the number of specific matches required.  

examples of quantifiers include:

- ```*``` matches any amount of occurences
- ```+``` matches at least one occurence
- ```{n}``` matches exactly n occurences
- ```{n,x}``` matches from n to x occurences

In this regex ```{n, x}``` quantifiers are used in the form of ```{0,13}``` this means that ```[a-zA-Z'-]``` can be matched from 0-13 times within the first and last name. Including the required capital letter and lowercase letter at the beginning and end of each name respectively this sets the bounds of each name at (2,15).

- for example: 
    - ```a{5}``` matches ```aaaaa```

### Character Classes

Character classes specify which characters that can be matched.

examples of character classes include:

- ```.``` matches all characters
- ```\w``` matches all alphanumeric characters
- ```\s``` matches whitespace characters
- ```a``` matches the letter a

This is used in this example in combination with bracket expressions to fulfill matching requirements. In this example the non-bracket class is the space between names shown as ``` ```. 

- for example:
    - ```\w*``` (using the * quantifier) matches ```we58gdj```


### Bracket Expressions

Bracket expressions match a character out of a specified range of characters. The characters within the ```[]``` are valid matches.

Bracket expressions are used in the example above in tandem with quantifiers to match certain quantities of characters. There are 3 unique instances of bracket expressions in the regex: ```[A-Z]```, ```[a-zA-Z'-]```, and ```[a-z]```. 

- ```[A-Z]``` matches if the single first character of either name is a capital letter
    - ```A``` is a match
- ```[a-z]``` matches if the single last character of either name is a lowercase letter
    - ```a``` is a match
- ```[a-zA-Z'-]``` matches if the letters inbetween the first and last character are capital letters, lowercase letters, ', or -. This is used in conjuction with ```{0,13}``` to match from 0 up to 13 characters.
    - ```aBc'D-e``` is a match

- all combined it looks like ```[A-Z][a-zA-Z'-]{0,13}[a-z]``` 
    the following are examples of matches
    - ```LeBron```
    - ```Le-Bron```
    - ```Le'BrOn```


## Author

I am an aspiring web developer currently finishing up a full stack bootcamp. My github is [nickgoshev](github.com/nickgoshev) and my email is [nickgosh420@gmail.com](nickgosh420@gmail.com). Feel free to reach out!

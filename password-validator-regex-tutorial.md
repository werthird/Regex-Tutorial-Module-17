# Regex Password Validator

To validate that password contains certian characters and is a certian length, here is a regular expression string that will allow you to test your passwords against.

## Summary

We will be looking over this regex: 

```
/^(?=.*\d)(?=.*[A-Za-z])(?=.*[@!#\$%\^&\*])[A-Za-z\d@!#\$%\^&\*]{8,20}$/
```

It can be used to test a users password to ensure that it contains a capitol, number and special character, and that it is between 8 and 20 characters long.


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Lookahead](#lookahead)
- [Authos](#author)

## Regex Components

Let's start by breaking down this regex, slowly building it from the bottom, so we can fully understand how this works. 

In order to use this in JavaScript to validate a password, we need to wrap the regex in forward-slash, so our language can read it as a literal and not a string. 

```
/regex/
```

<hr>

### **Anchors**

At the beginning of the regex, we have what are called anchors. Anchors allow us to capture a certian section of a string, verses any part of the string that passes our regex. Our regex used one set of anchors:

```
^ ... $
```

By surrounding our regex in these we are looking for any full word that matches the specific qualifications that are between the ^ and the $.

<hr>

### **Quantifiers**

Next, we are using some qualifiers. Qualifiers set the limit of the string out regex is trying to match. We are using a few qualifiers:

```
{8,20}
```
This quantifier checks the length of the string we are testing. If the string is at least 8 characters long and no more then 20 characters, then it will pass this regex test. We added this to ensure that the password is of a managable and secure length.

```
.*
```
The other quantifier we have is one that is used to match zero or more times. It is used to as a select all, or anything possible option. We'll explain a little more on our use of it later.

<hr>

### **Grouping Constructs**

Grouping constructs allow us to break a regex into sections so that we can more easily manage what we are trying to achieve. There is more that we can use grouping constrants for, but for now we'll keep the explaination to our specific regex. 

```
(?=.*\d)
(?=.*[A-Za-z])
(?=.*[@!#\$%\^&\*])
```
In order to group parts of the regex, you need to wrap it in (). Our password validator wants to check that we have at least one capitol letter, number and special character. You can see that we are testing for each of those conditions in our regex. Don't worry about what is inside the () for now. Just know, in order to test each condition, we need to wrap them in seperate groups so that each one has to pass.

<hr>

### **Bracket Expressions**

Here is where we get into the meat and potatos of the regex. Anything inside square brackets represents the range of what we are trying to match. Take a look at what we are trying to match in our password:

```
[A-Za-z\d@!#\$%\^&\*]
```

1. ```A-Z``` - we are looking for any character from capitol A to Z
2. ```a-z``` - we are looking for any character from lowercase a to z
3. ```\d```  - we are looking for any number from 0-9; (this is called a character class that we will talk about next)
4. ```@!#\$%\^&\*``` - we are looking for any of these special characters. *You might notice that we are looking for \ quite a few time. Well, we aren't actually looking for a back slash. The characters that come right after the \, $ ^ *, are characters that are used in the language of regex, and will be used to do something, unless we tell regex to treat them as the literal character.*

As you can see, any password with any of those characters will pass our test. But we want to make sure that the password has at least on of each of those. That is where we get into our validation, in the lookahead section.



<hr>

### **Character Classes**

Character classed are used to define certian sets of characters. The character class we are using here is:

```
\d
```
This will match to any diget in the string. It is the same as if we were to use [0-9].

<hr>


### **Lookahead**

Now we are getting into the good stuff. So far we have checked if the password was between 8 and 20 characters long. Then we are accepting a password with any of the characters from A-Z or a-z or 0-9 or the special character. But how do we make sure that the password has at least one of those characters. This is where we use the lookahead. This is the validation of our password.

```
(?=.*\d)
```

Let's break this down:

1. ?= - This is our lookahead. We are looking ahead at the character and making sure that they have at least one of what we specify
2. .* - This is out Quantifier. It is saying that we can have any character before what we are requiring
3. \d - This is what we are actually requiring. We are saying that the password has to have at least one number in it.

Hopefully now we are able to see how we are making sure that the password meets all the required parameters. We are saying make sure that the password has at least on number, one capitol, one lowercase and one special character.

<hr>


## Author

My name is Devin Reilly and I'm a student at UCF in Florida. This paper was for a homework assignment in my coding bootcamp adventure. I hope it was helpful for anyone who needs it. 

Check out my [GitHub Profile](https://github.com/werthird)!
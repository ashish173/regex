!SLIDE 
# /REGULAR EXPRESSIONS/ in Ruby #
## Programmers swiss army knife!!##
##by ashish singh ##
### @ashish173 ###

!SLIDE code small commandline incemental
# Index #
* Introduction/Basic functionality
* How to use in Ruby?
* Some Advanced Functionality
* Real World Use Cases
* AND SOME HACKING!!!

!SLIDE code small
# INTRODUCTION #
* A nice way to match patterns
* Describe patterns in a string
* Used for testing presence of patterns 
* And also extracting matched patterns

!SLIDE code small 
# But Y USE **REGEX** Y NOT FIND??? #
* Find is good for simple words 
* Find will fail for more complex patterns
* Find is something we would be not be talking 
  about during this talk.
* Find can _find_ NEW YORK **but not** N.Y.C., N.Y., NY,
  nyc (and believe me thats the least you can do 
  with regexes!!)

!SLIDE code small bullet incremental
# Ruby Regexes!!!  
    $ >>> /Invest/.match("Investigations")
      => #<MatchData "Invest" >

    $ >>> /class/.match("you use classes to wrap data and functions")
      => #<MatchData "class">

    $ >>> /W[aeiou]rd/.match("Word")
      => #<MatchData "Word"> 
    
!SLIDE code small bullet incremental
#BASICS OF REGULAR EXPRESSIONS #
* A regex is usually delimeted with a forward 
  slash(/)

* /pattern/ =~ 'pattern in coral reefs'

* / holds the pattern to be matched / 

* /pattern/.match , 'match' is method that matches 
  pattern and returns a MatchData object.


!SLIDE code small bullet incremental
#BASICS OF REGULAR EXPRESSIONS #
* MatchData object is an object that behaves 
  similar to a list 

* >>> m1 = /Ruby/.match("I am in Love with Ruby and Python")
  => #\<MatchData "Ruby">
  >>> m1[0] = "Ruby"

 
!SLIDE code small bullet incremental
#META CHARACTERS AND ESCAPES #
* (, ), {, }, [, ], .(period), ?, *, + are meta 
  characters.

* They have specific meaning in a pattern.

* To match them they must be escaped with a 
  \(backslash).

* /def fun\\(\\)/.match("def fun() print 'just a function'")
  => #\<MatchData "def fun()">

* /1 \\+ 2 = 3\\?/.match('Does 1 + 2 = 3?')
  => #<MatchData "1 + 2 = 3?">

!SLIDE code small centre
# META CHARACTERS MYSTRY #

!SLIDE code small bullet incremental
# Parentheses -> ( )  #

!SLIDE code small bullet incremental
# ( parentheses ) #
* Parentheses can be used for capturing

* /ash(\\w+) f\\1/.match("ashish fish`")
  => #<MatchData "ashish fish" 1: "ish">

* we captured "ish" using parens

* also used for grouping more on that in coming
  slides.

!SLIDE code small bullet incremental
# Square Brackets -> [ ]  #

* Square brackets are mainly used to delimit
  character classes.

!SLIDE code small bullet incremental
# CHARACTER CLASSES #

* A Character class is delimited with square 
  brackets [, ].

* Lists all characters that may appear at that 
  point in the match.

* /J[aeisou]shile/.match("we are a group of Joshile")
  => #<MatchData "Joshile">

* /ashish[1273]+/.match("ashish173 is my github handle")
  => #<MatchData "ashish173">

!SLIDE code small bullet incremental
#  Hyphen( - )  #
* Hyphen is a metacharacter used for denoting an
  inclusive range of characters.

* [a-f] is equivalent [abcdef]

* [0-9] is equivalent to [0123456789]

* If the first character is ^ (caret) then 
  then the class is inverted.

* Now it will match any character except those
  named


!SLIDE code small bullet incremental
# More Metacharacters #

* /./ - Any character except a newline

* /./m - Same as above but for multiline

* /\w/ - A word character([a-zA-Z0-9_]) 

* /\W/ - A non-word character([^a-zA-Z0-9_])

* /\d/ - A digit character([0-9])

!SLIDE code small bullet incremental
# More Metacharacters  #

* /\D/ -A non digit character

* /\h/ -A hexdigit character

* /\H/ -A non-hexdigit character

* /\s/ -A white character 

* /\S/ -A non-whitespace character


!SLIDE code small bullet incremental
# REPETITIONS #

* All the metacharacters can be followed by 
  a repitition metacharacter to specify how
  many times they need to occur.

* Such metacharacters are called quantifiers.

* /Jo[a-z]+/.match("Joshsoftware is a ruby shop")
  => #<MatchData "Joshsoftware">


!SLIDE code small bullet incremental
# REPETITIONS  #

* **+**  in last example is for one or more 
  occurrence of any character b/w a to z.

* /Jo[a-z]*/.match("Jo bhi main kehna chahun")
  => #<MatchData "Jo"> 

* **\*** in above example is for zero or more
  occurrences of any character b/w a to z.

* More Quanifiers in next slide.


!SLIDE code small bullet incremental
# QUANTIFIERS #

* **\*** - Zero or more times

* **\+** - One or more times 

* **?** - Zero or more times **optional**

* **\{n\}**  - Exactly n times

* **\{n,\}** - n or more times


!SLIDE code small bullet incremental
# QUANTIFIERS #

* **\{,m\}** - m or less times

* **\{n,m\}** - Atleast n and at most m times

* A greedy metacharacter can be made lazy by
  following it with ?.

* /<.+>/.match("\<a\>\<b\>")
  => #\<MatchData "\<a\>\<b\>">

* /<.+?>/.mathc("\<a\>\<b\>")
  => #\<MatchData "\<a\>">    made lazy by adding '?'  

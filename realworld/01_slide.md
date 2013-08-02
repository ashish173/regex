
!SLIDE code small bullet incremental
# REAL WORLD USE OF REGULAR EXPRESSIONS #

* Validating EMAILS

* Validating International Phone Numbers

* Validate Traditional Date formats

* Limit the length of text

* Validate Credit Card Numbers

!SLIDE code small bullet incremental
# VALIDATING EMAILS #

* email simple form ashish@joshsoftware.com

* some words + @ symbol + again some words

* /^\S+@\S+$/.match("ashish@joshsoftware.com")
  => #<MatchData "ashish@joshsoftware.com">

* But it will fail for my other email add
  aitashish173@gmail.com

* no worries regexes to rescue

  
!SLIDE code small bullet incremental
# VALIDATING EMAILS #

* /^[A-Za-z0-9+_\-]+@[A-Za-z0-9+_\-]+$/.match
  ("ashish_173@joshsoftware12.com")
  => #<MatchData "ashish_173@joshsoftware12.com">

* but this will fail for ashish.singh@gmail.com
  
* /^[A-Za-z0-9+_.\-]+@[A-Za-z0-9+_.\-]+$/.match
  ("ashish_1.73@joshsoftware12.com")
  => #<MatchData "ashish_1.73@joshsoftware12.com">

* There can be many more validations in email.


!SLIDE code small bullet incremental
# VALIDATE INTERNATIONAL PHONE NUMBERS #

* These formats include. 1234567890, 123-456-7890
  123.456.7890, (123) 456 7890

* an optional paren enclosed number 
  \\(?\(\[0-9\]\{3\}\)\\)?

* period, space, hypen between numbers optional 
  [-. ]?

* ending with 4 numbers \[0-9\]\{4\}$
  

!SLIDE code small bullet incremental
# FINAL VALIDATION #

*  ^(\\(\?\(\[0-9\]\{3\}\)\\)?\[-. \]?\(\[0-9\]\{3\}\)\[-. \]\)?
   \([0-9]\{4\}\)$
 

!SLIDE code small bullet incremental
# CLEANING TEXT #

* You are given a text and you have to remove empty lines
    text = "   hello   world
    the space   

    is nice here!    "
    regex = /\s+/ # matches for spaces
    text.gsub(regex, ' ')   
    # =>  hello world the space is nice here! 

!SLIDE code small bullet incremental
# CLEANING TEXT #

* gsub\(pattern, replace \)    

* gsub replaces in the string the pattern 
  that matches

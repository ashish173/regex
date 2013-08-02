!SLIDE code small bullet incremental
# CAPTURING #

* /\[csh\]\(\.\.\) \[csh\]\\1/.match("The cat sat in the hat")
  => => #<MatchData "cat sat" 1:"at">

* a sub part of pattern can be captured by parens

* Within the pattern we can use \n to refer to 
  capture and MatchData[n] outside the pattern.

* MatchData[1] = "at"

!SLIDE code small bullet incremental
# CAPTURING #
* capture group can be referred by name when defined with
  \(?\<name\>\)

* /\$\(?\<dollars\>\d+\)\.\(?\<cents\>\\d\+)/.match("$3.67")
  => #<MatchData "$3.67" dollars:"3" cents:"67">

* named groups can be backrefernced with \k<name>; 
  name is the group name

* /\(?\<wel>\[aeiou\]\)\.\\k\<wel\>\.\\k\<wel\>/.match("ototomy")
  => #<MatchData "ototo" vowel:"o">

* when =~ operator is used captured text is assigned to 
  local varables.


!SLIDE code small bullet incremental
# CAPTURING #

* /\\$\(\?\<dollars\>\\d\+\)\.(?<cents>\d+)/ =~ "$3.67" 
  => dollars #=> "3"

* variable dollars is assigned value 3


!SLIDE code small bullet incremental
# CAPTURING #
* \(?:..\) construct provides grouping without capturing
  
* It combines terms without creating a backreference.

* Improves Performance.

* /I(n)ves(ti)ga\2ons/.match("Investigations")
  => #<MatchData "Investigations" 1:"n" 2:"ti">

* /I(?:n)ves(ti)ga\1ons/.match("Investigations")
  => #<MatchData "Investigations" 1:"ti">

* the first group is omitted 

!SLIDE code small bullet incremental
# GROUPING #

* Parens are used for grouping.

* /\[aeiou\]\\w\{2\}/.match("Caenorhabditis elegans")
  => #<MatchData "aen">

* /\(\[aeiou\]\\w\)\{2\}/.match("Caenorhabditis elegans")
  => #<MatchData "enor" 1:"or">

* MatchData[1] = "or" the last match


!SLIDE code small bullet incremental
# ALTERNATION #

* The Vertical bar metacharacter(|) combines two expression 
  into a single one.

* Either of the two expressions are matched.

* /\\w\(and|or\)\\w/.match("Feliformia")
  => #<MatchData "form" 1:"or">

* /\\w\(and\|or\)\\w/.match("furandi")
  => #<MatchData "randi" 1:"and">


!SLIDE code small bullet incremental
# ANCHORS #

* Anchors are metacharacters that match the 
  zero-width (positions) between character.

* ^ \(Caret\) - matches begining of line

* $ \(dollar\) - Matches end of line

* \\A - Matches begining of string

* \\Z - Matches end of string. 
 
!SLIDE code small bullet incremental
# ANCHORS #
* \(?=pat\) - Positive lookahead assertion 

* \(?!pat\) -Negative lookahead assertion

* \\B - matches non-word boundaries

* /real/.match("surrealist")
  => #<MatchData> "real"

* /\\Areal/.match("surrealist")
  => #nil


!SLIDE code small bullet incremental
# ANCHORS #

* /\Band/.match("Supply and Demand") 
  => #<MatchData "and">





!SLIDE code small bullet incremental
# OPTIONS #

* The end delimiter for regexp can be followed 
  options which control how the pattern will match

* /pat/i - Ignore Case

* /pat/m - Treat a newline as a character matched

* /pat/x - Ignore whitespace and comments in pattern

* /pat/o - Perform #\{\} interpolation only once


!SLIDE code small bullet incremental
# OPTIONS EXAMPLES #

* /(?i:J)osh/.match("josh")
  => #<MatchData "josh"> 



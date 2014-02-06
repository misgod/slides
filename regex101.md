<img src="http://screwdesk.com/wp-content/uploads/2013/06/regula_exp.jpg" width="800" height="500"/>


##Regular Expression 101 


---
###  What is Regular  Expression

A regular expression (abbreviated **regex** or **regexp**) is a sequence of characters that forms a search pattern, mainly for use in pattern matching with strings, or string matching,i.e. "find and replace"-like operations. 

~~ Wikipedia

---
### What does it mean?

<br/>


```
<a\s+href=(?:"([^"]+)"|'([^']+)').*?>(.*?)</a>
```

---
## Why learn Regex??
---

<img src="http://imgs.xkcd.com/comics/regular_expressions.png" width=800 height=700>
---
### Why use Regex??

* <span class="fragment">It's  short, fast and fun</span>

* <span class="fragment">It save your time to get things done</span>

* <span class="fragment">In everywhere and portable</span>  

* <span class="fragment">And ...</span>

---

### Make you more like a Geek 

<img src="http://webpages.charter.net/mark_turner/matrix/matrix07.jpg" width=800 height=400>
Awesome!!
---

## Case Study

---
### One day ...
![](http://img.gawkerassets.com/img/18ix6b4gf1akujpg/k-bigpic.jpg)

You got a bunch of data includes some "phone numbers"-like, and you need to validate each numbers and store it with exact format

---
### A piece of Input Data
- 022748222
- 9944-4-33323
- (03)3394937
- (03-4284959
- ((01))936483-11
- 06-48694-1
- 06-7563821
- 07-3939889
- 09-678463a
- 09--238-49
- 03-7633-345
- bb-7633-345
- ...
- ...

<https://db.tt/SaHU9ha4>
---
### Requirement

* Input: 
 - a bunch of data including phone numbers with different formats

* Validate: 
 - \#########| 062345678  => O
 - \##-#######| 06-2345678 => O
 - \##-###-####| 06-234-5678 => O
 - \(##)#######| (06)2345678 => O
 - \(##)###-####| (06)234-5678 => O
 - \(##)-###-####| (06)-234-5678 => O
 - Otherwise => X

* Output: 
 - \#########  ex.062345678

---
### How to do?
![Thinking](http://1.bp.blogspot.com/-oM6-u0uSUcQ/Tbmt2m6PVAI/AAAAAAAAB0s/vgyuV3Zrxos/s1600/why.jpg)


---
## We'll be back to talk it later
---

## Let's get started with Regex

---
## One thing you should know  ...  
<br/>
Regex has existed since 1950s. Today, there are many Regex flavors.  
Different  flavors have different implementation.  
You can use below link to check differences between regex flavors

http://www.regular-expressions.info/refflavors.html
---
### Characters

* Characters
   - letters: <font color="yellow">**A to Z, a to z**</font>
   - numbers: <font color="green">**0 to 9**</font>
   - symbols: <font color="red">**! @ # % &** ...etc</font>

* Special Characters
   - <font color="yellow">**( ) [ ] \ ^ $ . | ? * + **</font>
   - escape them with a backslash=> **\**
 
* Non-Printable Characters
   - <font color="green">**\t  \r  \n \a \e \f \v**</font>  
 
* Literal Characters
   - Any character except Special Characters
---
<br/> 

```
book
```

This is a <font style="BACKGROUND-COLOR: blue">book</font>



```
Book  #case sensitive
```

This is a book
 


```
is
```

Th<font style="BACKGROUND-COLOR: blue">is</font> <font style="BACKGROUND-COLOR: blue">is</font> a book</font>



```
book!
```

This is a <font style="BACKGROUND-COLOR: blue">book!</font>


```
book\(18x\) #escape special characters
```

This is a <font style="BACKGROUND-COLOR: blue">book(18x)</font>.  

```
台語
```
貢<font style="BACKGROUND-COLOR: blue">台語</font>嘛A通


---
### Character Classes
Matches **ONLY** one character on a set of characters

* <font color="yellow">[Aa]</font> :  matches either 'A' or 'a' 

* <font color="yellow">[a-z]</font> : matches a-z

* <font color="yellow">[A-Z]</font> : matches A-Z

* <font color="yellow">[0-9]</font> : matches 0-9

* <font color="yellow">[^Aa]</font> : matches anything but 'A' and 'a'

* <font color="yellow">[A^a]</font> : matches only 'A', '^ ,'a'

---
```
[0-9]
```
<font style="BACKGROUND-COLOR: blue">1</font>+<font style="BACKGROUND-COLOR: blue">1</font>=<font style="BACKGROUND-COLOR: blue">2</font>

```
[1-5]
```
<font style="BACKGROUND-COLOR: blue">3</font>+<font style="BACKGROUND-COLOR: blue">4</font>=<font>9</font>


```
[dD]og  #alternative-- (d|D)og
```
I love <font style="BACKGROUND-COLOR: blue">dog</font>. <font style="BACKGROUND-COLOR: blue">Dog</font>s are human's best friend


```
[a-zA-Z]
```
<font style="BACKGROUND-COLOR: blue">a</font><font style="BACKGROUND-COLOR: green">b</font>123<font style="BACKGROUND-COLOR: blue">A</font><font style="BACKGROUND-COLOR: green">B</font>

```
[^a-zA-Z]
```
abc<font style="BACKGROUND-COLOR: blue">1</font><font style="BACKGROUND-COLOR: green">2</font><font style="BACKGROUND-COLOR: blue">3</font>ABC


```
[c-e]
```
ab<font style="BACKGROUND-COLOR: blue">c</font><font style="BACKGROUND-COLOR: green">d</font><font style="BACKGROUND-COLOR: blue">e</font>fg


---
### Shorthand Classes


* <font color="yellow">**\d**</font> == <font color="green">[0-9]</font>: digits

* <font color="yellow">**\w**</font> == <font color="green">[0-9a-zA-Z\_]</font>: alphanumeric or \_

* <font color="yellow">**\s**</font> == <font color="green">[ \t(?:\n|\r\n)]</font>: whitespace

* <font color="yellow">**\D, \W, \S**</font>: The above BUT negated


---
```
\d
```
<font style="BACKGROUND-COLOR: blue">1</font>+<font style="BACKGROUND-COLOR: blue">1</font>=<font style="BACKGROUND-COLOR: blue">2</font>

```
\D
```
1<font style="BACKGROUND-COLOR: blue">+</font>1<font style="BACKGROUND-COLOR: blue">=</font>2


```
\w
```
<font style="BACKGROUND-COLOR: blue">a</font>=<font style="BACKGROUND-COLOR: blue">b</font>

```
\W 
```
a<font style="BACKGROUND-COLOR: blue">=</font>b


```
\s
```
a<font style="BACKGROUND-COLOR: blue"> </font>b<font style="BACKGROUND-COLOR: blue"> </font>c

```
\S
```
<font style="BACKGROUND-COLOR: blue">a</font> <font style="BACKGROUND-COLOR: blue">b</font> <font style="BACKGROUND-COLOR: blue">c</font>

---
### Dot <font color="yellow">**.**</font>

* Matches any single character except line break characters.   
<br/>
* Most regex flavors have an option to make the dot match line break characters too.  
<br/>
* <font color="yellow">T.m</font> =>  <font style="BACKGROUND-COLOR: blue">Tim</font> and <font style="BACKGROUND-COLOR: blue">Tom</font>

---
### Alternation <font color="yellow">|</font>


*  match either the left side, or the  right side of pattern.   

*  <font color="yellow">abc|xyz</font> =>  <font style="BACKGROUND-COLOR: blue">abc</font>def<font style="BACKGROUND-COLOR: blue">xyz</font>xbz  
---
### Anchors

* **^** : Matches at the start of the string     

 -  <font color="yellow">^[Aa]</font> =>  <font style="BACKGROUND-COLOR: blue">A</font>n apple a day  

 -  <font color="yellow">^app</font> => An apple a day  

 -  <font color="yellow">^An a</font> => <font style="BACKGROUND-COLOR: blue">An a</font>pple a day  
 -  <font color="yellow">\^a</font> => <font style="BACKGROUND-COLOR: blue">^a</font>bcabc
 

* **$** : Matches at the end of the string
 -  <font color="yellow">.$</font> => An apple a da<font style="BACKGROUND-COLOR: blue">y</font>

 -  <font color="yellow">day$</font> => An apple a <font style="BACKGROUND-COLOR: blue">day</font>

 -  <font color="yellow">d\$</font> => abcdabc<font style="BACKGROUND-COLOR: blue">d$</font>

---
### Word Boundaries

* **\b** : matches between a \w and \W
  -  <font color="yellow">\ba</font> => <font style="BACKGROUND-COLOR: blue">a</font>bc def <font style="BACKGROUND-COLOR: blue">a</font>aa  

  -  <font color="yellow">\ba\b</font> => An apple <font style="BACKGROUND-COLOR: blue">a</font> day     
* **\B** : The above BUT negated
  -  <font color="yellow">\Ba</font> => An apple a d<font style="BACKGROUND-COLOR: blue">a</font>y

  -  <font color="yellow">\Bat\B</font> => vac<font style="BACKGROUND-COLOR: blue">at</font>ion evacu<font style="BACKGROUND-COLOR: blue">at</font>ion at that time ate my evalu<font style="BACKGROUND-COLOR: blue">at</font>ion

---
### Quantifiers

* **{n}** : matches exactly n times
  - <font color="yellow">a{4}</font> => aaa <font style="BACKGROUND-COLOR: blue">aaaa</font> <font style="BACKGROUND-COLOR: blue">aaaa</font>a

* **{n,}** : matches n or more times
  - <font color="yellow">a{4,}</font> => aaa <font style="BACKGROUND-COLOR: blue">aaaa</font> <font style="BACKGROUND-COLOR: blue">aaaaa</font>

* **{n,m}** : matches between n and m times
  - <font color="yellow">a{3,4}</font> => <font style="BACKGROUND-COLOR: blue">aaa</font> <font style="BACKGROUND-COLOR: blue">aaaa</font> <font style="BACKGROUND-COLOR: blue">aaaa</font>a
---
### Quantifiers
* **\***: same as {0,}
 - <font color="yellow">a\d*b</font> => <font style="BACKGROUND-COLOR: blue">ab</font> <font style="BACKGROUND-COLOR: blue">a3b</font> a<font style="BACKGROUND-COLOR: blue">a33b</font>b

* **+**: same as {1,}
  - <font color="yellow">a\d+</font> => ab<font style="BACKGROUND-COLOR: blue">a01</font>ba<font style="BACKGROUND-COLOR: blue">a3</font>b

* **?**: same as {0,1}
  - <font color="yellow">T.?m</font> => Toom and <font style="BACKGROUND-COLOR: blue">Tom</font> and <font style="BACKGROUND-COLOR: blue">Tm</font>
---
### Regex match is greedy   
The engine will always try to match as much as possible

<br/>

<font color="yellow"><.+></font> => <font style="BACKGROUND-COLOR: blue">&lt;div&gt;Hello World!&lt;/div&gt;</font>

<br/>

<font color="yellow">and\S+</font> => <font style="BACKGROUND-COLOR: blue">andy</font> and <font style="BACKGROUND-COLOR: blue">android</font> 

---

### Make It Lazy by **?**

<br/>

<font color="yellow"><.+?></font> => <font style="BACKGROUND-COLOR: blue">&lt;div&gt;</font>Hello World!<font style="BACKGROUND-COLOR: blue">&lt;/div&gt;</font>

<br/>

<font color="yellow"><[^/].+?></font> => <font style="BACKGROUND-COLOR: blue">&lt;div&gt;</font>Hello World!&lt;/div&gt;

<br/>

<font color="yellow">and\S+?</font> => <font style="BACKGROUND-COLOR: blue">andy</font> and <font style="BACKGROUND-COLOR: blue">andr</font>oid 

---
### Capturing Groupings **(regex)**

<br/>

* <font color="yellow">(\d+)-(\d+)-(\d+)</font> => <font style="BACKGROUND-COLOR: blue">333</font>-<font style="BACKGROUND-COLOR: blue">444</font>-<font style="BACKGROUND-COLOR: blue">55</font>
  
  - Group[1] = 333
  
  - Group[2] = 444
  
  - Group[3] = 55

* <font color="yellow">([\w\S]+)@([\w\-\.]+\w+)</font> => <font style="BACKGROUND-COLOR: blue">sam.lee@fake-mail.com.tw</font>

  - Group[1] = sam.lee

  - Group[2] = fake-mail.com.tw

---
### Non-capturing Groupings **(?:regex )**

<br/>

* <font color="yellow">(\d+)-(?:\d+)-(\d+)</font> => <font style="BACKGROUND-COLOR: blue">333</font>-<font style="BACKGROUND-COLOR: blue">444</font>-<font style="BACKGROUND-COLOR: blue">55</font>
  
  - Group[1] = 333
   
  - Group[2] = 55

* <font color="yellow">([\w\S]+)@(?:[\w\-\.]+\w+)</font> => <font style="BACKGROUND-COLOR: blue">sam.lee@fake-mail.com.tw</font>

  - Group[1] = sam.lee

---
### Backreference **\\**

* <font color="yellow">(\d+)=\1</font> => <font style="BACKGROUND-COLOR: blue">1=1</font> 1=2 <font style="BACKGROUND-COLOR: blue">4=4</font> 2=3
  
  - Group[1] in Match[1] = 1

  - Group[1] in Match[2] = 4

---
### Positive Lookahead **(?=regex)**

<br/>

* <font color="yellow">Ted(?=dy)</font> => Ted has a <font style="BACKGROUND-COLOR: blue">Ted</font>dyBear
  



---
### Negative Lookahead **(?!regex)**

<br/>

* <font color="yellow">Ted(?!dy)</font> => <font style="BACKGROUND-COLOR: blue">Ted</font> has a TeddyBear


---
### Positive Lookbehind **(?<=regex)**

<br/>

* <font color="yellow">(?<=Bat)man</font> => Superman Bat<font style="BACKGROUND-COLOR: blue">man</font> Ironman
  

---
### Negative Lookbehind **(?<!regex)**

<br/>

* <font color="yellow">(?<!Bat)man</font> => Super<font style="BACKGROUND-COLOR: blue">man</font> Batman Iron<font style="BACKGROUND-COLOR: blue">man</font>
  

---
### Mode Modifiers

#### depends on your tool

* **/i** : case-insensitive match

* **/m** : Multu-line mode

* **/g** : match all possible not just first one

---

## Back to the Case Study

---
### A piece of Input Data
- 022748222
- 9944-4-33323
- (03)3394937
- (03-4284959
- ((01))936483-11
- 06-48694-1
- 06-7563821
- 07-3939889
- 09-678463a
- 09--238-49
- 03-7633-345
- bb-7633-345
- ...
- ...

---
### Requirement

* Input: 
 - a bunch of data including phone numbers with different formats

* Validate: 
 - \#########| 062345678  => O
 - \##-#######| 06-2345678 => O
 - \##-###-####| 06-234-5678 => O
 - \(##)#######| (06)2345678 => O
 - \(##)###-####| (06)234-5678 => O
 - \(##)-###-####| (06)-234-5678 => O
 - Otherwise => X

* Output: 
 - \#########  ex.062345678
---
# Live Demo

Note:(?:^\((?<=\()(\d{2})(?=\))\)|^(\d{2}))-?(\d{3})-?(\d{4})

---
### Scala
```
  def parsePhones(url:String) = {
    val source  = scala.io.Source.fromURL(url)

    val pattern = """(?:^\((?<=\()(\d{2})(?=\))\)|^(\d{2}))-?(\d{3})-?(\d{4})""".r

    for{
      line <- source.getLines()
      m<-pattern.findFirstMatchIn(line)
    } yield m.subgroups.filter(_ != null).reduce(_+_)
  }

```

```
val url = "https://dl.dropboxusercontent.com/u/67374708/slides/regex101/phones.txt"
parsePhones(url).foreach(println)
```
---
# Live Demo
### grep log

Note: cat xxx|grep  "\s\([VDIWEF]\sFrisbee\|E\sAndroidRuntime\|F\|^StatusBar.NetworkController\)\s"

---

# Q & A

---

### Thank You!

<img src="http://webpages.charter.net/mark_turner/matrix/matrix07.jpg" width=800 height=400>

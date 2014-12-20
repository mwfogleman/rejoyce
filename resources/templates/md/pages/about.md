{:title "About"
 :layout :page
 :page-index 0
 :navbar? true}

When I was a child, my favorite punctuation mark was the em-dash. I
spoke with the em-dash, I understood with the em-dash, I thought with
the em-dash. To be sure, I still like the em-dash—this very sentence
has two em-dashes in it—but when I became a man, I picked up some
parentheses, and I started to like them. And now they are my favorite
punctuation mark!  

So it could be said that I like to do LISt Processing. I have been
known to use [Emacs](https://www.gnu.org/software/emacs/)
and [Clojure](http://clojure.org/) to do so.  

Usually, when you introduce people to LISt Processing, you use a book
like the Little Schemer. Here is a gratuitous picture of some animals,
which originates from a certain sequel to the Little Schemer:  
  
![The Fun Never Ends...](/files/fun.png)

I love the Little Schemer. If you haven't read it, you totally should!
But I will admit being tickled by the idea of using another book as an
introduction.  

In truth, this "book" is really a series of three essays
on "Lisp", by [Douglas R. Hofstadter](https://en.wikipedia.org/wiki/Douglas_Hofstadter)
(a.k.a. Egbert B. Gebstadter):  

* Atoms and Lists
* Lists and Recursion
* Recursion and Generality

You can find all three in the collection "Metamagical Themas." As a
bonus, they also have some cute drawings of animals. Here is "the
homely Inner Glazunkian porpuquine":  

![The homely Inner Glazunkian porpuquine](/files/porpuquine.png)

Here is a Clojure version of a neat function that Mr. Hofstadter
adduces in the first essay:  

```
(def readers-digest-condensed-version (juxt first last))
```

For best results, type this in character-for-character in your
[friendly neighborhood REPL](http://www.tryclj.com/) (REACTIVE
ENVIRONMENT for PROGRAMMING LANGUAGES).  

Then try calling it on the vector [1 2 3 4 5], like so:  

```
(readers-digest-condensed-version [1 2 3 4 5])
```

Pressing ENTER should yield the vector [1 5]. But it will work for any
sequence, of any size or shape!  

Go ahead and take a few minutes to follow Mr. Hofstadter's advice, and
apply the readers-digest-condensed-version function "to the entire
text of [James Joyce](https://en.wikipedia.org/wiki/James_Joyce)'s
*[Finnegans Wake](https://en.wikipedia.org/wiki/Finnegans_Wake)*
(treating it as a big long [sequence] of words)."

You'll soon see that the result should be "the shorter [sequence] (riverrun the)."  

Finally, he adds the obvious next step:  

> It would be nice as well as useful if we could create an inverse operation to readers-digest-condensed-version called rejoyce that, given any two words, would create a novel beginning and ending with them, respectively—and such that James Joyce would have written it (had he thought of it). Thus execution of the Lisp statement (rejoyce ‘Stately ‘Yes) would result in the Lisp genie generating from scratch the entire novel Ulysses. Writing this function is left as an exercise for the reader. To test your program, see what it does with (rejoyce ‘karma dharma).  

Although any self-respecting Lisper can implement the rejoyce function
in a matter of minutes, I have done so in a particularly elegant way,
and I hope to blog about it here soon...

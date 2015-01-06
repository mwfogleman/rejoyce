{:title "2014: A Year of Emacs"
 :layout :post
 :tags ["Anki" "Emacs"]
 :toc false}

My Emacs "birthday" is January 21, 2014. That's right-- I just started using Emacs this year! While it's not quite my one-year birthday, I thought I'd take advantage of the annual review blogging tradition to do a retrospective on my first year in Emacs. Note: much of the following chronology takes place during an extended romp through Asia.

I installed Arch Linux in the Fall of 2013. When using Linux, you often need to edit configuration files. The friend who helped me set me up with Vim. I learned the basics--how to insert, save, and quit--and not much else.

![Arch on a bench](/files/seattle_arch.jpg)

In January, I decided it might be fun to give Emacs a try. Here is a picture of Marina Bay in Singapore, taken just before or while I did the Emacs tutorial:

![Marina Bay in Singapore, just before or during my Emacs birth](/files/singapore_emacs.jpg)

As a life-long user of keyboard shortcuts, I appreciated Emacs' notation for key bindings. The tutorial begins with basic cursor controls; easy enough, but nothing exciting. I could see the line, sentence, and buffer equivalents being useful. But my jaw dropped when it taught me C-t, transpose-chars. I knew that mastering just that command would probably save me a lot of pain and typos, and that was probably the least of what Emacs could do.

<blockquote class="twitter-tweet" lang="en"><p><a href="https://twitter.com/hashtag/Emacs?src=hash">#Emacs</a>: using transpose-chars is a litmus test. If you care enough to save keystrokes to internalize C-t, then you must be a power user.</p>&mdash; Fredrik Appelberg (@appelberg) <a href="https://twitter.com/appelberg/status/538282100911529984">November 28, 2014</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

While the Emacs tutorial probably isn't meant to take more than an hour or two on the first try, it took me probably twice as long. This was because I made [Anki](http://ankisrs.net/) cards. Some people say that Emacs' learning curve is steep. For myself, I've found Emacs' learning curve to be gentle, but (pleasantly) endless. Then again, it was probably making Anki cards that made the learning curve less steep for me.

A variation of this card was probably one of my first Emacs cards:

<a href="https://books.google.com/books?id=eoI7dNY1d0YC&printsec=frontcover&dq=learning+gnu+emacs&hl=en&sa=X&ei=EcWhVLq1CIbQggTWhYKYCw&ved=0CB8Q6AEwAA#v=onepage&q=most%20common%20typo&f=false">
![Anki card: transpose-chars 1](/files/c-t1.png)
</a>

[Cloze](https://en.wikipedia.org/wiki/Cloze_test) [deletion](http://www.supermemo.com/articles/20rules.htm) [cards](http://ankisrs.net/docs/manual.html#cloze-deletion) like this one are very convenient for this kind of thing. One reason is that it's easy to add [new, related information](https://twitter.com/camdez/status/543953065645076481) later:

<a href="https://twitter.com/camdez/status/543953065645076481">
![Anki cards transpose-chars 2](/files/c-t2.png)
</a>

In February, the battery on my little Arch laptop died. I spent most of the month without a laptop, waiting for a new battery to arrive by mail. I borrowed my friend and travel partner's machine to review my Anki cards. Still, I did manage to have a little time to develop my Emacs-fu.

In Hanoi, the hotel room we stayed in had a (virus-ridden) Windows machine. What else could I do but install Emacs? At this time, my Emacs configuration was not that complex, so it wasn't worth adapting. As it turned out, that time with a bare Emacs proved especially helpful for mastering some of the key Emacs concepts that I hadn't quite made use of yet; in particular, I got the hang of using multiple buffers in one session. By the the end of February, my new battery had arrived, and I was back in the Emacs saddle. 

In March, I converted my [my Emacs configuration](https://github.com/mwfogleman/config/blob/master/home/.emacs.d/michael.org) to an Org-literate format, and started tracking it with Git. This was really the first project that I used Git for, and it gave me an opportunity to learn Git.

<blockquote class="twitter-tweet" lang="en"><p>Thank you Magit for teaching me git <a href="https://twitter.com/hashtag/emacs4life?src=hash">#emacs4life</a></p>&mdash; ionrock (@ionrock) <a href="https://twitter.com/ionrock/status/547076969754415104">December 22, 2014</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></Script>

The other highlight of March was starting to learn a little Elisp. I found Robert Chassell's "[An Introduction to Programming in Emacs Lisp](https://www.gnu.org/software/emacs/manual/html_node/eintr/index.html)" especially helpful. Chassell's overview and Org-mode's fantastic documentation helped me to [write](https://twitter.com/mwfogleman/status/442611399206789120) my first significant piece of Elisp (some org-capture templates).

April started off with a bang when my Emacs configuration was [featured in a major motion picture, Tron Legacy](http://jtnimoy.com/blogs/projects/14881671). But that wasn't nearly as exciting as making my first major mode, [tid-mode](https://github.com/mwfogleman/tid-mode).

In late June, Artur Malabarba launched his Emacs blog, Endless Parentheses. One of his early posts was about [hungry-delete](http://endlessparentheses.com/hungry-delete-mode.html). I was excited about it, but found that it did not work with transient-mark-mode. Artur encouraged me to write a fix. I was very excited when Nathaniel Flath, the maintainer, agreed to merge my patches into hungry-delete. At about the same time, Artur [posted an adapted version of my narrow-or-widen-dwim function to Endless Parentheses](http://endlessparentheses.com/emacs-narrow-or-widen-dwim.html). Sacha Chua, Nathaniel Flath, and some other Emacs Lisp hackers also offered suggestions.

At the end of July, I started learning Clojure, and added an initial CIDER configuration. While reading the Clojure Cookbook, I decided to hack out [a function that turned the pages](https://github.com/clojure-cookbook/clojure-cookbook#exploring-the-book). Ryan Neufeld, one of the co-authors, merged my pull request, and a while later, I saw my function mentioned on Planet Clojure.

In October, I purchased a Mac for a Clojure contracting job. (Knowing Emacs helped me get the job!) Adding the :ensure keyword to my use-package declarations made the Emacs configuration portion of my OS X set-up process near-instant and pain-free. It was a really cool feeling to be using the same Emacs configuration on two different machines. By the end of the month, both were running on the newly-released Emacs 24.4.

Once Emacs 24.4 was out, Artur posted [an Emacs 25 wishlist](http://endlessparentheses.com/big-things-to-expect-from-emacs-25.html) to Endless Parentheses. I responded with this tweet:

<blockquote class="twitter-tweet" lang="en"><p><a href="https://twitter.com/hashtag/Emacs?src=hash">#Emacs</a> 25 wishlist: putting people like @bruceconnor <a href="https://twitter.com/_wilfredh">@_wilfredh</a> <a href="https://twitter.com/sachac">@sachac</a> <a href="https://twitter.com/sanityinc">@sanityinc</a> <a href="https://twitter.com/nicferrier">@nicferrier</a> all in one room for a hackathon...</p>&mdash; Michael Fogleman (@mwfogleman) <a href="https://twitter.com/mwfogleman/status/527430311836418048">October 29, 2014</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

This tweet indirectly led to the happy occasion of the [Emacs Hangouts](http://sachachua.com/blog/2014/10/emacs-hangout-notes/).

That just about brings us to this post. In retrospect, I can't believe it's been less than a year, or that I've learned so much. Thanks to everyone who has helped me so far on the endless path of mastering Emacs, especially Ben, Eric, Sacha Chua, Artur Malabarba, and Bozhidar Batsov.

<a href="https://en.wikipedia.org/wiki/Monomyth">
![Joseph Campbell was a Lisp guru](/files/emacs_monomyth.png)
</a>

I want to close this post out with Sacha's tweet about 2015:

<blockquote class="twitter-tweet" lang="en"><p>What are your Emacs resolutions? In 2015, I want to get the hang of refactoring, syntactical editing, dynamic autocompletion, and testing.</p>&mdash; Sacha Chua (@sachac) <a href="https://twitter.com/sachac/status/544676125478096897">December 16, 2014</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

Like Sacha, I want to learn how to write and run tests in Emacs. I want to learn more about org-mode's features and possible workflows. More broadly, I'd like to make more posts about Emacs, and find other ways to contribute to the Emacs community. I'd like to [learn more about Emacs core development](http://lars.ingebrigtsen.no/2014/11/13/welcome-new-emacs-developers/). In terms of contrib, I'd like to help accelerate the [release](https://github.com/magit/magit/issues/1645) of Magit's ["next" branch](https://github.com/magit/magit/tree/next). Above all, I'm sure I'll keep tweaking my configuration.

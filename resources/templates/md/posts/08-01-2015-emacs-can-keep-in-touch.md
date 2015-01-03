{:title "Emacs can keep in touch"
 :layout :post
 :tags ["Emacs"]
 :toc false}

I've wanted to show a specific Emacs workflow that I've established at
the
[Emacs Hangouts](http://sachachua.com/blog/2014/10/emacs-hangout-notes/)
that I've attended, but thought it might require too much explanation
for an Emacs Hangout. Hence, this post. You might be interested in
this workflow if you regularly edit a specific text file in a
particular way, run an external program with the same parameters. You
might also get some ideas if you're an Emacs-wielding programmer, and
wish Emacs had some particular functionality, but would prefer to use
Bash or another language to give it that functionality.

Some time ago, my friend [Ben](https://github.com/benpence/) started
working on a side project called
"[Keep In Touch](https://github.com/benpence/keepintouch)." The
premise: you have friends, family, and acquaintances that you'd like
to stay in touch with. You maintain a list of those people, how often
you'd like to contact them, and when you last contacted them. Keep In
Touch can then figure out who you are out of touch with. For example,
if you want to talk to someone every 30 days, but it's been 31 days,
then you are out of touch with them, and the program tells you
so. Simple!

Since I started using the program, I've fallen in love with using
it. It has helped me to stay in touch with more people, more
often. Moreover, I
[re-implemented Keep in Touch in Clojure](https://github.com/mwfogleman/keepintouch/tree/clj)
as an exercise. And while Keep in Touch provides a serviceable CLI,
I've worked out a simple Emacs interface for maintaining the database
and viewing the program's output.

It all starts with telling Emacs where it can find the database:

```
(setq keepintouch-datafile "~/Dropbox/keepintouch.data")
```

Next, I needed a way to tell Emacs that I had contacted someone. The
result is an interactive function that asks you who you contacted. It
ordinarily assumes that you contacted the person today, but with a
prefix argument, it asks you for an alternate date. Then it opens the
file and makes the appropriate changes.

```
(defun keptintouch (arg)
  "Request a contact in a keepintouch.data file, and update their last
  contacted date (either today, or, if a prefix is supplied, a user-supplied date.)"
  (interactive "P")
  (let ((contact (read-string "Who did you contact? "))
        (date (if (equal arg nil)
                  (format-time-string "%Y/%m/%d")
                (read-string "When did you contact them? (year/month/date): "))))
    (save-excursion
      (find-file keepintouch-datafile)
      (goto-char (point-min))
      (search-forward contact)
      (forward-line -1)
      (beginning-of-line)
      (kill-line)
      (insert date)
      (save-buffer)
      (switch-to-buffer (other-buffer))
      (kill-buffer (other-buffer)))
    (message "%s was contacted." contact)))
```

"keptintouch" uses *read-string* to ask you who contacted, and, if
need be, when you contacted them. It uses *format-time-string* to
format today's date in the appropriate format.

The body of the function works almost like a keyboard macro. Often,
you can start writing an Elisp function by hitting "C-h k"
(*describe-key*) and finding out what functions are called when you
execute the steps as keystrokes. Another way to do this quickly might
be to make the keyboard macro, run *edit-last-kbd-macro*, and use the
function annotations to read their documentation or make pseudo-code.

One reason that this is a function instead of a keyboard macro is that
it uses some buffer management functions. (All interactive functions
are of course accessible to keyboard macros through keyboard strokes,
which can really save you some time in one-off situations!) It opens
my Keep In Touch database in a new buffer, finds the contact, edits
their last contacted date, saves, closes, and switches the buffers. If
all went well, it reports success with *message*. If for some reason
the contact is non-existent, *search-forward* will throw an error. (If
that happens, or I want to view or edit the datafile manually, I find
it with *ido-recentf-open*.)

All of this is wrapped in *save-excursion*, which is kind of like the
shell commands *popd* and *pushd* except for buffers. In other words,
it does something, and then returns the user to what they were doing
before they executed the function.

Now that I had a way to maintain the database, I needed a way to run
Keep in Touch and view its output, a sorted backlog of people that you
are out of touch with.

The Clojure version of Keep in Touch is designed to be
[exported to a .jar file](https://github.com/technomancy/leiningen/blob/stable/doc/TUTORIAL.md#uberjar). Running
the resulting program from the command line looks like this:

```
# note the special location of the .jar
cd target/uberjar
java -jar keepintouch-0.1.0-SNAPSHOT-standalone.jar ~/Dropbox/keepintouch.data schedule backlog
```

I decided to look at *shell-command*'s documentation to find a way to
run this command and put the results into an output buffer. As it
turns out, *shell-command* is that function. As expected, it takes an
argument for the desired shell-command. But it also allows for two
optional arguments: the name of an output buffer, and the name of an
error buffer.

```
(defun keptintouch-backlog ()
  "Create a buffer with Keep In Touch backlog."
  (interactive)
  (let ((src "~/src/keepintouch/clj/keepintouch")
        (jar "-jar target/uberjar/keepintouch-0.1.0-SNAPSHOT-standalone.jar")
        (cur default-directory)) 
    (cd src)
    (shell-command
     (concat "java " jar " " keepintouch-datafile " schedule backlog")
     "*Keep In Touch Backlog*")
    (cd cur)))
```

You'll see that the concat will expand to the shell command that runs
the .jar, and that it is followed by an appropriate buffer name.

All of this Lisp makes its way to my finger with two key-binds (by way
of [use-package](https://github.com/jwiegley/use-package)'s
[bindkey.el](https://github.com/jwiegley/use-package/blob/master/bind-key.el)):

```
(bind-keys ("C-c k" . keptintouch)
           ("C-c K" . keptintouch-backlog))
```

One variable, two functions, and two keybinds are all it took to make
my life easier and get back to staying in touch with friends. You can
eat your Emacs cake, and have defun, too.


# Table of Contents

1.  [Emacs configuration](#orgc5eec19)
    1.  [todo items](#org557dbc7)
        1.  [clean up beginner recommendations](#orgbabe5da)
2.  [For beginners](#orge4b4757)
    1.  [Basic configurations](#org220a326)
    2.  [Emacs documenation](#orgd6158de)
        1.  [Manual](#org206b9a8)
        2.  [Emacs lisp](#org92ed81d)
    3.  [org-mode](#org30e0a57)
    4.  [configurations by Emacs power users](#org2ecf69a)
3.  [Compiling Emacs 27.1 on Debian Buster (10)](#orgeabe84a)


<a id="orgc5eec19"></a>

# Emacs configuration

This is my emacs configuration. You can read it [here](https://github.com/arthurschutgh/dotemacs/blob/master/arthur.org).

Emacs allows you to do allmost *all* of your computing in one
program. You can read your mail, do calculations, organize your life
with orgmode (agenda, todo items, spreadsheets, lists, notes, plan
projects, literate programming, manage contacts), write documents,
publish to your blog, write programs, etc. The possibilities are
endless. Emacs has its own programming language Emacs Lisp. It allow
you to extend Emacs to your liking.

-   [Multiple cursors and macros](https://www.youtube.com/watch?v=jNa3axo40qM) **impressive!** (4 minute video)
-   [Getting Started With Org Mode](https://www.youtube.com/watch?v=SzA2YODtgK4) **recommended** (hour long presentation)
-   [A Guided Tour of Emacs](https://www.gnu.org/software/emacs/tour/index.html)
-   [Why Emacs? by Bozhidar Batsov](https://batsov.com/articles/2011/11/19/why-emacs/)
-   [The most successful malleable system in history](https://malleable.systems/blog/2020/04/01/the-most-successful-malleable-system-in-history/)


<a id="org557dbc7"></a>

## todo items


<a id="orgbabe5da"></a>

### TODO clean up beginner recommendations


<a id="orge4b4757"></a>

# For beginners

Learning Emacs is a life long journey. Start by reading the
tutorial. Press C-h t to start the tutorial. This means: press
Ctrl-h followed by t.


<a id="org220a326"></a>

## Basic configurations

After reading the tutorial experiment with these basic
customizations:

-   [Emacs configuration in 24 minutes](https://www.youtube.com/watch?v=FRu8SRWuUko)
-   [Configuring Emacs from Scratch - Intro](https://medium.com/@suvratapte/configuring-emacs-from-scratch-intro-3157bed9d040)


<a id="orgd6158de"></a>

## Emacs documenation


<a id="org206b9a8"></a>

### Manual

-   [GNU Emacs manual](https://www.gnu.org/software/emacs/manual/emacs.html)


<a id="org92ed81d"></a>

### Emacs lisp

Leveraging the power of Emacs requires learning Emacs lisp.

-   quick introduction (**recommended**!) [Learn X in Y minutes where X = elisp](https://learnxinyminutes.com/docs/elisp/)
-   GNU manual about learning elisp [An Introduction to Programming in Emacs Lisp](https://www.gnu.org/software/emacs/manual/eintr.html)
-   [GNU Emacs Lisp Reference Manual](https://www.gnu.org/software/emacs/manual/elisp.html) (not really needed by beginners)


<a id="org30e0a57"></a>

## org-mode

After gaining some experience with Emacs you can start
experimenting with org-mode. This package allows you to organize
your life in plain text files.

-   [user manual](https://orgmode.org/#docs)
-   [org-mode setup by norang.ca](http://doc.norang.ca/org-mode.html)


<a id="org2ecf69a"></a>

## configurations by Emacs power users

These configurations are intimidating. I find them useful to gain
new ideas. I didn't know there is even a google-translate package
for Emacs!

-   [Emacs config by Harry R. Schwartz](https://github.com/hrs/dotfiles) (less intimidating)
-   [Emacs config by John Wiegley](https://github.com/jwiegley/dot-emacs)
-   [Sacha Chua's Emacs configuration](https://pages.sachachua.com/.emacs.d/Sacha.html)
-   [Bozhidar's Emacs config](https://github.com/bbatsov/emacs.d)
-   [Emacs config by Magnar Sveen](https://github.com/magnars/.emacs.d)
-   [Emacs config by Aya Igarashi](https://ladicle.com/post/config/)
-   [Emacs config by Doug Davis](https://github.com/douglasdavis/dot-emacs)


<a id="orgeabe84a"></a>

# Compiling Emacs 27.1 on Debian Buster (10)

1.  Install dependencies (execute as root)
    
        apt build-dep emacs
        apt install libjansson-dev libcairo2-dev
2.  Download [emacs-27.1.tar.gz](https://ftp.gnu.org/gnu/emacs/emacs-27.1.tar.gz) from ftp.gnu.org
3.  Extract the archive with
    
        tar -xzf emacs-27.1.tar.gz
4.  Change to emacs-27.1 directory
    
        cd emacs-27.1
5.  Run configure
    
        ./configure --with-cairo --prefix=/usr/local/
6.  Run make and drink coffee
    
        make
7.  Install emacs in `/usr/local/` (execute as root)
    
        make install


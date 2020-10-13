
# Table of Contents

1.  [Emacs configuration](#org3b4dd81)
2.  [Why Emacs?](#org7b6c91a)
3.  [For beginners](#org1198efa)
    1.  [basic configurations](#orga65d520)
    2.  [Emacs documenation](#orgc34d56d)
        1.  [Manual](#org135840e)
        2.  [Emacs lisp](#org4dd9e27)
    3.  [org-mode](#orgd743bda)
    4.  [configurations by Emacs power users](#org4bf403b)
4.  [Compiling Emacs 27.1 on Debian Buster (10)](#org051aca0)


<a id="org3b4dd81"></a>

# Emacs configuration

This is my emacs configuration. You can read it [here](https://github.com/arthurschutgh/dotemacs/blob/master/arthur.org).


<a id="org7b6c91a"></a>

# Why Emacs?

Emacs allows you to do allmost *all* of your computing in one program.

-   [Multiple cursors and macros](https://www.youtube.com/watch?v=jNa3axo40qM) **impressive!**
-   [Getting Started With Org Mode](https://www.youtube.com/watch?v=SzA2YODtgK4) **recommended**
-   [A Guided Tour of Emacs](https://www.gnu.org/software/emacs/tour/index.html)
-   [Why Emacs? by Bozhidar Batsov](https://batsov.com/articles/2011/11/19/why-emacs/)
-   [The most successful malleable system in history](https://malleable.systems/blog/2020/04/01/the-most-successful-malleable-system-in-history/)


<a id="org1198efa"></a>

# For beginners

Learning Emacs is a life long journey. Start by reading the
tutorial. Press C-h t to start the tutorial. This means: press
Ctrl-h followed by t.


<a id="orga65d520"></a>

## basic configurations

After reading the tutorial experiment with these basic
customizations:

-   [Emacs configuration in 24 minutes](https://www.youtube.com/watch?v=FRu8SRWuUko)
-   [Configuring Emacs from Scratch - Intro](https://medium.com/@suvratapte/configuring-emacs-from-scratch-intro-3157bed9d040)


<a id="orgc34d56d"></a>

## Emacs documenation


<a id="org135840e"></a>

### Manual

-   [GNU Emacs manual](https://www.gnu.org/software/emacs/manual/emacs.html)


<a id="org4dd9e27"></a>

### Emacs lisp

Leveraging the power of Emacs requires learning Emacs lisp.

-   quick introduction (**recommended**!) [Learn X in Y minutes where X = elisp](https://learnxinyminutes.com/docs/elisp/)
-   GNU manual about learning elisp [An Introduction to Programming in Emacs Lisp](https://www.gnu.org/software/emacs/manual/eintr.html)
-   [GNU Emacs Lisp Reference Manual](https://www.gnu.org/software/emacs/manual/elisp.html) (not really needed by beginners)


<a id="orgd743bda"></a>

## org-mode

After gaining some experience with Emacs you can start
experimenting with org-mode. This package allows you to organize
your life in plain text files.

-   [user manual](https://orgmode.org/#docs)
-   [org-mode setup by norang.ca](http://doc.norang.ca/org-mode.html)


<a id="org4bf403b"></a>

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


<a id="org051aca0"></a>

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


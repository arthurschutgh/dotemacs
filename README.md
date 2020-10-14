
# Table of Contents

1.  [Emacs configuration](#orgcce8cd2)
2.  [Why Emacs?](#org02c86b9)
3.  [For beginners](#org255386c)
    1.  [basic configurations](#orgf9461be)
    2.  [Emacs documenation](#org9f61908)
        1.  [Manual](#org1d35582)
        2.  [Emacs lisp](#orgb768a9a)
    3.  [org-mode](#org5311c6d)
    4.  [configurations by Emacs power users](#orga1b2c0b)
4.  [Compiling Emacs 27.1 on Debian Buster (10)](#org6c4f78e)


<a id="orgcce8cd2"></a>

# Emacs configuration

This is my emacs configuration. You can read it [here](https://github.com/arthurschutgh/dotemacs/blob/master/arthur.org).

Rant: I have a fair amount of trouble getting language servers
to work. The [Omnisharp server](https://github.com/OmniSharp/omnisharp-emacs) by Microsoft for C# development has
been the easiest to install.


<a id="org02c86b9"></a>

# Why Emacs?

Emacs allows you to do allmost *all* of your computing in one program.

-   [Multiple cursors and macros](https://www.youtube.com/watch?v=jNa3axo40qM) **impressive!**
-   [Getting Started With Org Mode](https://www.youtube.com/watch?v=SzA2YODtgK4) **recommended**
-   [A Guided Tour of Emacs](https://www.gnu.org/software/emacs/tour/index.html)
-   [Why Emacs? by Bozhidar Batsov](https://batsov.com/articles/2011/11/19/why-emacs/)
-   [The most successful malleable system in history](https://malleable.systems/blog/2020/04/01/the-most-successful-malleable-system-in-history/)


<a id="org255386c"></a>

# For beginners

Learning Emacs is a life long journey. Start by reading the
tutorial. Press C-h t to start the tutorial. This means: press
Ctrl-h followed by t.


<a id="orgf9461be"></a>

## basic configurations

After reading the tutorial experiment with these basic
customizations:

-   [Emacs configuration in 24 minutes](https://www.youtube.com/watch?v=FRu8SRWuUko)
-   [Configuring Emacs from Scratch - Intro](https://medium.com/@suvratapte/configuring-emacs-from-scratch-intro-3157bed9d040)


<a id="org9f61908"></a>

## Emacs documenation


<a id="org1d35582"></a>

### Manual

-   [GNU Emacs manual](https://www.gnu.org/software/emacs/manual/emacs.html)


<a id="orgb768a9a"></a>

### Emacs lisp

Leveraging the power of Emacs requires learning Emacs lisp.

-   quick introduction (**recommended**!) [Learn X in Y minutes where X = elisp](https://learnxinyminutes.com/docs/elisp/)
-   GNU manual about learning elisp [An Introduction to Programming in Emacs Lisp](https://www.gnu.org/software/emacs/manual/eintr.html)
-   [GNU Emacs Lisp Reference Manual](https://www.gnu.org/software/emacs/manual/elisp.html) (not really needed by beginners)


<a id="org5311c6d"></a>

## org-mode

After gaining some experience with Emacs you can start
experimenting with org-mode. This package allows you to organize
your life in plain text files.

-   [user manual](https://orgmode.org/#docs)
-   [org-mode setup by norang.ca](http://doc.norang.ca/org-mode.html)


<a id="orga1b2c0b"></a>

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


<a id="org6c4f78e"></a>

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


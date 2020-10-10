
# Table of Contents

1.  [emacs config](#org421ccdf)
2.  [startup](#orgfb08fe1)
3.  [melpa config](#org3f365b1)
4.  [use-package installation](#org23e25e4)
5.  [packages](#org7ba3bd7)
    1.  [org-mode](#org33c4474)
    2.  [diminish](#orgb72c8bc)
    3.  [which-key](#orgca2e6f8)
    4.  [avy](#orged01939)
    5.  [yasnippet](#org6cc7208)
    6.  [yasnippet-snippets](#org4fe3767)
    7.  [company](#orga825382)
    8.  [flycheck](#orgd2859f1)
    9.  [flx-ido](#org85cb7b2)
    10. [smartparens](#org56fdf59)
    11. [magit](#org2ee7c10)
    12. [project management](#orge0957d5)
        1.  [projectile](#orge6203ab)
        2.  [perspective](#org027250d)
        3.  [persp-projectile](#org9dc83f3)
    13. [language specific packages](#orgbc52f30)
        1.  [old setup](#orgaee1469)
6.  [when emacs closes](#orgf652692)


<a id="org421ccdf"></a>

# emacs config

This is my emacs configuration. Put the following code in init.el:

(require 'org)

(org-babel-load-file (expand-file-name "arthur.org" user-emacs-directory))


<a id="orgfb08fe1"></a>

# startup

    (setq gc-cons-threshold (* 50 1024 1024)
          gc-cons-percentage 0.6
          ;; read-process-output-max
          )
    
    ;; no backups
    (setq auto-save-default nil)
    (setq make-backup-files nil)
    ;; FIXME what does this variable?
    (setq auto-save-list-file-prefix nil)
    
    ;; startup and appearance
    (setq inhibit-startup-message t)
    (setq inhibit-splash-screen t)
    (tool-bar-mode -1)
    ;; browsing the menu makes it easy to discover keybindings
    ;; (menu-bar-mode -1)
    (scroll-bar-mode -1)
    (blink-cursor-mode -1)
    
    (load-theme 'wombat)
    
    ;; (global-hl-line-mode t) ;; easy to find point (point is emacs jargon for cursor)
    ;; (global-linum-mode t)
    
    (fset 'yes-or-no-p 'y-or-n-p)
    
    ;; calendar
    (setq calendar-week-start-day 1)
    (setq calendar-date-style 'iso)
    
    ;; modeline config
    ;; clock
    (setq display-time-24hr-format t)
    ;; no indicator for Mail
    (setq display-time-mail-string "")
    ;; no indicator for load average
    (setq display-time-default-load-average nil)
    (display-time-mode t)
    (line-number-mode t)
    (column-number-mode t)
    
    ;; use auto-fill-mode when editing .txt files
    (add-hook 'text-mode-hook 'auto-fill-mode)
    
    ;; (defun arh/ansi-term () (interactive) (ansi-term "bash"))
    ;; (global-set-key (kbd "C-c t") 'arh/ansi-term)
    ;; FIXME make keybinding for eshell


<a id="org3f365b1"></a>

# melpa config

    (require 'package)
    (add-to-list 'package-archives '("melpa" . "https://melpa.org/packages/") t)
    ;; Comment/uncomment this line to enable MELPA Stable if desired.  See `package-archive-priorities`
    ;; and `package-pinned-packages`. Most users will not need or want to do this.
    ;;(add-to-list 'package-archives '("melpa-stable" . "https://stable.melpa.org/packages/") t)
    (package-initialize)


<a id="org23e25e4"></a>

# use-package installation

    ;; use-package
    ;; https://github.com/jwiegley/use-package#installing-use-package
    ;; read use-package documentation
    (eval-when-compile
      ;; Following line is not needed if use-package.el is in ~/.emacs.d
      ;; (add-to-list 'load-path "<path where use-package is installed>")
      (require 'use-package))


<a id="org7ba3bd7"></a>

# packages


<a id="org33c4474"></a>

## org-mode

    ;; org-mode
    ;; https://orgmode.org/
    (use-package org
      :init (setq org-export-backends '(ascii html icalendar latex md odt))
      :ensure t
      :demand t
      :mode (("\\.org$" . org-mode))
      :bind (("C-c l" . org-store-link)
    	 ("C-c a" . org-agenda)
    	 ("C-c c" . org-capture)
    	 ("C-c b" . org-switchb))
      :config
      (setq org-agenda-files '("~/personal/old-org/index.org" "~/personal/old-org/todo.org"))
      (setq org-agenda-todo-list-sublevels t)
      (setq org-directory "~/personal/old-org/")
      (setq org-startup-folded t)
      (setq org-blank-before-new-entry (quote ((heading . nil)
    					   (plain-list-item . nil))))
      (add-hook 'org-mode-hook (lambda () (auto-fill-mode -1))) ;; disable auto-fill-mode in org-mode
      )
    
    ;; org-capture
    ;; FIXME add todo item
    (setq org-capture-templates
          '(("a" "Maak afspraak")
    	("aa" "Afspraak vanuit agenda (of vandaag)" entry (file+datetree "~/personal/old-org/index.org") "* %T %?")
    	("ad" "Afspraak kies datum" entry (file+datetree+prompt "~/personal/old-org/index.org") "* %T %?")
    	("d" "dagboek" entry (file+datetree "~/personal/old-org/journal.org") "* %U\n%?")
    	))


<a id="orgb72c8bc"></a>

## diminish

    ;; diminish
    ;; https://github.com/myrjola/diminish.el
    (use-package diminish
      :ensure t)


<a id="orgca2e6f8"></a>

## which-key

    ;; which-key
    ;; https://github.com/justbur/emacs-which-key
    (use-package which-key
      :ensure t
      :diminish which-key-mode
      :config (which-key-mode 1))


<a id="orged01939"></a>

## avy

    ;; avy
    ;; https://github.com/abo-abo/avy
    (use-package avy
      :ensure t
      :bind (("C-:" . avy-goto-char))
      )


<a id="org6cc7208"></a>

## yasnippet

    ;;yasnippet
    ;;https://github.com/joaotavora/yasnippet
    ;; This seems to work very well :-)
    ;; TAB is bound to yas-maybe-expand
    (use-package yasnippet
      :ensure t
      :diminish (yas-minor-mode)
      :config (yas-global-mode 1)
      )


<a id="org4fe3767"></a>

## yasnippet-snippets

    ;;yasnippet-snippets
    ;;https://github.com/AndreaCrotti/yasnippet-snippets
    (use-package yasnippet-snippets
      :ensure t
      )


<a id="orga825382"></a>

## company

    ;; company
    ;; https://github.com/company-mode/company-mode
    ;; http://company-mode.github.io/
    ;; FIXME use :hook
    ;; FIXME configure company to refrain from completion in comment blocks
    (use-package company
      ;; :init (add-to-list 'company-backends 'company-capf) ;; is this necessary?
      :ensure t
      :diminish company-mode
      :demand t
      :config
      (setq company-idle-delay 0.0)
      (add-hook 'prog-mode-hook 'company-mode)
      ;; (global-company-mode t)
      )


<a id="orgd2859f1"></a>

## flycheck

    ;; flycheck
    ;; https://github.com/flycheck/flycheck
    ;; FIXME use :hook
    (use-package flycheck
      :ensure t
      :diminish flycheck-mode
      :config
      (add-hook 'prog-mode-hook 'flycheck-mode)
      )


<a id="org85cb7b2"></a>

## flx-ido

    ;; flx-ido
    ;; https://github.com/lewang/flx
    ;; flx-ido is recommended by projectile documentation
    (use-package flx-ido
      :ensure t
      :config
      (require 'flx-ido)
      (ido-mode 1)
      (ido-everywhere 1)
      (flx-ido-mode 1)
      (setq ido-enable-flex-matching t)
      (setq ido-use-faces nil)
      )


<a id="org56fdf59"></a>

## smartparens

    ;; smartparens
    ;; https://github.com/Fuco1/smartparens
    ;; install according to these instructions:
    ;; https://ebzzry.io/en/emacs-pairs/
    ;; First: M-x package-install RET smartparens RET
    ;; above command is not necessary
    (use-package smartparens-config
      :ensure smartparens
      :diminish smartparens-mode
      :config (progn (show-smartparens-global-mode t)))
    
    (add-hook 'prog-mode-hook 'turn-on-smartparens-mode)
    ;; (add-hook 'prog-mode-hook 'turn-on-smartparens-strict-mode)
    ;; (add-hook 'markdown-mode-hook 'turn-on-smartparens-strict-mode)
    ;; smartparens seems to break C-- C-k to kill a line backwards


<a id="org2ee7c10"></a>

## magit

    ;; magit
    ;; https://github.com/magit/magit
    ;; TODO install magit


<a id="orge0957d5"></a>

## project management


<a id="orge6203ab"></a>

### projectile

    ;; projectile
    ;; https://github.com/bbatsov/projectile
    ;; https://docs.projectile.mx/projectile/index.html
    ;; I am not sure about this:
    ;; .projectile should live in the parent directory of directories which should be considered projects
    ;; do not put .projectile in the directory which you consider a project
    ;; This seems to work:
    ;; Put .projectile in a project directory
    ;; Run projectile-discover-projects-in-directory in the parent directory
    (use-package projectile
      :ensure t
      :config
      ;; My keyboard has no super key
      ;; (define-key projectile-mode-map (kbd "s-p") 'projectile-command-map)
      (define-key projectile-mode-map (kbd "C-c p") 'projectile-command-map)
      ;; FIXME determine directories to search for projects
      ;; FIXME ~/projects/ for testing
      (setq projectile-project-search-path '("~/projects/"))
      ;; FIXME alien indexing method?
      (setq projectile-indexing-method 'alien)
      (projectile-mode +1)
      )


<a id="org027250d"></a>

### perspective

    ;; perspective
    ;; https://github.com/nex3/perspective-el
    ;; https://github.com/nex3/perspective-el#some-musings-on-emacs-window-layouts
    (use-package perspective
      :ensure t
      :after projectile
      :config
      (persp-mode) ;; create main perspective
      (setq persp-state-default-file "/home/arthur/.emacs.d/perspective-state")
      )


<a id="org9dc83f3"></a>

### persp-projectile

    ;; persp-projectile
    ;; https://github.com/bbatsov/persp-projectile
    (use-package persp-projectile
      :ensure t
      :after perspective
      :config (persp-state-load persp-state-default-file) ;; is it necessary to load it here?
      )


<a id="orgbc52f30"></a>

## language specific packages


<a id="orgaee1469"></a>

### old setup

    ;; ================================================================================
    ;; old setup
    ;; ;; C#
    ;; ;; csharp-mode
    ;; (use-package csharp-mode
    ;;   :ensure t
    ;;   :mode "\\.cs\\'"
    ;;   )
    
    ;; ;; omnisharp
    ;; ;; https://github.com/OmniSharp/omnisharp-emacs
    ;; ;; on first start: M-x omnisharp-install-server
    ;; ;; FIXME auto start omnisharp server?
    ;; (use-package omnisharp
    ;;   :ensure t
    ;;   :after company
    ;;   :hook (csharp-mode . omnisharp-mode) ;; -hook is added by use-package.el
    ;;   :config (add-to-list 'company-backends 'company-omnisharp))
    
    
    ;; ;; python
    ;; ;; anaconda needs setuptools
    ;; ;; setuptools for python3 has already been installed on my system (Debian 10)
    ;; ;; to use python3 set this variable
    ;; (setq python-shell-interpreter "python3")
    ;; ;; anaconda
    ;; ;; https://github.com/pythonic-emacs/anaconda-mode
    ;; (use-package anaconda-mode
    ;;   :ensure t
    ;;   :hook ((python-mode . anaconda-mode) ;; -hook is added by use-package.el
    ;; 	 (python-mode . anaconda-eldoc-mode))
    ;;   )
    
    ;; (use-package company-anaconda
    ;;   :ensure t
    ;;   :after company
    ;;   :config (add-to-list 'company-backends 'company-anaconda)
    ;;   )
    
    ;; ;; fsharp-mode
    ;; ;; https://github.com/fsharp/emacs-fsharp-mode
    ;; (use-package fsharp-mode
    ;;   :defer t
    ;;   :ensure t
    ;;   :config (require 'eglot-fsharp)
    ;;   )


<a id="orgf652692"></a>

# when emacs closes

    (add-hook 'kill-emacs-hook #'persp-state-save) ;; what does # do?


tinyschemg
===========

Tinyschemg, a working repository for mg(1) and tinyscheme.

branches
--------

- vendor: vanilla sources from CVS
- master: tinyscheme wip

done
----

- initial port to Linux
- got rid of theo in the executable

todo
----

- UTF-8 support
- autotools for better integration with package tools
- rethink tools integrated (cscope & friends)
- allow to eval the current buffer (C-x C-e)
- implement a mode where you can actually interact with scheme,
  instead of eval'ing the minibuffer (like M-x theo)
  - M-x scheme-mode
- expand mgscheme_insert() to also allow for inserting integers.

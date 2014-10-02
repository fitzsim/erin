erin.el
=======

This is an extension to [erin.el]
(http://www.neilvandyke.org/erin-twiki-emacs/erin.el) that allows retrieving
and posting TWiki pages from within Emacs.

This extension uses Emacs's built-in URL package and interprets response HTML
using regexps.  I'm not sure how applicable or robust it is for TWiki
installations in general, but it's very convenient for the intranet TWiki I use
daily at work, which doesn't support any sort of proper RPC mechanism.  And
this mode avoids TWiki's built-in editors completely (which are a pain, even
for copy-from-browser/edit-in-Emacs/paste-into-browser use cases).

Installation
------------

Put erin.el at /path/to/erin/erin.el, then add the following to your
initialization file:

    (add-to-list 'load-path "/path/to/erin")
    (require 'erin)

Customize `erin-url-format` and `erin-username` for your TWiki installation.
By default temporary files will be stored in `~/.emacs.d/erin` for editing.

Caveats
-------

There's no support for conflict detection or resolution, so avoid using this
mode to edit high-traffic topics.  If prior to posting a change you suspect
someone else may have edited the same topic in the meantime, re-run
`erin-edit-topic` to get the freshest copy, then merge your old and new
temporary files, e.g. using `ediff`.

Use
---

Log in:
`M-x erin-log-in`

Edit a topic:
`M-x erin-edit-topic`

[edit the topic in `erin-mode`]

Commit edits:
`C-c C-c`

Cancel edits:
`C-c C-k`

Log out:
`M-x erin-log-out`

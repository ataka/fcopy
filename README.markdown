h1. fcopy.el

h2. Introduction

*Funny copy* is a minor mode to copy text; first, set the paste point*, and next
look for the text to copy.  The past point is the point where fcopy-mode start.
One stroke commands are provided to search and copy the text.  Copy commands
automatically back the cursor to the past point, insert the text, and exit
fcopy-mode.

h2. Install fcopy

Put this in your .emacs file:

{{{
(autoload 'fcopy-mode "fcopy" "copy lines or region without editing." t)
}}}

h2. Usage of fcopy

_M-x fcopy-mode_ takes you into Funny Copy mode.  The place where you get in
fcopy-mode is the paste point; the text you choose to copy will be inserted.

You can exit Funny Copy in 2 ways.  _C-g_ exits Funny Copy and takes your cursor
back to the paste point.  _q_ just exits and does not move.

Some 1-stroke key commands are prepared, like *view-mode*.  _f_, _b_, _n_, _p_,
_a_, _e_ are in common with _C-f_, _C-b_, _C-n_, _C-p_, _C-a_, _C-e_,
respectively.  Moving commands are as follows.
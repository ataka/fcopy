# fcopy.el

## Introduction

<dfn>fcopy</dfn> starts `fcopy-mode`, a minor mode to copy text; first, set the
**paste point**, and next look for the text to copy.  The past point is the
point where fcopy-mode start.  One stroke commands are provided to search and
copy the text.  Copy commands automatically back the cursor to the past point,
insert the text, and exit fcopy-mode.

## Install fcopy

Put this in your .emacs file:

```elisp
(autoload 'fcopy "fcopy" "Copy lines or region without editing." t)
```

## Usage of fcopy

<kbd>M-x fcopy</kbd> brings you into Funny Copy mode.  The place where you
get in fcopy-mode is the paste point; the text you choose to copy will be
inserted.

You can exit Funny Copy in 2 ways.  <kbd>C-g</kbd> exits Funny Copy and takes
your cursor back to the paste point.  <kbd>q</kbd> just exits and does not move.

### Moving Commands

Some 1-stroke key commands are prepared, like **view-mode**.  <kbd>f</kbd>,
<kbd>b</kbd>, <kbd>n</kbd>, <kbd>p</kbd>, <kbd>a</kbd>, <kbd>e</kbd> are in
common with <kbd>C-f</kbd>, <kbd>C-b</kbd>, <kbd>C-n</kbd>, <kbd>C-p</kbd>,
<kbd>C-a</kbd>, <kbd>C-e</kbd>, respectively.

<dl class="def">
   <dt><kbd>C-f</kbd> (<kbd>C-b</kbd>)</dt>
   <dd>forward (backward) char.</dd>

   <dt><kbd>f</kbd> (<kbd>b</kbd>)</dt>
   <dd>forward (backward) word.</dd>

   <dt><kbd>n</kbd> (<kbd>p</kbd>)</dt>
   <dd>next (previous) line with skipping blank lines.</dd>

   <dt><kbd>a</kbd> (<kbd>e</kbd>)</dt>
   <dd>beginning (end) of line.</dd>

   <dt><kbd>A</kbd> (<kbd>E</kbd>)</dt>
   <dd>beginning (end) of sentence.</dd>

   <dt><kbd>N</kbd> (<kbd>P</kbd>)</dt>
   <dd>next (previous) paragraph.</dd>

   <dt><kbd>SPACE</kbd> (<kbd>BackSpace</kbd>)</dt>
   <dd>scroll up (down).</dd>

   <dt><kbd>s</kbd> (<kbd>r</kbd>)</dt>
   <dd>forward (backward) incremental search.</dd>

   <dt><kbd>S</kbd> (<kbd>R</kbd>)</dt>
   <dd>forward (backward) incremental search with regexp.</dd>

   <dt><kbd>&lt;</kbd> (<kbd>&gt;</kbd>)</dt>
   <dd>beginning (end) of buffer.</dd>

   <dt><kbd>g</kbd></dt>
   <dd>Go to line</dd>

   <dt><kbd>o</kbd></dt>
   <dd>Other buffer</dd>

   <dt><kbd>,</kbd> (comma)</dt>
   <dd>Pop mark ring</dd>
</dl>

### Copy Commands

Copy commands take us back to the past point, insert copy text, and exit Funny Copy.

<dl class="def">
   <dt><kbd>.</kbd> (period)</dt>
   <dd>Set mark</dd>

   <dt><kbd>k</kbd></dt>
   <dd>copy the rest of the current line like <kbd>C-k</kbd>.
    If you type <kbd>k</kbd> just after entering fcopy-mode,
    Funny Copy copies text from above line.</dd>

   <dt><kbd>RET</kbd></dt>
   <dd>copy region like <kbd>M-w</kbd>.
    If mark is not active, copy the whole current line.
    With prefix arg, remove the white spaces around the copy text.</dd>

   <dt><kbd>M-RET</kbd></dt>
   <dd>copy rectangle.</dd>

   <dt><kbd>w</kbd></dt>
   <dd>copy word.</dd>

   <dt><kbd>c</kbd></dt>   
   <dd>copy char.</dd>

   <dt><kbd>C</kbd> or <kbd>Shift-Space</kbd></dt>
   <dd>copy block text.
    <dfn>Block text</dfn> means text that separated by spaces.
    For example, <samp>one-to-one</samp> is regarded as 3 words by Emacs.
    However, for Funny Copy, it is regarded as one block.</dd>

   <dt><kbd>(</kbd> (left parenthesis)</dt>
   <dd>copy text between the parens (ex. (...), {...}, [...], &lt;...&gt;).
    You should use this command in the parens, of course.
    If you don't need to copy the parens around text,
    use <kbd>)</kbd> (right parenthesis) instead.</dd>
  
   <dt><kbd>'</kbd> (single quote)</dt>
   <dd>copy text surrounded by the same chars (ex. '...', "...", $...$).
    You should use this command in the chars, of course.
    If you don't need to copy the chars around text,
    use <kbd>&quot;</kbd> (double quote) instead.</dd>

   <dt><kbd>;</kbd> (semi-colon)</dt>
   <dd>copy comments. Comment pattern is depended on major mode.</dd>
</dl>

If you want not to copy text, but to cut, toggle <dfn>delete flag</dfn> with
<kbd>C-d</kbd>.  You can see a delete mark <samp>:d</samp> in mode line.</p>

If you want modify the copy text before paste it, toggle <dfn>modify flag</dfn>
with typing <kbd>m</kbd>.  You can see a modify mark <samp>:m</samp> in mode
line.  When modify flag is on, <dfn>modify buffer</dfn> is opened before
inserting the text.  You can modify the text with replacement and insert the
modified text with <kbd>C-cC-c</kbd>.  See the commentary section in fcopy.el
for details.

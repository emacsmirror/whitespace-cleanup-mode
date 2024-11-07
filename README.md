[![Melpa Status](http://melpa.org/packages/whitespace-cleanup-mode-badge.svg)](http://melpa.org/#/whitespace-cleanup-mode)
[![Melpa Stable Status](http://stable.melpa.org/packages/whitespace-cleanup-mode-badge.svg)](http://stable.melpa.org/#/whitespace-cleanup-mode)
[![Build Status](https://github.com/purcell/whitespace-cleanup-mode/actions/workflows/test.yml/badge.svg)](https://github.com/purcell/whitespace-cleanup-mode/actions/workflows/test.yml)
<a href="https://www.patreon.com/sanityinc"><img alt="Support me" src="https://img.shields.io/badge/Support%20Me-%F0%9F%92%97-ff69b4.svg"></a>

whitespace-cleanup-mode.el
==========================

This Emacs library minor mode will intelligently call `whitespace-cleanup`
before buffers are saved.

`whitespace-cleanup` is a handy function, but putting it in
`before-save-hook` for every buffer is overkill, and causes messy diffs
when editing third-party code that did not initially have clean whitespace.

Additionally, whitespace preferences are often project-specific, and
it's inconvenient to set up `before-save-hook` in a `.dir-locals.el` file.

`whitespace-cleanup-mode` is a minor mode which calls `whitespace-cleanup`
before saving the current buffer, by default only if the whitespace in the buffer
was initially clean. It determines this by quickly checking to see if
`whitespace-cleanup` would have any effect on the buffer. With the custom variable
`whitespace-cleanup-mode-only-if-initially-clean` toggled off, it will always
clean up the buffer for you.


Installation
=============

If you choose not to use one of the convenient
packages in [Melpa][melpa], you'll need to
add the directory containing `whitespace-cleanup-mode.el` to your `load-path`, and
then `(require 'whitespace-cleanup-mode)`.

Usage
=====

Enable `whitespace-cleanup-mode` in an individual buffer like this:

```
M-x whitespace-cleanup-mode
```

Optionally enable it everywhere by default using
`global-whitespace-cleanup-mode`. (You can override that by setting
`whitespace-cleanup-mode` to `nil` in file or directory local
variables.)

Alternatively, enable whitespace cleanup for a particular major mode:

```elisp
(add-hook 'ruby-mode-hook 'whitespace-cleanup-mode)
```

To enable it for an entire project, set `whitespace-cleanup-mode` to `t` in
your `.dir-locals.el` file.

This mode is built upon some functionality built into `whitespace-mode`, namely
`whitespace-action`: if you would rather see a warning when saving a file with
bogus whitespace, or even have the save aborted, then set that variable.

[melpa]: http://melpa.org

<hr>

[💝 Support this project and my other Open Source work via Patreon](https://www.patreon.com/sanityinc)

[💼 LinkedIn profile](https://uk.linkedin.com/in/stevepurcell)

[✍ sanityinc.com](http://www.sanityinc.com/)

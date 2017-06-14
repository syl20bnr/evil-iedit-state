# evil-iedit-state
[![MELPA](http://melpa.org/packages/evil-iedit-state-badge.svg)](http://melpa.org/#/evil-iedit-state)
[![MELPA Stable](http://stable.melpa.org/packages/evil-iedit-state-badge.svg)](http://stable.melpa.org/#/evil-iedit-state)

<!-- markdown-toc start - Don't edit this section. Run M-x markdown-toc-generate-toc again -->
**Table of Contents**

- [evil-iedit-state](#evil-iedit-state)
    - [Description](#description)
    - [Install](#install)
        - [Package manager](#package-manager)
        - [Manually](#manually)
    - [Key bindings](#key-bindings)
        - [State transitions](#state-transitions)
        - [In iedit state](#in-iedit-state)
            - [Navigation](#navigation)
            - [Edit occurrences](#edit-occurrences)
            - [Restrict to scope](#restrict-to-scope)
            - [Expand occurrences above the first or below the last](#expand-occurrences-above-the-first-or-below-the-last)
            - [Change case](#change-case)
            - [Other](#other)
        - [In iedit-insert state](#in-iedit-insert-state)

<!-- markdown-toc end -->

## Description

This package adds two new [Evil][evil-link] states:
- iedit state
- iedit-insert state

It also has a nice integration with [expand-region][]. This allows for quickly
editing some or all occurrences of the selected text, by pressing <kbd>e</kbd>.

## Install

### Package manager

You can either install `evil-iedit-state` from [MELPA][melpa-link]:

```
 M-x package-install evil-iedit-state
```

Or add it to your `Cask` file:

```elisp
(source melpa)

(depends-on "evil-iedit-state")
```

### Manually

Add `evil-iedit-state.el` to your load path. `evil-iedit-state` requires both
`iedit` and `evil` to be installed.

## Key bindings

### State transitions

| Key Binding                    | From          | To     |
|--------------------------------|---------------|--------|
| <kbd>e</kbd>                   | expand-region | iedit  |
| <kbd>ESC</kbd>, <kbd>C-g</kbd> | iedit         | normal |
| <kbd>ESC</kbd>                 | iedit-insert  | iedit  |
| <kbd>C-g</kbd>                 | iedit-insert  | normal |

To sum-up, in `iedit-insert state` you have to press <kbd>ESC</kbd> twice to go
back to the `normal state`. You can also press <kbd>C-g</kbd> at any time to
return to normal state.

**Note:** evil commands that switch to `insert state`, will also switch in
`iedit-insert state`.

### In iedit state

`iedit state` inherits key bindings from `normal state`, but the following key
bindings are specific to the `iedit state`.

#### Navigation

| Key Binding   | Description                                   |
|---------------|-----------------------------------------------|
| <kbd>0</kbd>  | go to the beginning of the current occurrence |
| <kbd>$</kbd>  | go to the end of the current occurrence       |
| <kbd>gg</kbd> | go to first occurrence                        |
| <kbd>G</kbd>  | go to last occurrence                         |
| <kbd>n</kbd>  | go to next occurrence                         |
| <kbd>N</kbd>  | go to previous occurrence                     |

#### Edit occurrences

| Key Binding      | Description                                                                |
|------------------|----------------------------------------------------------------------------|
| <kbd>TAB</kbd>   | toggle current occurrence                                                  |
| <kbd>#</kbd>     | prefix all occurrences with an increasing number                           |
| <kbd>C-u #</kbd> | same as above, but choose the starting prefix number                       |
| <kbd>A</kbd>     | switch to `iedit-insert state` at the end of the current occurrence        |
| <kbd>D</kbd>     | delete all occurrences                                                     |
| <kbd>I</kbd>     | switch to  `iedit-insert state` at the beginning of the current occurrence |
| <kbd>p</kbd>     | replace occurrences with last yanked (copied) text                         |
| <kbd>S</kbd>     | (substitute) delete the occurrences and switch to `iedit-insert state`     |

#### Restrict to scope

| Key Binding  | Description                                              |
|--------------|----------------------------------------------------------|
| <kbd>F</kbd> | restrict the scope to the function that the cursor is in |
| <kbd>L</kbd> | restrict the scope to the current line                   |

#### Expand occurrences above the first or below the last

| Key Binding  | Description                              |
|--------------|------------------------------------------|
| <kbd>J</kbd> | Expand the occurrences by one line below |
| <kbd>K</kbd> | Expand the occurrences by one line above |

#### Change case

| Key Binding    | Description               |
|----------------|---------------------------|
| <kbd>U</kbd>   | Up-case the occurrences   |
| <kbd>C-U</kbd> | down-case the occurrences |

#### Other

| Key Binding                    | Description                                   |
|--------------------------------|-----------------------------------------------|
| <kbd>ESC</kbd>, <kbd>C-g</kbd> | go back to `normal state`                     |
| <kbd>V</kbd>                   | toggle visibility of lines with no occurrence |

**Note:** <kbd>0</kbd>, <kbd>$</kbd>, <kbd>A</kbd> and <kbd>I</kbd> have the
default Vim behavior when used outside of an occurrence.

### In iedit-insert state

| Key Binding    | Description               |
|----------------|---------------------------|
| <kbd>ESC</kbd> | go back to `iedit state`  |
| <kbd>C-g</kbd> | go back to `normal state` |

[melpa-link]: http://melpa.org/
[evil-link]: https://github.com/emacs-evil/evil
[iedit]: https://github.com/tsdh/iedit
[expand-region]: https://github.com/magnars/expand-region.el

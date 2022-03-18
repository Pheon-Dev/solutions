
---

# PROBLEM 1
* 错误：failed to synchronize all databases (无效或已损坏的数据库 (PGP 签名))
## Solution
- Delete:       :`/var/lib/pacman/sync`
- Run           :`sudo pacman -Syyu`

---

# PROBLEM 2
Error detected while loading xmonad configuration file: /home/chaitanya/.xmonad/xmonad.hs

  `
xmonad.hs:13:1: error:
    Could not load module ‘XMonad’
    It is a member of the package ‘xmonad-0.15-1Vwc5FoSZfx6Vsxacie0H7’
    which is unusable due to missing dependencies:
      X11-1.9.2-JuqOkXPYHHHDX5QPzci7Ja data-default-0.7.1.1-DVZWGRf90hqGebpGTaPvOV utf8-string-1.0.2-7pqBkplor7g1hjwTjVt3SV
    Use -v (or `:set -v` in ghci) to see a list of the files searched for.
   |
13 | import XMonad
   | ^^^^^^^^^^^^^

  `

## Solution 
  $ mkdir -p ~/.config/xmonad && cd ~/.config/xmonad

  → ~/.config/xmonad/xmonad.hs
  `
    import XMonad

  main :: IO ()
  main = xmonad def
  `
  $ curl -sSL https://get.haskellstack.org/ | sh
  $ git clone https://github.com/xmonad/xmonad
  $ git clone https://github.com/xmonad/xmonad-contrib

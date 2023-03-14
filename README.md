# Different UNIX Problems and their Solutions
---

## PROBLEM 1

* 错误：failed to synchronize all databases (无效或已损坏的数据库 (PGP 签名))
* error: failed to synchronize all databases (invalid or corrupted database (PGP signature))

### Solution

- Delete:
```
  sudo mv /var/lib/pacman/sync /var/lib/pacman/mksync
```
- Run:
```
  sudo pacman -Syyu
```

---

## PROBLEM 2

Error detected while loading xmonad configuration file: /home/username/.xmonad/xmonad.hs

```
xmonad.hs:13:1: error:
    Could not load module ‘XMonad’
    It is a member of the package ‘xmonad-0.15-1Vwc5FoSZfx6Vsxacie0H7’
    which is unusable due to missing dependencies:
      X11-1.9.2-JuqOkXPYHHHDX5QPzci7Ja data-default-0.7.1.1-DVZWGRf90hqGebpGTaPvOV utf8-string-1.0.2-7pqBkplor7g1hjwTjVt3SV
    Use -v (or ':set -v' in ghci) to see a list of the files searched for.
   |
13 | import XMonad
   | ^^^^^^^^^^^^^

```

### Solution 

- Run:
```
  mkdir -p ~/.config/xmonad && cd ~/.config/xmonad
```

- Edit:
```
  ~/.config/xmonad/xmonad.hs
```

- Add:
```
  import XMonad
  main :: IO ()
  main = xmonad def
```
- Run:
```
  curl -sSL https://get.haskellstack.org/ | sh
  git clone https://github.com/xmonad/xmonad
  git clone https://github.com/xmonad/xmonad-contrib
```

---

## PROBLEM 3

GPGME Error on update

```
$ ~ sudo pacman -Syyu
error: GPGME error: No data
error: GPGME error: No data
error: GPGME error: No data
error: GPGME error: No data
:: Synchronizing package databases...
 core                                        170.6 KiB   552 KiB/s 00:00 [########################################] 100%
 extra                                      1901.8 KiB  7.52 MiB/s 00:00 [########################################] 100%
 community                                     6.6 MiB  9.08 MiB/s 00:01 [########################################] 100%
 multilib                                    177.4 KiB  3.21 MiB/s 00:00 [########################################] 100%
error: GPGME error: No data
error: GPGME error: No data
error: GPGME error: No data
error: GPGME error: No data
error: failed to synchronize all databases (invalid or corrupted database (PGP signature))

```

### Solution 

- Run:
```
  sudo rm -R /var/lib/pacman/sync
  sudo pacman -Syyu
```

---

## PROBLEM 4

error: failed to commit transaction (invalid or corrupted package)

```
$ ~ sudo pacman -Syyu
:: Synchronizing package databases...
........................................................................................................................
........................................................................................................................
 error: failed to commit transaction (invalid or corrupted package)
 Errors occurred, no packages were upgraded.

```

### Solution 

- Run:
```
  find /var/cache/pacman/pkg/ -iname "*.part" -delete
  pacman -Sy archlinux-keyring
  sudo pacman -Syyu
```

- Maybe Run:
```
  pacman-key --refresh-keys
```

---

## PROBLEM 5

Cargo returns error: no default toolchain configured

```
$ ~ cargo <flags> ••••
error: no default toolchain configured
$ ~

```

### Solution 

- Run:
```
  rustup default stable
```

---

## PROBLEM 6

ERR_PNPM_UNEXPECTED_STORE eUnexpected store location

```
$ ~ pnpm add ····
ERR_PNPM_UNEXPECTED_STORE  Unexpected store location
Edit <code>App.tsx</code> and save to test HMR updates. 
The dependencies at "/path/to/somewhere/" are currently linked from the store at "/home/<username/.pnpm-store/v3". <p>
pnpm now wants to use the store at "/home/<username>/.local/share/pnpm/store/v3" to link dependencies.
        className="App-link"
If you wantftohusesthernewtstoreglocation, reinstall your dependencies with "pnpm install".
        target="_blank"
You may changeothenglobalestorerlocation by running "pnpm config set store-dir <dir>".

```

### Solution 

- Run:
```
pnpm store path | xargs rm -rf
```
- Run:
```
pnpm install
```

---
https://www.linuxbabe.com/desktop-linux/fix-cant-read-superblock-error

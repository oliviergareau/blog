---
title: "Fix Yay Libalpm"
date: 2024-03-16T12:14:10-04:00
draft: false
tags: [ "linux" ]
---

# How to fix yay: error while loading shared libraries: libalpm.so.13: cannot open shared object file: No such file or directory

Today after upgrading my Arch Linux system, I was greeted with the following error when trying to run `yay`:

```console
olivier@olivier-arch ~> yay
yay: error while loading shared libraries: libalpm.so.13: cannot open shared object file: No such file or directory
```

This is an error I have already seen in the past. The fix is to sync `base-devel` and reinstall `yay`. Here are the steps:

Remove `yay` using `pacman`:

```console
# pacman -R yay
```

Synchronize the `git` and `base-devel` packages with `pacman`:

```console
# pacman -S git base-devel
```

Navigate to your cached git repository of `yay`. If you do not have this directory, you can always git clone `yay` from the AUR [here](https://aur.archlinux.org/packages/yay).

```console
olivier@olivier-arch ~> cd ~/.cache/yay/yay
```

Update the `yay` git repo to the latest version and run `makepkg` to install it:

```console
olivier@olivier-arch ~> git pull
Already up to date.
olivier@olivier-arch ~> makepkg -si
```

Once `yay` is reinstalled, it should now work!

```console
olivier@olivier-arch ~> yay
:: Synchronizing package databases...
 core is up to date
 extra is up to date
 community is up to date
 multilib is up to date
:: Searching AUR for updates...
:: Searching databases for updates...
 there is nothing to do
```
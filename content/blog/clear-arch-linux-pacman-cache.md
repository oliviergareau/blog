---
title: "Clear Arch Linux Pacman Cache"
date: 2022-05-30T21:48:40-04:00
draft: false
tags: [ "linux" ]
---

# How to clear the pacman cache in Arch Linux

If you are like me and enjoy keeping your Arch Linux system up-to-date, you will inevitably end up in a situation where the package cache of `pacman` takes up a lot of disk space. Here is how to prune this cache and only keep one previous version of cached packages.

You will first want to install the `pacman-contrib` package in order to obtain the `paccache` utility:

```console
# pacman -S pacman-contrib
```

You can now run the `paccache` utility and **delete all the cached packages except for the most recent one**:

```console
# paccache -rk 1
```

Here is the console output of running `paccache` on my machine:

```console
olivier@olivier-arch ~> sudo paccache -rk 1
[sudo] password for olivier: 

==> finished: 1012 packages removed (disk space saved: 2.96 GiB)
olivier@olivier-arch ~>
```
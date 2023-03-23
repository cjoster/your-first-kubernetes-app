# Working with git

Git is a souce code management (SCM) tool that allows teams
to collaborate on source code. Kubernetes admins and developers
treat their kubernets objects as source code, so storing it in,
and managing it with `git` makes sense.

This is not intended to be a full `git` totorial, but instead
simply get you started with the concepts. A far better `git` tutorial
can be found on git's website here: [https://git-scm.com/docs/gittutorial](https://git-scm.com/docs/gittutorial)

To install `git`, run the following commands. 

## Linux DNF based distro (Fedora, Centos 8+, RHEL 8+, etc)

```bash
sudo dnf install git
```

## Linux Yum based distro (pre Fedora 18, CentOS 7 and earlier, RHEL 7 and earlier, etc)

```bash
sudo yum install git
```

## Linux dpkg based (Debian, Ubuntu, etc)

```bash
sudo apt-get update
sudo apt-get install git
```

## MacOS

On a Mac, you have several options. You can use the `xcode` tools version of it,
which is distrubuted and maintained by Apple, or, if you have [Homebrew](https://docs.brew.sh/Installation)
installed, you can use `brew` to install a likely newer version of `git` using
that (homebrew requires the `xcode` tools, so you'll have to do the next step
either way:

### Install the xcode tools

```bash
xcode-select --install
```

### If installing from Homebrew

```bash
brew install git
```

## Windows

There are a variety of tools that can work with `git` repositories
on a Windows machine. If you choose to use these tools, you will
need to figure out how to get started with this tutorial on your
own.

The typical Windows-base git mechanisms are [git bash](https://git-scm.com/download/win)
and Microsoft's on [VS Code](https://code.visualstudio.com/download).

# Next steps

Once you have `git` installed, head on to the next section [Cloning a git repository](../02-Cloning-a-git-Repository)
or you can head back to the [Table of Contents](../) and navigate to the next section.

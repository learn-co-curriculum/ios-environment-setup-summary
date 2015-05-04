---
tags: setup, environment, bash
languages: objc, bash
---

## iOS Environment Setup Summary

If you've gone through setup on the Learn OSX application, your machine has already been setup for iOS development. The setup is based on [Environmentalizer](https://github.com/flatiron-school/environmentalizer), a script we use at Flatiron.

The purpose of this document is to provide you with a summary of how your machine has been setup.

### XCode

XCode, the Apple Development Environment, should have already been installed on your machine by you (it's very difficult to automate that). You can verify this by looking in your `Applications` directory and finding the program file.

![XCode](https://dl.dropboxusercontent.com/s/ibfvkkg7s14i4fw/2015-05-03%20at%208.21%20PM.png)

### GCC

Along with XCode, we installed the XCode Command Line Tools and compiler known as GCC. You can verify this by going into your terminal and typing `gcc`.

```bash
$ gcc
clang: error: no input files
```

_Note: The `$` connotates a command meant to be typed into your prompt. You do not copy the `$` into your terminal. Your prompt is actually `// ♥`_

![GCC](https://dl.dropboxusercontent.com/s/9m0nbrhd5szrjbk/2015-05-03%20at%208.22%20PM.png)

Any output about `no input files` is fine, what you don't want to see is something like this:

```bash
$ gcc
-bash: gcc: command not found
```

You also might get something about accepting terms of service from Apple, if you do, go through that process.

### CocoaPods

CocoaPods is what we use to import third party code into our projects. To make sure it is installed, type `pod` into your terminal. You will hopefully get some help text that looks something like this:

```bash
Usage:

    $ pod COMMAND

      CocoaPods, the Cocoa library package manager.

Commands:

    + init       Generate a Podfile for the current directory.
    + install    Install project dependencies to Podfile.lock versions
    + ipc        Inter-process communication
    + lib        Develop pods
    + list       List pods
    + outdated   Show outdated project dependencies
    + plugins    Show available CocoaPods plugins
    + repo       Manage spec-repositories
    + search     Searches for pods
    + setup      Setup the CocoaPods environment
    + spec       Manage pod specs
    + trunk      Interact with the CocoaPods API (e.g. publishing new specs)
    + try        Try a Pod!
    + update     Update outdated project dependencies and create new Podfile.lock

Options:

    --silent     Show nothing
    --version    Show the version of the tool
    --verbose    Show more debugging information
    --no-ansi    Show output without ANSI codes
    --help       Show help banner of specified command
```

As long as you don't get a bash error, you are fine. Bash errors look like this:

```bash
-bash: pod: command not found
```

### File Directory

The changes here are simple. The Environmentalizer adds a "Development" folder to the root of your home directory. This gives you a place to organize your code.

Here are a few tips for setting up your directories:

* When creating directories, except for directories in `~` (the home directory), always use lowercase directory names for ease of access.
* When creating directory names it is preferable to use a "-" instead of a "_" to denote spaces.
* Keep all code in one place so you can access it easily.
* Make sure you have another directory to keep your resources and other things that are related to code, but aren't code here you might keep your local copy of [The markdown cheetsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links) or other documentation.
* Remember to build your folder structure so you can easily navigate in and out of your project directories. 

### .bash_profile

Your .bash_profile is a script that runs every time you open or login to your shell. It can configure environment variables, like your `PS1` (which stores your command prompt), or `EDITOR` (which is the command other programs will use when they need to launch your default editor).

You can also create aliases for common commands so that they are shorter to use.

And finally, you can also build functions to simplify common workflows.

The Environmentalizer installs the [Flatiron Bash Profile](https://github.com/flatiron-school/dotfiles/blob/master/bash_profile) for you!

Within that bash profile are comments that explain each part. **Make sure to read them!** You can always comment sections in/out to see what they do and how they effect your prompt, shell, and environment.

Just remember, to activate a change in the dotfile, you must **reload your shell**. You can do that via opening a new tab or typing `source .bash_profile` (from the `~` directory).

You know if your `bash_profile` was setup correctly if your prompt has the Flatiron Love.

```bash
[20:23:45] ~
// ♥ 
```

### Homebrew

[Homebrew](http://brew.sh/) is a package manager for OSX. Not only will it help you install packages via commands like `brew install wget` but it will also organize the packages you install and add the appropriate locations to your path. As if that weren't enough, Homebrew also ensures that your system configurations are up to date. Commands like `brew doctor` will help you gauge the health of your system and often provide suggestions for how to fix problems.

You should be able to type in: `brew doctor` and get output from homebrew. Warning and errors are fine, as long as you don't see:

```bash
$ brew doctor
-bash: brew: command not found
```

### Git

[Git](http://en.wikipedia.org/wiki/Git_%28software%29) is the most widely used Version Control system in the world. Read about it, YOU WILL USE IT A LOT! In conjunction with GitHub, it will be used as a Version Control system for all of your projects as well as many other things you will learn. Type in: `git --version`

```bash
$ git --version
git version 2.3.5
```

Any version of git is fine, again, you just don't want to see:

```bash
$ git --version
-bash: git: command not found
```

#### The Learn Submitter

We've installed a ruby gem called `learn-xcpretty` for interacting with `learn.co` from XCode. Generally, you only interact with `learn-xcpretty` through XCode, but to test things out type `learn-xcpretty` in your terminal. As long as you don't get the following bash error `learn-xcpretty: command not found.` you're all set.

#### Sublime Text

[Sublime Text](http://www.sublimetext.com/) is the text editor we use at The Flatiron School. The Environmentalizer installs Sublime Text with a package manager so you can install cool themes and useful add-ons. Make sure you take the time to set it up to your liking, because you will be spending a lot of time with it! You'll see Sublime Text in your `Applications` directory.

![Sublime Text](https://dl.dropboxusercontent.com/s/wenp87iskz1gz9j/2015-05-03%20at%208.36%20PM.png)

#### Sensible Defaults

Like the `.bash_profile` these are scripts and configuration files that work in different areas. You should read through them all to see the specifics of what they are doing. Each has a specific purpose and works for different things. 

* `.gitconfig` will contain the settings that you will take advantage of when employing git in your command line. 
* `.gitignore` is a collection of files that you want git to ignore. Some files that you don't want git to track including, but not limited to, `.DS_Store` and `.env`.

Remember to look through all of these files to see exactly what settings each contains and learn what effect they have on your computer. 

### Symlinks

Symlink stands for "Symbolic Link". A symlink is represented as a text string that the is automatically interpreted by the operating system as as a path to another file or directory. In other words a symlink is like a shortcut to another location. One will allow you to type something like `desktop` in bash to `cd` from any file directory to the desktop. It can also be used as a command, for example you will often find yourself typing `subl .` to open up the current file directory in Sublime Text. This is because the text `desktop` is symbolically linked to the desktop path ("~/Desktop") and `subl` is symbolically linked to the location on your computer where Sublime Text is stored. Some symlinks will be installed by Homebrew and others will be installed by the Environmentalizer. However, to really make your computer your own, look into creating your own!

### SSH Key

SSH stands for "Secure Shell". It is a command interface for communicating with secure servers. SSH keys serve as a means to identify yourself to a SSH server. To set up proper SSH Key Authentication you need a public key (like the one you got from GitHub) and a private key (which will be generated when the Environmentalizer runs). The private key on your computer will allow you to access the Github server with the public key without having to enter a password. You can test this with:

```bash
$ ssh git@github.com
Hi aviflombaum! You've successfully authenticated, but GitHub does not provide shell access.
```

If you get anything else, there was a problem setting up your SSH keys.

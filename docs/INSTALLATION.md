# Installation

## Installation Options

The current Unison release is available for Mac OS X, 64-bit Linux, and Windows users! We hope that if you are trying out Unison you'll come talk to us in the Exercism slack or in the [Unison language slack](http://unison-lang.org/slack). Come ask questions, and report issues you might encounter! We want you to have a welcoming and positive experience when getting started! 😊

### Option 1: Using Homebrew

First [install homebrew](https://brew.sh/) if you haven’t already.

Then from the command line enter these commands:

```
brew tap unisonweb/unison
brew install unison-language
```

This will install the Unison codebase manager executable, `ucm`. If you’re upgrading from a previous version, just do

```
brew upgrade unison-language.
```

Note: if you get prompted for a GitHub username and password at this point, make sure you spelled unisonweb/unison correctly.

### Option 2: Install manually for Mac and Linux users

Linux:

```
mkdir unisonlanguage
curl -L https://github.com/unisonweb/unison/releases/download/release%2FM3/ucm-linux.tar.gz --output unisonlanguage/ucm.tar.gz
tar -xzf unisonlanguage/ucm.tar.gz -C unisonlanguage
./unisonlanguage/ucm
```

Mac:

```
mkdir unisonlanguage
curl -L https://github.com/unisonweb/unison/releases/download/release%2FM3/ucm-macos.tar.gz --output unisonlanguage/ucm.tar.gz
tar -xzf unisonlanguage/ucm.tar.gz -C unisonlanguage
./unisonlanguage/ucm
```

### Option 3: Install manually for Windows users

1. Set your default terminal application to “Windows Terminal” for best results. Search for “Terminal” in Settings, or follow [this how-to.](https://bit.ly/3IXwdlY)
2. If you’re not sure you already have it, install Git:
  * Via winget: `winget install --id Git.Git -e --source winget`
  * If you are on Windows 10 and don’t have winget, you can install it from [the Microsoft Store](https://www.microsoft.com/en-us/p/app-installer/9nblggh4nns1), and then run the command above.
3. [Download the UCM with this link](https://github.com/unisonweb/unison/releases/download/release%2FM3/ucm-windows.zip) and extract it to a location of your choosing.
4. Run `ucm.exe`

### Option 4: Nix installation
Head to [https://github.com/ceedubs/unison-nix/#usage](https://github.com/ceedubs/unison-nix/#usage) and follow the instructions in the readme there.

## Create your Unison codebase

Run `ucm` to initialize a Unison codebase in `$HOME/.unison`. This is where Unison will store function definitions, types, namespaces, and so on. By default, the Unison Codebase Manger (abbreviated the "UCM")  will begin downloading the standard library, called `base`, which you'll use to write Unison code. It may take a moment! 🕰

## Unison workflow

When you want to write Unison code, you'll issue the `ucm` command to start the codebase manager. The UCM will then observe changes to any `.u` suffixed file in the directory where it is called from. For example, you might be implementing functions in a file called `scratch.u` in a directory called `~/exercism/unison/my-exercise/`. You should `cd` into `~/exercism/unison/my-exercise/` and run `ucm`. This will ensure that the UCM is watching your `scratch.u` file for changes.

If you're ever confused about what directory the `ucm` is watching for file changes under, it's printed in the welcome screen upon starting the cli.

```
👀 I'm watching for changes to .u files under /Users/myUser/Exercism/unison/myExercise
```

## Editor support

You can use any text editor to write your `.u` files. A few popular editors with Unison support are listed below:

### Vim

Using [vim-plug](https://github.com/junegunn/vim-plug):

1. Install [`vim-plug`](https://github.com/junegunn/vim-plug) if you haven't already.
2. Add the following to your .vimrc: `Plug 'unisonweb/unison', { 'branch': 'trunk', 'rtp': 'editor-support/vim' }`
3. Issue the vim command `:PlugInstall`.

For more information run `:help unison`
from within vim or view the [online help doc](https://github.com/unisonweb/unison/blob/trunk/editor-support/vim/doc/unison.txt).

### Atom
From the console, run:

```
apm install unisonweb/atom-unison
```

### VS Code

1. Bring up the Extensions view by clicking on the Extensions icon in the Activity Bar on the side of VS Code, or with ⇧⌘X.
2. Search for "unison"
3. Select "Unison Syntax Highlighting" and click "Install."

### Emacs
Install [`unison-mode`](https://github.com/dariooddenino/unison-mode-emacs).

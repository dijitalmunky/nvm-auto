# nvm-auto

nvm-auto is an plugin for the venerable [oh-my-zsh](http://ohmyz.sh/).

It aims to alleviate needing to type `nvm use` as much as possible, especially
if you often switch between versions of node.js and use `.nvmrc` files in your
project to manage what version of node your project needs.

## The Problem

Let's say for example that you have the following
directory structure with 2 projects in it:

```txt
~
+-- Project1
|   +--- .nvmrc
|
+-- Project2   
    +--- .nvmrc
```

Let's say Project1's `.nvmrc` file states we need node **v4.2.4**.  Project2's,
on the other hand, states a need for **v5.8.0**.

To move between projects you will need to do something like:

```zsh
cd Project1
nvm use

// do some stuff in project one

cd Project2
nvm use

//do some other stuff

```

If you are like me, you often forget to execute the `nvm use` commands after
each `cd`.  This can lead to problems ranging from the simple scripts not
running to more problematic ones like global npm installs against the wrong
node version, or bad module builds for the local repo.

## How nvm-auto helps

If you use `oh-my-zsh`, then this plugin helps by auto-executing the `nvm use`
command when you switch contexts (for example from Project1 to Project2).

No more bad installs, no more cluttering up the global node area with unneeded
modules.

## Installation

For the impatient:

```zsh
cd ~/.oh-my-zsh/custom/plugins
git clone https://github.com/dijitalmunky/nvm-auto.git
sed -e 's/^plugins=(\(.*\))/plugins=(\1 nvm-auto)/' -i.pre-nvm-auto ~/.zshrc
echo 'nvm_auto_switch' >> ~/.zshrc
source ~/.zshrc
```

For the less impatient:

1.  Ensure you have nvm >=0.30 installed properly.

2.  Make sure you have set the `default` alias for nvm - e.g.:
    `nvm alias default 10.14.1`

3.  Have `oh-my-zsh` installed (D'uh!)

4.  Open a terminal and navigate to your `~/.oh-my-zsh/custom/plugins` folder.

5.  Clone this repository to that folder.

6.  Add `nvm-auto` to your plugins variable in `~/.zshrc`.

7.  Add a call to the `nvm_auto_switch` function **after** NVM is initialized in
    your `.zshrc` file.

8.  Source `.zshrc` in your current shell or restart your shell.

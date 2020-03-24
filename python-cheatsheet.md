# Python Cheatsheet

## Linux Commands
---

Most used commands:

- `$ pwd` - print working directory
- `$ cd` - change to a different directory
- `$ cd /` - change to the root directory
- `$ cd ` - without any parameters, it will go to the HOME directory
- `$ cd ..` - change to the previous directory
- `$ mkdir` - make a new directory
- `$ touch` - create a empty file


## Python, pip3, Git Installation
---

On Ubuntu based linux distros. You might want to run the following command to update your package.


- `$ sudo apt update` - only updates the list of available packages and their versions, but it does not install or upgrade any packages installed on your local machine.
- `$ sudo apt upgrade` - upgrade actually installs newer version of the packages you have.

Python installation

- `$ python3 --version` - check python3 version

- `$ sudo apt install python3` - install python3.

pip3 installation:

- `$ pip3 --version` - check pip3 version.
- `$ sudo apt install python3-pip` - install pip3

Git installation:

- `$ git --version` - check Git version.
- `$ sudo apt install git-all` or `sudo apt-get install git` - install Git

## Setting up virtual environment
---

Create a directory where the project will live and then move into the directory you just created.

```
$ mkdir foo
$ cd foo
```

Using the following command to create the virtual environment.

`$ python3 -m venv venv`  

Activating the virtual environment.

```
$ source venv/bin/active
(venv) $ _

```

Click [here](https://docs.python.org/3/using/cmdline.html#cmdoption-m) to find more info on `python3 -m <moduel-name>`

> With this command, I'm asking Python to run the venv package, which creates a virtual environment named venv. The first venv in the command is the name of the Python virtual environment package, and the second is the virtual environment name that I'm going to use for this particular environment. If you find this confusing, you can replace the second venv with a different name that you want to assign to your virtual environment. In general I create my virtual environments with the name venv in the project directory, so whenever I cd into a project I find its corresponding virtual environment.

## Git Commands
---

Configaration
```
$ git config --global user.name "First Last"
$ git config --global user.email "foo@outlook.com"
```

Create a new repository
- `$ git init`

Checkout a repository
- `$ git clone /path/to/repository` - createa working copy of a local repository by running the command.
- `$ git clone username@host:/path/to/repository` - when using a remote server, your command looks like this.

Add & commit
- `$ git add <filename>` or `$ git add .` - propsoe changes (add it to the Index)
- `$ git commit -m "Commit message"` - to actually commit these changes.


Pushing changes:
-  `$ git push origin master` - Your changes are now in the **HEAD** of your local working copy. To send those changes to the remote repository.

- `$ git remote add origin <server>` - If you have not cloned an existing repository and want to connect your repository to a remote server, you need to add it with this command.

- `$ git clone <URL parameter>`
>In Git, "origin" is a shorthand name for the remote repository that a project was originally cloned from. More precisely, it is used instead of that original repository's URL - and thereby makes referencing much easier.<br><br>
>Note that origin is by no means a "magical" name, but just a standard convention. Although it makes sense to leave this convention untouched, you could perfectly rename it without losing any functionality.<br><br>
>In the following example, the URL parameter to the "clone" command becomes the "origin" for the cloned local repository:



update & merge

- `$ git pull` - to update your local repository to the newest commit.


[CLICK HERE](https://rogerdudler.github.io/git-guide/) for more Git guide.


Returning to an Old Revision. [More info](https://www.git-tower.com/learn/git/faq/restore-repo-to-previous-revision)

- `$ git reset --hard 0ad5a7a6`
> This will rewind your HEAD branch to the specified version. All commits that came after this version are effectively undone; your project is exactly as it was at that point in time.

- `$ git reset --soft 0a5a7a6`
>The reset command comes with a couple of options, one of the more interesting ones being the "--soft" flag. If you use it instead of --hard, Git will keep all the changes in those "undone" commits as local modifications:You'll be left with a couple of changes in your working copy and can then decide what to do with them.

## Vim Text Editor Commands
---

Vim has two mode, one is **COMMAND MODE**, another is **INSERT MODE**

**COMMAND MODE**
- `:q` - leave the program
- `:w` - write the current state to the file.
- `:wq` - save and exit.
- `:q!`  - quitck without saving anychanges.
- `:set number`
- Press **i** enters INSERT MODE.
- `dd` - Delete a line.
- `<number> dd` - put a number before a command, like `dd`, it will try to do that command, that number of times.
- `u` - UNDO your last action.
- Hit **Ctrl + R** will redo your actions.
- `/<search-string>` - automatecally highlited the first match, when you hit ENTER, it will take your cursor to the first caracter of the first match. You can go to the next with the lower case **n**. Upper case **N** will search backward.
-`:%s/<string-need-replaced>/<string-to-replaced-with/gc` - g stand for greedy, without **g**, it will only replace the first occurence. **c** ask for confirmation.  

**INSERT MODE**
- Press **ESC** back to COMMAND MODE.

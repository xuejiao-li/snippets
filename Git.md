# Git

## Tutorials & Resources

[Youtube: Travesymedia](https://www.youtube.com/watch?v=SWYqp7iY_Tc)

[Git official website](https://git-scm.com)

## Install

- Use Mac or Windows installer downloaded from the Git official website
- Use this command `brew install git` on the Mac. 

Use the snippets below in the terminal to check the git version and add your inforamtion to the git. 
```
$ git --version
$ git config --global user.name "Xuejiao Li"
$ git config --global user.email "example@outlook.com"

```
## Basic Command

```
$ git init 
$ git add index.html
$ git add .
$ git status

$ git commit -m "first commit"
$ git commit 

$ git remote add origin https://github.com/xuejiao-li/test.git
$ git push -u origin master

$ git clone https://github.com/xuejiao-li/Hands-On-Data-Analysis-with-Pandas.git . 
(clone or copy a repository to your current working directory, this only works when the directory is empty)

```

NOTE: `git commit` without `-m` when using this command, it will bring you to the text editor in terminal. Type I activate the INSERT MODE. after addming the comment in the first line. Type ESC to exit the INSERT MODE. type :wq to save the change and get out of the editor. 

When you need to work on a different computer for the existed repository on the Github. 

1. Create a folder where you can init the Git `git init` , the name of the folder dosn't have to match the name of your repository
2. Add the remote repository `git remote add origin http://github.com/xuejiao-li/test.git` the origin is a standard convention used for the URL of your repository. 
3. Pull the repository to your local machine by using `git pull origin master` to pull the remote repository to your local master branch. 

**NOTE: After the first time when you push and pull, you are able to simply use `git push` and `git pull` without `origin master`**


## *Make sure you complete the [pre-work](https://github.com/radhigulati/prework_instructions/blob/master/instructions.md) before continuing with the Git tutorial*

## Introduction 
In this tutorial you will learn how to:
* Use the command line
* Create and manipulate directories and files
* Commit and push changes to GitHub from the command line
* Create and accept pull requests

Knowing how to use a version control system and the command line are  considered basic requirements for software developers. After this tutorial, you will have some comfortability with the command line, using Terminal commands, Git, and GitHub.

During the tutorial you will be typing commands into the Terminal. The commands will appear like ```command``` or like 

    $ command
When I tell you to type a command into your terminal, type the command the way it is written. If you see a command with the ```$``` symbol, do not type the ```$``` symbol. The ```$``` symbol just shows you where you begin typing in the terminal. 

Glossary of Terminal commands:
* ```pwd```: present working directory
* ```ls```: list
* ```ls -la```: list all contents of directory including ignored files in long format
* ```cd```: change directory
* ```mkdir```: make directory
* ```touch```: creates a new file


## Create project
Let's begin!

<span style="color:red"> **TASK:** </span> First, let's create a new directory in the Terminal where we will store all projects. Make sure you are in your home directory before creating the projects folder. To check which directory you are in use the ```pwd``` command in your terminal and you should see something like ```/Users/radhika```. If you type in ```pwd``` into your terminal you should see the current directory you are in.

<span style="color:red"> **TASK:** </span>Once you are in the correct directory use the command ```mkdir projects``` to create a new projects folder. Type in the command ```ls -la``` to list out the contents of this folder. 

<span style="color:red"> **TASK:** </span> Let's access the new projects folder. To do this type in the command ```cd projects```. If you type in ```pwd``` you should see something like ```/Users/radhika/projects```.

<span style="color:red"> **TASK:** </span> Now lets create a directory for our project using the ```mkdir``` command and the directory name. One person should name their project ```git-demo``` and one person should name their project ```git-demo-rko```. I will use ```git-demo``` in my examples in this tutorial. 
```
$ mkdir git-demo
```
<span style="color:red"> **TASK:** </span> Now let's access the directory using the ```cd``` command
```
$ cd git-demo
```
<span style="color:red"> **TASK:** </span> If you type in ```pwd``` you should see that you are in the ```git-demo``` folder.

<span style="color:red"> **TASK:** </span> We need it initialize this repository by using the command ```git init```. Make sure you are in your project folder, and type ```git init``` into your terminal. 
> **Learning Note** Executing git init creates a .git subdirectory in the current working directory, which contains all of the necessary Git metadata for the new repository.

> **Learning Note** You won't see anything in GitHub right now because we haven't pushed anything to GitHub. We've just been working on the local machine, so everything is stored locally right now.

## Create your first file
Let's create a a file in the project folder called ```demo.txt```.

<span style="color:red"> **TASK:** </span> To create this file, type ```touch demo.txt``` into your terminal.

Let's open the code editor you downloaded earlier for this project. <span style="color:red"> **TASK:** </span> To open VScode from the project folder in the terminal, you can type ```code .``` within your terminal within the project. Once your code editor is open, you should have access to your file. <span style="color:red"> **TASK:** </span> Within your file write ```This is a demo git repo.``` Save the changes once written (```cmd + s``` or ```file``` > ```save```)

Let's add this file to our staging area. 

> **Learning Note** The staging area is where we keep track of all the files we need to commit. If a file is not added to the staging area, it will not be commited. 

> **Learning Note** The ```git add``` command adds a change in the working directory to the staging area. It tells Git that you want to include updates to a particular file in the next commit. However, ```git add``` doesn't really affect the repository in any significant way—changes are not actually recorded until you run git commit.

<span style="color:red"> **TASK:** </span>To add a file to the staging area  type in the command ```git add demo.txt```. If you want to add all the files to the staging area you can use ```git add .``` For our case right now, you can use either.

## Commit changes
<span style="color:red"> **TASK:** </span> Now let's commit the changes. Type ```git commit -m "First commit. Added demo.txt file"```

Then type ```git status``` to check the status of git.

## Add project to GitHub

<span style="color:red"> **TASK:** </span>Let's navigate to GitHub and create a new project. Within GitHub, navigate to the ```new``` button to create a new project. For the ```repository name``` use ```git-demo```. You can add a description that says ```This project is a beginner git project.``` Make the project ```public```. DO NOT initialize this project with a ```README file```. Then click ```create repository```.

You have now created an empty repository with a README file within GitHub. You will be directed to a page with some instructions that I will describe below. Keep in mind we've already run ```git init```.

<span style="color:red"> **TASK:** </span> You have already added and commited changes to Git, so type ```git status``` to check the status of git. If you have changes that have not been added run the add and commit commands again:

    git add .
    git commit -m "add some description"

If you see:

    Your branch is up to date with 'origin/main'.

    nothing to commit, working tree clean
This means you have not made any new changes.

<span style="color:red"> **TASK:** </span> Now, we need to point our local repository to the remote repository. To do that type the following command in your terminal (make sure you are in your project directory)
```git remote add origin [repository url]```

The ```repository url``` will be ```git@github.com:[your github username]/[name of repo].git```. For example, my url would be ```git@github.com:radhigulati/git-demo.git```. You can find this url in the instructions on your GitHub page for the new project you created. 

<span style="color:red"> **TASK:** </span>You can change the ```master``` branch to ```main``` by using the command ```git branch -M main```. If you are interested in why GitHub renamed it's ```master``` branch to ```main``` checkout [this](https://www.theserverside.com/feature/Why-GitHub-renamed-its-master-branch-to-main#:~:text=GitHub%20took%20action%20based%20on,a%20different%20default%20for%20new) article.

**If you recieve an error that says ```error: refname refs/heads/master not found
fatal: Branch rename failed``` then follow the steps below otherwise skip these steps:**

1. Within the project directory, type the command ```cd .git```
2. Then open this folder in your code editor (with vscode you can type in ```.code```)
3. Navigate to the ```HEAD``` file 
4. Change ```ref: refs/heads/master``` to ```ref: refs/heads/main```
5. Save this file

Now your ```master``` branch will be ```main```.

<span style="color:red"> **TASK:** </span> Let's push your project to GitHub. To do this, type the command ```git push -u origin main```.

If you navigate to GitHub, you should see your file in GitHub!

## Creating a branch
Now let's create a new branch, add some commits, and merge that branch to your main branch.

> **Learning note** A branch represents an independent line of development. Branches serve as an abstraction for the edit/stage/commit process. You can think of them as a way to request a brand new working directory, staging area, and project history. New commits are recorded in the history for the current branch, which results in a fork in the history of the project. The changes in the branches you create will not effect the main/master branch until you are ready to merge with the main/master branch.

<span style="color:red"> **TASK:** </span> Let's view all the branches available. Make sure you are in the project directory in your terminal. Use the command ```git branch``` to view all the branches. 

You should only see your ```main``` branch. Remember, we changed      ```master``` to ```main```.

<span style="color:red"> **TASK:** </span>Now, let's create a branch called ```dev```. To do this type ```git checkout -b dev```. 

<span style="color:red"> **TASK:** </span> When you type ```git branch``` you should see the ```main``` branch and the ```dev``` branch. You should also be in the ```dev``` branch. 

<span style="color:red"> **TASK:** </span> Let's access the ```demo.txt``` file within the code editor and add some changes. Type something in the file like "I love Revenue Enablemnet" or "Hello {partner}, hope you are having a nice day". Keep it appropriate for work. :) 

The change you made will not be available in the ```main``` branch yet. If you want to check and see what the ```txt``` file in the ```main``` branch looks like, you can go back to the ```main``` branch by typing the command ```git checkout main``` and viewing the ```demo.txt``` file.

<span style="color:red"> **TASK:** </span> Now we want to stage and commit the change we made to the ```demo.txt``` file in the ```dev``` branch. To do this type the ```git add .``` command then ```git commit -m "Adding the dev branch"```

<span style="color:red"> **TASK:** </span> You can verify your commit history in the new branch by typing ```git log```. Here you should see the new commit.

Right now, the ```main ``` branch is behind on one commit, so let's merge the ```dev``` branch with the ```main``` branch. 

*Continued in the next section* 
## Merging branches
<span style="color:red"> **TASK:** </span> To merge the code from the ```dev``` branch into the ```main``` branch, checkout the ```main``` branch first. So use the command ```git checkout main``` to access the ```main``` branch. 

<span style="color:red"> **TASK:** </span> Now we can use the ```merge``` command to merge branches, so type ```git merge dev```.

The merge should work, and you shouldn't see conflicts. In a real project, conflicts can happen and developers have to clear those conflicts before a merge is possible.

<span style="color:red"> **TASK:** </span> We can push these changes to GitHub now. Follow these commands

1. ```git add .```
2. ```git commit -m "merged dev with main"```
3. ```git push```

<span style="color:red"> **TASK:** </span> Your branches should now be merged! You can go to GitHub and checkout the ```demo.txt``` and make sure all of the contents are available.

## Creating a Pull Request
Let's learn about pull requests.

You are going to make a pull request on your partners ```git-demo``` project. 

<span style="color:red"> **TASK:** </span> Go to their project and click the ```fork``` button at the top right. Make sure you fork the project to your own organization. To clarify, you may see two organizations: yours and CircleCI. Make sure you click on your organization.

> **Learning note** Forking will save the project to your GitHub account (you should see the project once it's forked).

*Do the task below in the projects directory. Your path should look like /Users/radhika/projects*

<span style="color:red"> **TASK:** </span> Now, clone the repo locally (in your terminal). This link is available in GitHub when you click on the code button in the repo and choose ssh (you just need to use ```git clone``` before the url). For example 

    $ git clone git@github.com:radhigulati/git-demo.git

<span style="color:red"> **TASK:** </span> Create a new branch with ```git checkout -b <your-name demo>``` For example, ```git checkout -b radhika-demo```

<span style="color:red"> **TASK:** </span> Create a new remote for the upstream repo with the command:

```git remote add upstream <link to github url>``` 

The GitHub url is your partners GitHub project url.

For example: ```git remote add upstream https://github.com/radhigulati/git-demo-rko```

> **Learning note** "Upstream repo" refers to the original repo/parent repo you created your fork from.

<span style="color:red"> **TASK:** </span> Type ```ls -la``` into the terminal and you should see the ```demo.txt``` file. Make sure you see text from you partner. Within the file, you can type in something to them! (like "we love revenue enablement" or "Hello, {partner_name}!). Again, keep it safe for work. :) 

<span style="color:red"> **TASK:** </span> Double check you are in your branch with the command```git branch```. When you type this command, you should see your branch highlighted.

<span style="color:red"> **TASK:** </span> Follow the steps below to push your new changes. For instruction 3, ```[branch]``` will be the branch name that you used without the brackets. For example ```git push -u origin radhika-demo```:

1. ```git add demo.txt```
2. ```git commit -m "added my comment for a PR"```
3. ```git push -u origin [branch]``` ex: ```git push -u origin radhika-demo```

<span style="color:red"> **TASK:** </span> Go to the GitHub project page, and click on ```pull requests```.

<span style="color:red"> **TASK:** </span> You should see a green button that says ```New Pull Request``` that you should click on.

<span style="color:red"> **TASK:** </span> Add a description of what the PR contains, and click on ```create pull request```


## Accepting a Pull Request
<span style="color:red"> **TASK:** </span> Each person should go to ```pull requests```, click on the ```pull requests```, and as long as there are no conflicts you can ```merge the pull request```.

## Congrats
You have finished the Git tutorial!

In this tutorial, you learned how to:
* Use the command line
* Create and manipulate directories and files
* Commit and push changes to GitHub from the command line
* Create and accept pull requests

Next, we will work on a coding project where you will use the skills you learned today.





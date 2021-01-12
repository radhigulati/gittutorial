## Installing your text editor
> Install VScode, Sublime, or another text editor on your computer (I prefer VScode). If you downloaded vscode and have a mac, open up the Command Palette with **cmd+shift+p** or go to ```view > command palette``` in vscode and type in ```Shell Command: Install 'code' command in PATH```. This will allow you to open up vscode from the terminal in mac.

## Installing Git
First, we need to make sure you have git installed on your computer.

Open up your terminal (you can do a spotlight search on your mac for “terminal”)

>The Terminal, also known as the command line or a Terminal emulator, is an essential component of any useful operating system. The Terminal provides an efficient interface to access the true power of a computer better than any graphical interface.

>You can’t use a mouse or trackpad in Terminal, but you can navigate using the arrow keys. If you want to re-run a command, tap the up arrow key until you reach it, then press Return. To interrupt a command that’s already running, type Control-C.

First, check to see if you have git installed by typing in the command 

    $ git --version

If you do you'll see something like

    $ git version 2.20.1 (Apple Git-117)

If not, you might see something like

To install git, first install homebrew with 

    $ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

> Homebrew is a free and open-source software package management system that simplifies the installation of software on Apple's macOS operating system and Linux.

Once you've installed homebrew, you can install git with
    
    $ brew install git

Now let's set your Git username in your Terminal


## Adding your SSH Keys
Let's add your SSH keys to your GitHub account


1. Open Terminal.

2. Paste the text below, substituting in your GitHub email address.
```
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    
    To delete ssh keys
$ cd ~/.ssh
$ rm ~/.ssh/github_rsa.pub
```
3. When you're prompted to **"Enter a file in which to save the key,"** press Enter. This accepts the default file location.

4. At the prompt, type a secure passphrase.

5. Copy the SSH key to your clipboard. To do that type this command
```
$ pbcopy < ~/.ssh/id_rsa.pub
```

6. In the upper-right corner of any page in GitHub, click your profile photo, then click Settings.

7. In the user settings sidebar, click SSH and GPG keys.

8. Click New SSH key or Add SSH key.

9. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal Mac, you might call this key "Personal MacBook Air".

10. Paste your key into the "Key" field.

11. Click Add SSH key

> An SSH key is an alternate way to identify yourself that doesn't require you to enter you username and password every time.

Next, lets set up your Git usernmae for every reposiotry on your computer

1. Open terminal if it's not already open
2. Set a Git username:
````
$ git config --global user.name "Mona Lisa"
````
## Add email address to GitHub for commits
Next lets set your commit email address on GitHub. To do so, follow the instructions [here](https://docs.github.com/en/free-pro-team@latest/github/setting-up-and-managing-your-github-user-account/setting-your-commit-email-address#setting-your-commit-email-address-on-github).

Next, lets set up your commit email address in Git. 

1. Open terminal if it's not already open
2. Set an email address in Git. You can use your GitHub-provided no-reply email address or any email address.
````
$ git config --global user.email "email@example.com"
````
3. Confirm that you have set the email address correctly in Git:
```
$ git config user.email
email@example.com
```
## Create project
Now, let's get are first project going!

First, let's create a new directory where we will store all projects. Make sure you are in your home directory before creating the projects folder. To check which directory you are in use the ```pwd``` command in your terminal and you should see something like ```/Users/radhika```.

Once you are in the correct directory use the command ```mkdir projects``` to create a new projects folder. When you type in the command ```ls``` you should now see the projects folder within the list of folders and files. 

Let's access the new projects folder. To do this type in the command ```cd projects```. If you type in ```pwd``` you should see something like ```/Users/radhika/projects```.

Now lets create a folder for our project using the ```mkdir``` command
```
$ mkdir git-demo
```
Now let's access the directory using the ```cd``` command
```
$ cd git-demo
```
If you type in ```pwd``` you should see that you are in the ```git-demo``` folder.

We need it initialize this repository by using the command ```git init```. Make sure you are in your project folder, and type ```git init``` into your terminal. 
>Executing git init creates a .git subdirectory in the current working directory, which contains all of the necessary Git metadata for the new repository.

>You won't see anything in GitHub right now because we haven't pushed anything to GitHub. We've just been working on the local machine, so everything is stored locally right now.

## Create your first file
Let's create a a file in the project folder called ```demo.txt```.

To create this file, type ```touch demo.txt``` into your terminal.

Let's open the code editor you downloaded earlier for this project. If you are using vscode, you should be able to type in ```code .``` within your terminal within the project. Once your code editor is open, you should have access to your file. Within your file write ```This is a demo git repo.``` Save the changes once written.

Let's add this file to our staging area. The staging area is where we keep track of all the files we need to commit. If a file is not added to the staging area, it will not be commited. To add a file to the staging area  type in the command ```git add demo.txt```. If you want to add all the files to the staging area you can use ```git add .``` For our case right now, you can use either.

## Commit changes
Now let's commit the changes. Type ```git commit -m "First commit. Added demo.txt file"```

You can also change the ```master``` branch to ```main``` by using the command ```git branch -M main``` if you recieve an error that says ```error: refname refs/heads/master not found
fatal: Branch rename failed``` then follow these steps:

## Change "master" to "main"
1. Within the project directory, type the command ```cd .git```
2. Then open this folder in your code editor (with vscode you can type in ```.code```)
3. Navigate to the ```HEAD``` file 
4. Change ```ref: refs/heads/master``` to ```ref: refs/heads/main```
5. Save this file

Now your ```master``` branch will be ```main```.

Let's navigate to GitHub and create a new project. 

Within GitHub, naviage to the ```new``` button to create a new project.

For the ```repository name``` use ```git-demo```.

You can add a description that says ```This project is a beginner git project.```

Make the project ```public```.

Initialize this project with a ```README file```. Then click ```create repository```.

You have no created an empty repository with a README file within GitHub.

Now, we need to point our local repository to the remote repository. To do that tye the following command in your terminal (make sure you are in your project directory)
```git remote add origin [repository url]```

The ```repository url``` will be ```git@github.com:[your github username]/[name of repo].git```

For example, my url would be ```git@github.com:radhigulati/git-demo.git```

Let's push your project to GitHub.

To do this, type the command ```git push -u origin main``` or ```git push -u origin master```
if you branch name is still master.

If you navigate to GitHub, you should see your file in GitHub!

## Creating a branch
Now let's create a new branch, add some commits, and merge that branch to your main/master branch.

> A branch represents an independent line of development. Branches serve as an abstraction for the edit/stage/commit process. You can think of them as a way to request a brand new working directory, staging area, and project history. New commits are recorded in the history for the current branch, which results in a fork in the history of the project. The changes in the branches you create will not effect the main/master branch until you are ready to merge with the main/master branch.

Let's view all the branches available. Make sure you are in the project directory in your terminal. Use the command ```git branch``` to view all the branches. 

You should only see your ```main/master``` branch.

Now, let's create a branch called ```dev```. To do this type ```git checkout dev```. 

When you type ```git branch``` you should see the ```main/master``` branch and the ```dev``` branch. You should also be in the ```dev``` branch. 

Let's access the ```demo.txt``` file within the code editor and add some change. You can write whatever you want here then save the change. 

The change you made will not be available in the ```main/master``` branch yet. If you want to check and see you can go back to the ```main/master``` branch by writing the command ```git checkout main``` or ```git checkout master``` and viewing the ```demo.txt``` file.

Now we want to stage and commit the change we made to the ```demo.txt``` file in the ```dev``` branch. To do this type the ```git add .``` command then ```git commit -m "Adding the dev branch"```

You can verify your commit history in the new branch by typing ```git log```. Here you should see the new commit.

Right now, the ```main/master ``` branch is behind on one commit, so let's merge the ```dev``` branch with the ```main/master``` branch. 
## Merging branches
To merge the code from the ```dev``` branch into the ```main/master``` branch, checkout the ```main/master``` branch first. So use the command ```git checkout main``` or ```git checkout master``` to access the ```main/master``` branch. 

Now we can use the ```merge``` command to merge branches, so type ```git merge dev```.

The merge should work, and you shouldn't see conflicts. In a real project, conflicts can happen and developers have to clear those conflicts before a merge is possible.

We can push these changes to GitHub now. Follow these commands

1. ```git add .```
2. ```git commit -m "merged dev with main```
3. ```git push```

Your branches should now be merged! You can go to GitHub and checkout the ```demo.txt``` and make sure all of the contents are available.

## Creating a Pull Request
Let's learn about pull requests.

You are now going to make a pull request on your partners ```git-demo``` project. 

Go to their project and click the ```fork``` button at the top right. Make sure you fork the project to your organization.

Forking will save the project to your GitHub account (you should see the project once it's forked).

*Do this in the projects directory. Your path should look like /Users/radhika/projects*

Now, clone the repo locally (in your terminal) by running ```git clone git@github.com:<your github username>/<repo name>``` This link is also available if you click on the code button in the repo (you just need to use ```git clone``` before the url).

Create a new branch with ```git checkout -b <your-name demo>``` For example, ```git checkout -b radhika-demo```

Create a new remote for the upstream repo with the command:

```git remote add upstream https://github.com/trainer-dot/random```

In this case, "upstream repo" refers to the original repo/parent repo you created your fork from.

Type in ```ls``` into the terminal and you should see the ```demo.txt``` file. Make sure text from you partner. Within the file, you can type in something to them!

Double check you are in your branch with ```git branch```

Follow these steps to push your new changes:

1. ```git add demo.txt```
2. ```git commit -m "added my comment for a PR"```
3. ```git push -u origin [branch]```

For (3) [branch] will be the branch name that you used without the brackets. For exmaple ```git push -u origin radhika-demo```

git push -u <branch>

Go to the GitHub project page, and click on ```pull requests```

You should see a green button that says ```New Pull Request``` that you should click on.

Add a descirption of what the PR contains, and ```create pull request```


## Accepting a Pull Request
Partner should go to ```pull requests```, click on the ```pull reuqest```, and as long as there are no conflicts you can ```merge the pull request```.






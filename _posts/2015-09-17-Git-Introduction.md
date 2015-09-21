---
layout: post
title: Git Workshop
smalltext: Christopher Chapline
summary: An introduction to version control with Git
tags: talk
---

We will cover the basics of version control and cover how to get started using Git. It is
recommended that you bring a computer to this workshop. If possible, please have git installed prior
to the workshop. You can download git [here](https://git-scm.com/).

The workshop will take place on the 17th of September at 7pm in Gould-Simpson 942. Below is a post
that outlines the topics covered during the workshop.

---

# Installation and Setup

There are many different ways that you can install the git platform, including downloading the
required packages from the [git website](https://git-scm.com/). In addition, there are some
platform-specific methods that can be used to download git that will be covered below.

#### Linux

On most Linux distributions, you can install git through your favorite package manager, such as
`apt-get` or `yum`. The installation commands are as follows:

apt-get:

```
sudo apt-get install git
```

yum:

```
sudo yum install git
```

If neither of these commands work for, determine which Linux distribution you are running and find
the appropriate commands for your package manager.

#### OSX

There are several ways to install git on OSX:

1. (1) Installing the [Xcode Command Line Tools](https://developer.apple.com/xcode/). Git is bundled
with these.
2. (2) Running git from the terminal will prompt installation on 10.9+
3. (3) Installing git via [Homebrew](http://brew.sh/)

If none of these methods work, git has more documentation that you can find
[on their website](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git#Installing-on-Mac).

#### Windows

Throughout this workshop, we will be working with the command line version of Git. To install the
command line version of git for Windows, you can either download the most stable build from the
[official git download](http://git-scm.com/download/win) or download the GitHub windows package,
which includes a GUI client, and is available [here](http://windows.github.com/).

# Creating a GitHub Repository

We will be assuming for the purposes of this workshop that you are using
[GitHub](https://github.com/) for your remote repository hosting, but other services such as
[GitLab](https://about.gitlab.com/) or [Bitbucket](https://bitbucket.org/) will work with all of the
commands discussed.

To create a GitHub repository, first go to the homepage and click on the "New Repository" button:

<img src="/public/github_homepage.png" width=720px alt="Homepage" />

From there, you will be presented with a form to name and describe your repository. In addition to
naming and describing the repository, it will also provide with some additional options. Adding a
README to your repository will allow you to describe your application to your users. For an
example, check out the
[uofa-acm README](https://github.com/uofa-acm/uofa-acm.github.io/blob/master/README.md). It will
also ask if you would like to add a gitignore to your repository. A gitignore will prevent you from
adding unnecessary files (binaries, output files, etc.) to your repository unless you explicitly
specify that you want it added. These help keep your repository clean. A repository with all of the
templates can be found [here](https://github.com/github/gitignore). Lastly, it will ask you to
supply a license describing the permissions you are giving to contributors and users of your work.
GitHub has created [this website](http://choosealicense.com/) to help your pick the right license
for you.

Once you have created your repository, you can move on to cloning your repository and begin working
on your project.

# Cloning your Repository

Having a remote GitHub repository is great, but how do you get that remote copy on your local
machine? The answer is `git clone`. Cloning takes a repository on a git server and creates a local
copy of that repository. On the project page for your repository, you will find a link on the
left-hand side that gives you multiple URLs you can use to clone your repository, including SSH
and HTTPS. For now, we will be using the HTTPS
URL.

<a href="/public/clone_links.png">
<img src="/public/clone_links.png" width=720px alt="Git clone links"/>
</a>

Once you have your url, type the following command into your terminal:

```
git clone <url>
```

Running, the above command, you should see something like this:

<a href="/public/git_clone.png">
<img src="/public/git_clone.png" height=130px alt="git clone output" />
</a>

Once your repository has successfully cloned, you can change into the directory for your repository
and see the contents. Before we move on, let's check the status of our repository with `git status`.
This will show us how our local repository has changed with respect to the remote repository:

<a href="/public/git_status.png">
<img src="/public/git_status.png" height=130px alt="git status output" />
</a>

As shown above, your git status should say that there is nothing to commit. Let's change that!

# Add → Commit → Push

The basic workflow in git involves staging files that you have changed and adding those files to
commits that you push to the remote repository. So let's create a file that we can add to our
repository, say hello_world.txt.

First let's create the file:

```
echo "Hello World" > hello_world.txt
```

Now, if you run git status, you should see something similar to the following:

```
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)

  hello_world.txt

nothing added to commit but untracked files present (use "git add" to track)
```

As you can see, git is telling us that the filled is "untracked". Git is telling us that it is not
currently tracking updates to the file (read: the file is new to the repository). So how do we fix
that? Well, the `git add` command does exactly what we need to. This command takes a file that is
currently unstaged (new, modified, removed, etc.) and stages that change to be committed. The
command takes as arguments on the command line a series of files or directories to be stage. So if
we want to stage our newly created file, we execute the following command:

```
git add hello_word.txt
```

Running git status after this will show us the following:

```
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

  new file:   hello_world.txt
```

Now that we have staged a file, we are ready to create a commit. A commit can be thought of as
a self-contained patch that is applied to the repository. To create a commit, you can run the
`git commit` command. Upon running this, an editor should open up that asks you to provide a git
commit message. This message is something that should what was changed in your commit provides
necessary details about why the commit is being made

Once you finish your commit message, running git status should output something like this:

```
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
nothing to commit, working directory clean
```

At this point, the only thing left to do is to push your changes to the remote repository:

```
git push origin master
```

# Collaboration

One of git's biggest strengths is that it makes collaboration between large teams incredibly
managable. There are several concepts that make interacting with teams of other developers less
painful and makes the lives of everyone involved easier.

#### Branching

Branching is a technique in git that allows you to create multiple histories branching off from
a single point.

<a href="https://www.atlassian.com/git/images/tutorials/collaborating/using-branches/01.svg">
<img src="https://www.atlassian.com/git/images/tutorials/collaborating/using-branches/01.svg" height=200px>
</a>

As an example, let's say that you have made several commits to the master branch of the repository
that you're working in. What happens if you want to work on a new feature without potentially
breaking the code for the other people who are using your code? Well if you create a branch, it
allows you to work and commit your work without directly affecting the people who are working with
the master branch. It allows you to sequentially develop your new feature until you have everything
working and then move all of the code over to the master branch without incrementally breaking
everyone else's code by accident.

Git makes branches incredibly easy to create:

```
git checkout -b <new-branch-name>
```

This command will create a branch and automatically switch to it. To list the branches you have
locally, you can run `git branch`. This will result in output similar to the output shown below:

```
  master
* new_branch
```

To switch between already created branches, you can use `git checkout`. For example, if I wanted to
switch to the master branch after creating new\_branch, I would run `git checkout master`.

So what happens when you have a branch that has a bunch of commits, and you want to copy those
commits into the master branch? Well then you've officially entered merge territory!

#### Merges

When you've finished work on the contents of a certain branch and you want to merge those changes
into a different branch, you must do several things. First of all, checkout your target branch.
This means that if you want to merge new\_branch into master, you should first run
`git checkout master`. After you have checked out the target branch, you're ready to start the merge
process. This is done with the following command:

```
git merge new_branch
```

This will, in most cases, result in output similar to the following:

```
Updating 1d91f95..4eda83d
Fast-forward
 a.txt | 0
 b.txt | 0
 c.txt | 0
 d.txt | 0
 e.txt | 0
 f.txt | 0
 g.txt | 0
 7 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt
 create mode 100644 b.txt
 create mode 100644 c.txt
 create mode 100644 d.txt
 create mode 100644 e.txt
 create mode 100644 f.txt
 create mode 100644 g.txt
```

Afterwards, your git status will note that you are currently some number of commits ahead of the
remote repository. This number is the number of commits the merged branch was ahead of the master
branch. In most simple cases, merges are relatively easy to handle. However, you might be asking
about what happens if two branches have modified the same file and then a merge is performed. This
situation will lead to one of two outcomes: (1) Git automatically resolves the merge and everything
is fine; or (2) Git is unable to automatically resolve the merge and results in a merge conflict.

In the case that your merge results in a conflict, the process for merging the code takes a more
manual process that is discussed below.

#### Merge Conflicts :(

Coming soon...

#### Forks and Pull Requests

Coming soon...

# Additional Resources

[Try GitHub](https://try.github.io/) - Try Git in your browser

[Git Cheatsheet](http://www.git-tower.com/blog/git-cheat-sheet/) - General tips for git

[Git Pretty](http://justinhileman.info/article/git-pretty/) - Cleaning up after your mistakes

[Git Commit Tips](http://chris.beams.io/posts/git-commit/) - Tips for writing better commit messages

[Intermediate Git](https://www.andyjeffries.co.uk/25-tips-for-intermediate-git-users/) - More
complicate git commands

[Pro Git](http://git-scm.com/book/en/v2) - Scott Chacon and Ben Straub's "Pro Git" book is available online for free. From very basics to git internals. Good stuff.

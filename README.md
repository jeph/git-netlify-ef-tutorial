# Git Netlify EF Tutorial

This document should help you get familiar with the way we are structuring our deploys. It'll also
give you basic git skills.

## Netlify

Netlify is really cool because it automatically deploys a website that represents every single push to
our repository. In software, there's this concept called continuous integration which is basically
a way of building software incrementally. The idea is that you can build software by adding small features
to it bit by bit and that each change you add on should be ready for production as soon as you push it.
This is where Netlify comes in. It allows us to manage which features we want our users to have and
deploy them with the push of a button. This is a brief overview of what you need to know.

When you go into the Netlify dashboard you'll see a window like this. This is really the only window
you need to work with.

![Netlify](img/netlify.png?raw=true "Netlify")

Every time a piece of code is pushed, Netlify will automatically deploy a version of the code
to a special URL that you can access to see and test the code in a production environment. To
get the URL and see what your website would look like in prod, click on the box corresponding with
the push and Netlify will give you the URL. 
The box in the window that says "Published" is the version of the code that is currently being
deployed to users. 

## Basic git and GitHub

Git is a version control system that allows you to keep track of different iterations of a piece of
the software you write. We like to use git because it allows us make changes of our code without
having to worry about making backups of it. It also allows multiple people to work on the same
code at the same time. It does a bunch of other stuff too but this is what we use it for.

This is going to be a very basic usage guide. If you already know how to use git even a little bit, 
you can skip this. 

To first be able to work on the website you'll have to clone it from the repository. To get the code
onto your machine, you'll need to download it. We call this cloning because it makes a copy of the
repository stored online and puts it on your local machine. To clone use:
```sh
git clone <repository url>
```

So to clone our website, you would use:
```sh
git clone git@github.com:jeph/nyu-ef-website.git
```

Cool! Now lets say you've made awesome changes to the website or implemented some new features.
You should backup your work and also show us. You can do that by pushing your code to the repository.
This will update the copy of the code stored online. You should build software incrementally and do this
often so that other members of the team have access the most recent version of the code.

First you'll have to stage your changes. By running:
```sh
git status
```

You'll get a list of all the files you've made changes to. To tell git that you want these changes
pushed to the repository, you'll have to stage them. To stage them use:
```sh
git add <file or files to stage>
```

To stage all files in the current and child directories, use:
```sh
git add .
```

Then commit the changes with a brief description of what you did 
```sh
git commit -m "A breif description of what you did"
```
If you forget -m, git will open up your default text editor and ask for a commit message. For the 
command line or terminal, this is usually vim. To exit vim, type ```:q``` and then hit enter.

Finally push using:
```sh
git push
```

When two people are working on code at the same time, one person will inevitably push code before the other.
When the other person goes to push code, they will first have to pull the changes that the first person made.
You don't have to worry about when to do this because git will prevent you from pushing until you pull.

To pull, use:
```sh
git pull -r
```

```-r``` stands for rebase. This will prevent merge commits from cluttering the commit history. Don't 
worry about what this means if you don't know, but please use ```-r``` when you pull.

Git will automagically merge the changes from the repository with your local changes of the code and
preserve changes from both sources. 

Sometimes, if two people have made changes to the same part of the code, git won't know which changes
to preserve and which to toss and you, the user, will have to tell git which parts to keep and delete.
This is called a merge conflict. When this happens, git will notify you and it's up to you to modify
fix it. This can be done rather easily through your IDE or Editor's merge conflict resolution tool.

I use IntelliJ which has a fairly intuitive conflict resolution tool. You can read more about it
[here](https://www.jetbrains.com/help/idea/resolving-conflicts.html). You can also read more about
how VSCode handles them [here](https://code.visualstudio.com/docs/editor/versioncontrol). Git also
has a commandline interface that allows you to handle merge conflicts but I would recommend not using
it as it is rather difficult to use with larger conflicts.

Once you've resolved all the conflicts, stage ur changes and push again.

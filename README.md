# Git Collaboration Strategies
Simplest and most effective Git strategies that I know


## Collaboration on a Project where you don't have push Privileges

Let us say you like some project so much that you want to contribute to it. Or maybe you find it so broken that you want to fix it. More often then not, you can view and download files but cannot change anything. Speaking the language of [Git](http://git-scm.com/) - *you don't have push privileges* to the project.

If you are in this situation, you may find this strategy useful. I really like the project [AngularJS UI Bootstrap](https://github.com/angular-ui/bootstrap) and **will use it as example here**. If you are not used to Git of feel intimidated by it, you are at the right spot - I'll try to make it as easy and clear as I can.


### Fork the project

Your first step is to **fork** the project. Easy enough if you haven't forked it already a while ago. However, if you did, and your forked repository hadn't been updated with more recent changes for a while, **your existing forked repository will not be updated to the most recent changes just because you click on the "fork" button!** In fact, updating appears to be harder than it probably should be. Maybe to prevent folks to overwrite their own stuff, who knows...


### Make sure your fork has exact copy of the original project

Most likely you want to have the exact copy of the project as it is to get started with. Assuming you do, the simplest solution I found is the following *brutal one*, which **you have to use at your own risk**:

- Just delete your previously existing forked repository and fork it again from the origin! That way you get the latest version and don't need any udpate.

So yes, the usual warnings and disclaimers apply, you can lose any work in that deleted repository, but really the same rules about backups (that you've doing already, have you?) apply to any work you do and store anywhere...


### Clone your forked repository to your machine(s)

In my example I have forked the AngularJS UI Bootstrap project as https://github.com/dmitriz/bootstrap. In contrast to the original project, I have full privileges to my forked one. For instance, I can fully syncronize it with my local machnies, which I couldn't easily do with the original project. 

Now that we have our forked copy, we `clone` it to our local machine, speaking the language of Git. There are two ways:

- Clicking the "Clone in Desktop" button on the main page of your fork, or
- Running this command in local terminal:
```
    git clone https://github.com/dmitriz/bootstrap.git
```
For the first to work, you'd need to install Github's desktop application on your machine, and for the second, you need to [install Git](http://git-scm.com/downloads), which you'll likely need anyway...


### Make sure we have the most recent version on our machine

Who knows, as you were busy forking and cloning, someone could have already sent a new update to the original project. So here is my first rule:

- *Rule 1. I want my `master branch` to be clean at all times and reflect the latest changes as much as possible.*

That means, I never change anything there and try to update it regularly or whenever I need.

*What is a branch?. It is common to give a long explanation [what a branch is](http://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell). But in a real tiny nutshell - a branch is just a version of your code. It is like switching between directories containing different versions, except that Git does the switching for you in the same directory, and uses much less space for it.*

As you `cloned` your forked repository and entered its directory, you are (should be) in your local `master branch`. Here `master` is the common name for the main branch, which is like the main version of the code. Check that you are on `master` by
```
    $ git status
    # On branch master
    nothing to commit, working directory clean
```
It is often recommended to keep your `master branch` **deployable at any time**. In our situation we rely on the original project to be deployable, and simply try to syncronise it with the `upstream` at all times.

*What is upstream?. Another buzzword - [see this StackOverflow thread for a long discussion](http://stackoverflow.com/questions/2739376/definition-of-downstream-and-upstream). Similar to a waterfall, where water is falling on you, with you having no control on it when standing below, Git's `upstream` is the original code that we can't influence directly.  In our example, `upstream` is the name (string) that is commonly used to point to our original repository. [A so-called Remote](http://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes) if speaking Git language.*

Let us set our `upstream`, so Git will know where to get the updates:
```
    $ git remote add upstream https://github.com/angular-ui/bootstrap
```
and check it with:
```
    $ git remote -v
    origin	https://github.com/dmitriz/bootstrap.git (fetch)
    origin	https://github.com/dmitriz/bootstrap.git (push)
    upstream	https://github.com/angular-ui/bootstrap (fetch)
    upstream	https://github.com/angular-ui/bootstrap (push)
```
And now that we have set it, here is **my preferred and only command to update to most recent changes**:
```
    $ git pull --rebase upstream master
    From https://github.com/angular-ui/bootstrap
     * branch            master     -> FETCH_HEAD
    Current branch master is up to date.
```
This one commands is doing a lot - it checks for all new changes in the `ustream` since you updated last time, downloads them and updates your `master branch` (or whatever branch you are currently in). If you observe my *Rule 1* and never make any changes to your `master branch` (other than updates), this should always work smoothly. 

If, however, you've made some new local changes since your last update, the same command will try to do more for you - it will attempt to make all `upstream` changes **ahead of your new local changes**. And this is exactly how you want it - see below...

*Note. The option `--rebase` is important. Without it, Git would try to download the recent changes and `merge` them into your local `branch`. It won't matter for your `master` (if you observe Rule 1), but would matter for other `branches` where you do make changes. And we want to keep our life sane by remembering just one command instead of 10. ;-)


### Branch out and begin working

Now the most interesting part begins!
Finally we can work and do cool things!
But remember Rule 1 - don't mess with `master branch`.
So we first want to copy the `master` into a new `branch`:
```
    $ git checkout -b new-branch
    git checkout -b new
    Switched to a new branch 'new'
```
That's it! Now we can start working and mess around.





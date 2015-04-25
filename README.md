# Git Collaboration Strategies
Simplest and most effective Git strategies that I know


## Collaboration on a Project where you don't have push Privileges

Let us say you like some project so much that you want to contribute to it. Or maybe you find it so broken that you want to fix it. More often then not, you can view and download files but cannot change anything. Speaking the language of [Git](http://git-scm.com/) - *you don't have push privileges* to the project.

If you are in this situation, you may find this strategy useful. I really like the project [AngularJS UI Bootstrap](https://github.com/angular-ui/bootstrap) and **will use it as example here**.


### Fork the project

Your first step is to **fork** the project. Easy enough if you haven't forked it already a while ago. However, if you did, and your forked repository hadn't been updated with more recent changes for a while, **your existing forked repository will not be updated to the most recent changes just because you click on the "fork" button!** In fact, updating appears to be harder than it probably should be. Maybe to prevent folks to overwrite their own stuff, who knows...


### Make sure your fork has exact copy of the original project

Most likely you want to have the exact copy of the project as it is to get started with. Assuming you do, the simplest solution I found is the following *brutal one*, which **you have to use at your own risk**:

- Just delete your forked repository and fork it again! 

So yes, the usual warnings and disclaimers apply, you can lose any work in that deleted repository, but really the same rules about backups (that you've doing already, have you?) and such apply pretty much to any work you do anywhere...


### Clone your forked repository to your machine(s)

In my example I have forked the AngularJS UI Bootstrap project as https://github.com/dmitriz/bootstrap. In contrast to the original project, I have full privileges to my forked one. For instance, I can fully syncronize it with my local machnies, which I couldn't easily do with the original project. 

Now that we have our forked copy, we `clone` it to our local machine, speaking the language of Git. There are two ways:

- Clicking the "Clone in Desktop" button on the main page of your fork, or
- Running this command in local terminal:
```
    git clone https://github.com/dmitriz/bootstrap.git
```
For the first to work, you'd need to install Github's desktop application on your machine, and for the second, you need to [install Git](http://git-scm.com/downloads), which you'll likely need anyway...


Git Team Workflow
=================



## Summary ##
  

   * The idea is to create a copy of the `master` (stable branch) which will be called `develop`.
   * Each time you decide to introduce a feature or make significant changes you create your branch with a descriptive name.
   * When your feature is complete and tested, merge with the `develop` branch.
   * The `master` branch will act as the clean stable release which we will merge from the `develop` branch once we’ve collectively reviewed the changes.



## Workflow Commands ##


+ Do a git pull on the `develop` branch before creating your branch so you work on an upto date copy

```git
# use the develop branch
git checkout develop

# the default origin is 'master' so specify origin as 'develop' for the pull request
git pull origin develop
```


+ Create your branch as a copy of the develop branch

```git
# the -b flag tells git to create the branch if doesn't exist
git checkout -b [branch-name] develop

# view branches (you will see an asterix on your working branch)
git branch -a
```

+ Work on your branch and commit your changes.


+ Push your branch to the repo if required

```git
git push [branch-name]
```


+ Merging with the `develop` branch

```git
# move into develop branch
git checkout develop

# ensure you have the latest copy
git pull origin develop

# do the following if you have multiple commits in your branch
# the --squash flag removes all commit messages and gives you the opportunity to  
# commit to the develop branch with a single commit message
# otherwise all commit messages will be imported to the develop branch

git merge –-squash [branch-name]

# adding [branch-name] to develop branch
git commit -m ‘one line comment'
```


+ Update your git config file if required

```git
# location: .git/config

Change url field to include username i.e:
url = https://[username]@github.com/haani-niyaz/teamworkgit.git
```


+ Once merging is complete push to the `develop` remote branch

```git
git push origin develop
```




### Useful Commands ###

+ Push all branches to remote repositories

```git
git push -all
```



+ Instead of doing a git pull you can do the following to check what is different between the remote and local:

```git
# fetch remote branch within local branch
git fetch 

# compare changes
git diff ..origin/develop
```







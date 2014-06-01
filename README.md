Git Team Workflow
=================



## Summary ##
  

   * The idea is to create a copy of the `master` (stable branch) which will be called `develop`.
   * Each time you decide to introduce a feature or make significant changes you create your branch with a descriptive name.
   * When your feature is complete and tested, merge with the `develop` branch.
   * The `master` branch will act as the clean stable release which we will merge from the `develop` branch once we’ve collectively reviewed the changes.



## Workflow Commands ##


+ Do a git pull on the `develop` branch before creating your branch so you work on an upto date copy

```python
# use the develop branch
git checkout develop

# the default origin is 'master' so specify origin as 'develop' for the pull request
git pull origin develop
```


+ Create your branch as a copy of the develop branch

```python
# the -b flag tells git to create the branch if doesn't exist
git checkout -b <branch-name> develop

# view branches (you will see an asterix on your working branch)
git branch -a
```

+ Work on your branch and commit your changes.


+ Push your branch to the repo if required

```python
git push <branch-name>
```


+ Merging with the `develop` branch

```python
# move into develop branch
git checkout develop

# ensure you have the latest copy
git pull origin develop

# do the following if you have multiple commits in your branch
# the --squash flag removes all commit messages and gives you the opportunity to  
# commit to the develop branch with a single commit message
# otherwise all commit messages will be imported to the develop branch

git merge –-squash <branch-name>

# adding [branch-name] to develop branch
git commit -m ‘one line comment'
```


+ Update your git config file if required

```python
# location: .git/config

Change url field to include username i.e:
url = https://<username>@github.com/haani-niyaz/teamworkgit.git
```


+ Once merging is complete push to the `develop` remote branch

```python
git push origin develop
```



#### Using Tags  ####

+ Tags can be used to setup versions. You can also use it to capture working states of the code.

```ruby

# display tags
git tag

# create a tag i.e: v1.0
git tag v1.0 -m "Added new feature1"

# push to remote
git push origin v1.0


# switch to the point in time of using a tag
git checkout v1.0

# delete a tag locally
git tag -d v1.0

# delete a remote tag
git push origin :v1.0


```



### Useful Commands ###

+ Push all branches to remote repositories

```python
git push -all
```



+ Instead of doing a git pull you can do the following to check what is different between the remote and local:

```python
# fetch remote branch within local branch
git fetch 

# compare changes
git diff ..origin/develop
```


+ Comparing 2 branches

```python

# show the changes
git diff develop..bug_fix

# only shows which files have changes
git diff --name-status develop..bug_fix

```

+ Deleting a branch

```ruby

# deleting a local branch
git branch -d bug_fix

# deleting the corresponding remote branch (if it has been pushed)
git push origin :bug_fix

```






## Introduction to GitHub

The power in GitHub lies in version control. Code is often changed and in doing so previous versions of files can easily be lost. GitHub saves changes to files so that one can go back and restore previous versions if needed. Additionally, there is a plethora of functionality to: update code collaboratively, publish static website pages, report issues with code, etc..

## Creating a Git Repository

- To create a Git Repository by:

```
# change into your project directory
cd /path/to/your/project

# initialize the repository
git init
```

## Add/Commit Files

- To add files to be tracked:

```
# add files to be tracked
git add main.py input.txt 
```

- To commit these files to your Git Repository:

```
# commit the files to the repository, creating the first snapshot
git commit -m "Initial Commit"
```

## Configure Your Credentials

- To configure your credentials:

```
# configure your user name/email
git config --global user.name "Your Name"
git config --global user.email "[email address]"
```

## Push To GitHub

- Currently, these files are not on github. To add them to Github:

```
## push files to github
git remote add origin git@github.com:user_name/my_new_repo.git
git push -u origin master
```

## Going Further

- GitHub has much more functionality than what has been described here. To learn more, check out:

!!! info "[GitHub Docs](https://docs.github.com/en){:target="_blank" rel="noopener"}"

## References

!!! abstract ""
    1. [GitHub Docs](https://docs.github.com/en)

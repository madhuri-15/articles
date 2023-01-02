### Article link
[Getting started with Git & GitHub](https://medium.com/@madhuri15/getting-started-with-git-github-2088e7a8786f)

### Git Commands

```shell
# To check version of installed git
$ git --version
git version 2.32.1.windows.1
```
#### Configure Git
- Setting your username in Git
```shell
$ git config --global user.name "YOUR USER NAME"

# To check username
$ git config --global user.name
> YOUR USER NAME
```
- Setting your commit email address
```shell
$ git config --global user.email "YOUR_EMAIL"

# To check email address
$ git config --global user.email
"YOUR_EMAIL"
```
#### Repositories
- To create a new repository locally
```shell
$ git init
# Or
$ git init "REPOSITORY_NAME"
```
- To link the local repository to an empty GitHub repository.
```shell
$ git remote add origin [url]
```
- Cloning a repository
```shell
$ git clone [url]
```
- Adding a file to the repository
```shell
# To add a single file in repo
$ git add [FILE NAME]

# For adding multiple similar files with same extension
# For example adding all python files from folder to repo
$ git add .py

# To add all files
$ git add .
```
#### Branches
- To create a new branch
```shell
$ git branch [branch-name]
```
- To switch to the specific branch and update the working directory
```shell
$ git switch -c [branch-name]
```
- To save/commits a changes
```shell
$ git commit -m "[descriptinve message]"
```
- To check the status of the current branch

```shell
$ git status
```
- To merge a branch
```shell
# Change will merge into Specified branch's history into a current branch
$ git merge [branch]
```
- To delete a branch
```shell
# Deletes the specified branch
$ git branch -d [branch-name]
```

#### Synchronize changes
- To download all history from remote-tracking branches
```shell
$ git fetch
```
- Uploads all local branch commits to GitHub
```shell
$ git push REMOTE-NAME BRANCH-NAME

# You usually run following command to push your commits
$ git push origin main
```
- Update your current local repo with a corresponding remote repo
```shell
$ git pull
```

- To view lists of version history for the current branch
```shell
$ git log

# To view version history for a particular file
$ git log --follow [file]
```
- To view the differences between the two branches
```shell
$ git diff [first-branch]...[second-branch]
```

- Output metadata and content changes of the specified commit
```shell
$ git show [commit]
```







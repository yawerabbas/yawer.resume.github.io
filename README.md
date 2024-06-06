## How to Contribute to an Open Source Project on Github

This is a course that I found on [egghead](https://egghead.io/lessons/javascript-introduction-to-github).<br/>
We will be contributing to [repo](https://github.com/eggheadio-github/stack-overflow-copy-paste).

  The github website is very interactive and understandable.

### Repository structure

GitHub adds a lot of great features on top of git repository hosting. We’ll take a look at some of these features including:

-How to create a repository and organization on GitHub
-How to explore and find projects on GitHub
-About GitHub gists
-Searching pull requests and issues on GitHub

On github, along with the folder structure of the project, there are gui options to help in contribution.

- fork to make local repo of the project
- Issues to communicate with the project maintainer
- Pull requests 
- Wiki for contributing guidelines
- Code to clone or download and many more

### Installation

Check if github is present on the system. 
```bash
$ git --version

```
For installing on mac:
```bash
$ brew install git

```

For more details go to the [downloads page](https://git-scm.com/downloads)

### Configuration

```bash
$ git config --global user.name "name"
$ git config --global user.email "name@server.com"

```

#### gitignores

[gitignore](https://github.com/github/gitignore/blob/main/Global/macOS.gitignore)

paste this in .gitignore_global file in ~.
```
# General
.DS_Store
.AppleDouble
.LSOverride

# Icon must end with two \r
Icon

# Thumbnails
._*

# Files that might appear in the root of a volume
.DocumentRevisions-V100
.fseventsd
.Spotlight-V100
.TemporaryItems
.Trashes
.VolumeIcon.icns
.com.apple.timemachine.donotpresent

# Directories potentially created on remote AFP share
.AppleDB
.AppleDesktop
Network Trash Folder
Temporary Items
.apdisk
```

### Authentication using SSH

To generate id_ssh.pub for public key.

```bash
$ ls -la ~/.ssh

$ssh-keygen it rsa -b 4096 -C email #to generate key-pair

```

```bash
$eval "$(ssh-agent -s)"
$ssh-add ~/.ssh/id_rsa
$pbcopy < ~/.ssh/id_rsa.pub

```

Then goto github->Your profile->Edit profile-> SSH key-> add

Test 

```bash
$ ssh -T git@github.com
```

### Credential Storage

```bash
$git config credential.helper store
$git config --global credential.helper store
```

### Contribution

- Find issues you want to contribute to 

You cannot push code to repositories that you don’t own or have sufficient permission to. So instead, you make your own copy of the repository by “forking” it. You are then free to make any changes you wish to your repository.

Fork -> Clone using ssh ->  

#### Initial setup with upstream

Before you start making your changes, you often need to set up your environment for the changes. This is where the repositories' contributing instructions come in really handy. In this lesson we’ll get our environment set up and ready for changes.

To keep up with original project
```bash
$ git remote add upstream "ssh link"

$ git fetch upstream  

$ git branch --set-upstream-to=upstream/master master #local master points to upstream master

```

-> make branch according to CONTRIBUTING.md
```bash
$ git checkout -b pr/padLeft
# make changes
$ git status
$ git diff

$ git add .
$ git commit -m "message"
$ git push -u origin #remote(upstream) #local-branch 
$ git push --set-upstream origin #remote(upstream) #local-branch
```

->Create pull request-> coverage report -> CI/CD -> Update

```bash
$ cat .travis.yml
$ git commit --no-verify #to skip hooks

```
->Merge Conflicts

Sometimes your Pull Request can fall behind master in a repository and occasionally that will result in merge conflicts which you have to manage yourself. In this lesson we’ll learn how to use git rebase to update our pull request branch to the latest version of master and resolve merge conflicts with git.

```bash
$ git fetch upstream
$ git rebase upstream/master
$ git diff 
# make changes
$ git add .
$ git rebase --continue
$ git rebase --abort
$ git log
$ git push -f

#squashing multiple commits
$ git rebase -i sha

```

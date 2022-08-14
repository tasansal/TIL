# Common Git Patters

Common Git CLI patterns will be described here. This not only includes `Git` itself, and it also includes the GitHub CLI.

[[TOC]]

Git: [Link](https://git-scm.com)  
GitHub CLI: [Link](https://cli.github.com)

## Initialize Git Locally

```shell
git init
```

Documentation [here](https://git-scm.com/docs/git-init).

## Add All Files to Initialized Git

This is if the project already exists and you want to add the files to the newly initialized local Git repo. If you are starting from scratch, you can add as you go.

Adding existing project files.

```shell
git add .
```

If you want to exclude files, after adding all:

```shell
git reset -- file1 file2 ...
```

After adding or modfying files, don't forget to commit.

## Add Remote to Local Git

After we create the remote (i.e. GitHub repo), we can add it as the remote origin for the local repository.

```shell
git remote add origin <link to repo>
```

## Login to GitHub CLI

```shell
gh auth login
```

More arguments [here](https://cli.github.com/manual/gh_auth_login).

## Create GitHub Repo from CLI

```shell
gh repo create [<name>] --public  # public repo
gh repo create [<name>] --private  # private repo
gh repo create org/repo  # create repo under org
```

More arguments [here](https://cli.github.com/manual/gh_repo_create).

## Add GitHub Repo as Origin to Local Git

```shell
```
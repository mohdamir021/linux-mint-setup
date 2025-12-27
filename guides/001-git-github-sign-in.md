# GitHub Sign In in Git

### Login in

One way to log into `git` locally is to clone any repo you have in GitHub.

And you will see something like this:

```
git clone https://github.com/user123/portfolio-web.git
Cloning into 'portfolio-web'...
Username for 'https://github.com': user123
Password for 'https://user123@github.com': 
```

The password is the Personal Access Token (PAT) that you generate on GitHub settings.

Personal access tokens are an alternative to using passwords for authentication to GitHub when using the GitHub API or the command line.

Personal access tokens are intended to access GitHub resources on behalf of yourself. To access resources on behalf of an organization, or for long-lived integrations, you should use a GitHub App. For more information, see About creating GitHub Apps.

A token has the same capabilities to access resources and perform actions on those resources that the owner of the token has, and is further limited by any scopes or permissions granted to the token. A token cannot grant additional access capabilities to a user. For example, a personal access token can be configured with an admin:org scope, but if the owner of the token is not an organization owner, the token will not give administrative access to the organization.

* Be sure to save that token somewhere in case you want to log in

### Set up name and email in Git
Run this command to setup name and email to commit in vscode

```
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```


### VS Code login

It is straightforward af so don't mind.

You only need an active email address to get your code.
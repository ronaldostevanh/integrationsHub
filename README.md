# Integrations Hub

Next, you can find the flow configuration step by step the how you can set up your working directory to compile the project integrations Hub.

## Instructions : requirements for .npmrc 

In the project you'll find the next file called `.npmrc.example` which can serve to be a guide that how can configure the `.npmrc` for access to provate libraries, with the next context:

```bash
@homecu:registry=https://npm.pkg.github.com
//npm.pkg.github.com/:_authToken=<AUTH_TOKEN>
```
In this part you need to have an authentication token generated in the github setting option, if you don't have please follow the next steps:

- 1). Please go to the github option and click on *Settings*.
- 2). Go down scrolling until find the *Developer Settings* option and click on it.
- 3). Click on *Personal access token* option and then *Tokens (classic)*.
- 4). Go up and click on *Generate new token*, it splits option there and click on *Generate new token (classic)*
- 5). It'll request to log in again, please log in.
- 6). Once you log in, your need to granted all the select all the access that you want this token would has in git enviornment, please select all those project needs. (we recommend all associate with admin: and write.

 Once you have a token, please create a file called `.npmrc` and there add the script seen in the `.npmrc.example` replacing the *<AUTH_TOKEN>* by your token.

## Instructions : requirements for SSH key generation for git commands and retrieving repo.

For perform `git clone`  command in your working directory you need to have a SSH key active in git hub, if you have please skip this part, else please take a special attention to the next steps:

- 1). Please go to the github option and click on *Settings*.
- 2). Click on *SSH and GPG keys* option.
- 3). In your working directory please add your email using the following command.
 ```bash
git config --global user.email <mail from blossom (example: user@blossom.net)>
 ```
- 4). 


 ## Set up for compile project.

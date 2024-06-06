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
- 4). Once config your email, please make a authentication using github command to prove it.
- 5). Using the next command you can generate a new SSH key.
```bash
ssh-keygen -t rsa -b 4096 -C "<email from blossom>"
```
  this command will ask your about where you want to save that new SSH key, so you can set the dummy file for saved temporary using `.txt` extension.
- 6). Copy all the key with the next pattern in your file with the `.txt.pub` extension.
  ```bash
  ssh-rsa <ALPHANUMERIC_CODE> <email from blossom>
  ```
- 7). Go to the *SSH and GPG Keys* config in github and click on the top of page the button *New SSH Key*
  - There add the title that you want for this SSH key (example: *BlossomAccess*).
  - In the Key Type option please let it *Authentication Key*.
  - At the container below please add pattern copied from the step 6), and please click on *Add SSH Key*.

Now you're able to apply the next command to clone the repo's project in your working directory.
```bash
git clone git@github.com:homecu/BlossomIntegrationsHub.git
```

 ## Set up for compile project.

With the idea to compile all the requirements please install `nvm` library with the next command:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash
```
Install the `serverless` package with:

```bash
npm i - D @types/serverless
```
To configure the enviornment to use `nvm use` automatically, we need to add to `.zshrc` file the next script, please access to this file using `nano ~/.zshrc` then scroll until the end of the file and paste the next code:


- **Note**: If LDFLAGS exist just comment with *#* and use the version that is indicate next.

```bash
export LDFLAGS="-L/opt/homebrew/opt/openssl@3/lib"
export CPPFLAGS="-I/opt/homebrew/opt/openssl@3/include"

# Auto-load .nvmrc
autoload -U add-zsh-hook

load-nvmrc() {
  local node_version="$(nvm version)"
  local nvmrc_path="$(nvm_find_nvmrc)"

  if [ -n "$nvmrc_path" ]; then
    local nvmrc_node_version=$(cat "$nvmrc_path")
    if [ "$nvmrc_node_version" = "lts/*" ]; then
      nvmrc_node_version="$(nvm version-remote --lts)"
    fi
    if [ "$nvmrc_node_version" != "$node_version" ]; then
      nvm install "$nvmrc_node_version"
    fi
  elif [ "$node_version" != "$(nvm version default)" ]; then
    echo "Reverting to nvm default version"
    nvm use default
  fi
}

add-zsh-hook chpwd load-nvmrc
load-nvmrc
```
Once you update `.zshrc` file saving the changes, please run the next command line to load the project's require version for node.
```bash
source ~/.zshrc
```

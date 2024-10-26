## Contents
| Lesson | Lesson name |
| ------------- | ------------- |
| 1 | [Linux git setup](https://github.com/AritraLikhan/Lia/blob/main/README.md#Linux-git) |
| 2 | [Linux ls command](https://github.com/AritraLikhan/Lia/blob/main/README.md#Linux-ls-command) |


## Linux-git
### Installation process

```
sudo apt update
sudo apt install git
```
### Initialization process
>To initialize a git in local repository:
```
git init
```
>To uninitialize a git in remote repository:
```
rm -rf .git
```
>To check git status:
```
git status
```

### SSH setup process
> Since Github no longer supports login with username and password from bash, we depend on ssh for authentication and remote transfer purpose. We are to generate a ssh key of our local linux system and then add it to our linux account.
>To generate a ssh key (press enter key 4 times after the following line):
```
ssh-keygen -t rsa -b 4096 -C "aritralikhan2001@gmail.com"
```
>To add the SSH Key to the SSH Agent:
```
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```
>To copy the key from id_rsa.pub (copy the rsa key from the terminal following an enter of the command below):
```
cat ~/.ssh/id_rsa.pub
```
>Paste(add) the key from following Github url giving the key a title: 
https://github.com/settings/ssh/new

### Push to remote Github
> Open a directory:
```
mkdir Lia
```
>Run the following commands:
```
git init
touch README.md
git add .
git commit -m "README added" 
git branch -M main
git remote set-url origin git@github.com:AritraLikhan/Lia.git
git push -u origin main
```
## Linux-ls-command
>To see all the subdirectories and files under a directory, simply write its absolute or relative path:

Absolute path:
```
ls path/to/directory_name
```
Relative path:
```
ls ../directory_name
```
###Note: we can use simply 'ls directory_name' in the following cases:
>If the directory 'directory_name' is under the current directory, for example, if our current directory is '/home/aritralikhan2001', we can run the following:
```
ls Documents 
```
>If the directory 'directory_name' is '/home' or '/' (root):
```
ls /home 
```







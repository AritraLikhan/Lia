## Contents
| Lesson | Lesson name |
| ------------- | ------------- |
| 1 | [Linux git setup](https://github.com/AritraLikhan/Lia/blob/main/README.md#Linux-git) |
| 2 | [Linux ls command](https://github.com/AritraLikhan/Lia/blob/main/README.md#Linux-ls-command) |
| 3 | [Linux cd command](https://github.com/AritraLikhan/Lia/blob/main/README.md#Linux-cd-command) |
| 4 | [Linux file operations(create,view,append with cat)](https://github.com/AritraLikhan/Lia/blob/main/README.md#Linux-file-operations) |
| 5 | [Linux directory operations](https://github.com/AritraLikhan/Lia/blob/main/README.md#Linux-directory-operations) |




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
### Note: we can use simply 'ls directory_name' in the following cases:
>If the directory 'directory_name' is under the current directory, for example, if our current directory is '/home/aritralikhan2001', we can run the following:
```
ls Documents 
```
>If the directory 'directory_name' is '/home' or '/' (root):
```
ls /home 
```
>To see the list one directory backward the current directory(Lia):
```
ls ..
```
>To see the list two directories backward the current directory(Lia):
```
ls ../..
```
>To see all the files and directories including the hidden ones (suppose .git file in current directory Lia):
```
ls -a
```
>To see the list of files of a specific type, say, we wanna see the list of html files under a directory (current directory: /home/aritralikhan2001):
```
ls Lia/*.html
```
>To save the list into a text file (current directory: /home/aritralikhan2001):
```
ls Lia > out01.txt
```
>To see list of directories only (current directory: /home/aritralikhan2001):
```
ls -d */
```
>To see list of files only (current directory: /home/aritralikhan2001):
```
ls -f */
```
## Linux-cd-command
>To go to any directory:
Absolute path:
```
cd path/to/directory_name
```
Relative path:
```
cd ../directory_name
```
>To navigate to parent directory:
```
cd ..
```
>To navigate to root directory:
```
cd 
```
>To navigate to a directory whose name has space(s) :
```
cd 'directory name'
```
## Linux-file-operations
>To create a file and write a file:
```
cat > file01.txt #(enter)
```
```
Coding is not boring, 
```
```
But it takes a lot of patience; 
```
```
```
```
So hard for a lazy guy like me :"( 
```
Then press ctrl+d to end terminal inputs

>To see file contents: 
```
cat file01.txt
```
>To concatenate two files' contents and see them in the terminal (suppose we already have another text file file02.txt):
```
cat file02.txt file01.txt
```
>To concatenate two file contents and store it to a different file:
```
cat file01.txt file02.txt > file03.txt
```
>To append input from terminal to a file:
```
cat >> file01.txt
```
```
One Piece is most popular in Japan
```
Then press ctrl+d to end terminal inputs

>To append one file content to another : 
```
cat file02.txt >> file03.txt
```
>To concatenate multiple files and append to another file (assuming we already have file 'file04.txt'):
```
cat file01.txt file02.txt file03.txt >> file04.txt
```

## Linux-directory-operations
>To create directory (for example 'dir'):
```
mkdir dir 
```
>To create subdirectories inside an existing directory (for example 'subdir'):
```
mkdir dir/subdir 
```
>To directly create a directory hierarchy:
```
mkdir -p dir/{subdir01,subdir02} 
```
>To see the hierarchy of subdirectories and files within the current directory:
```
ls -R
```
>To remove only the top-level subdirectories if the following note's condition is satisfied (leaf nodes of the tree) (assuming 'dir/subdir01/{subdir011,subdir012}' path exists):
```
rmdir dir/subdir01/{subdir011,subdir012} 
```
>To delete the whole directory (assuming 'dir/subdir01/{subdir011,subdir012}' path exists):
```
rmdir -p dir/subdir01/{subdir011,subdir012} 
```
### Note: Don't try to delete the whole directory simply using "dir/subdir01/{subdir011,subdir012}" , it will prevent deletion if at least one of the subdirectories contain files/subdirectories not mentioned in the path

>To delete everything within a directory (current directory 'Lia' contains 'dir'):
```
rm -r dir
```
### Note: '-r' flag stands for recursive, that means if we have a directory path like: 'dir/subdir01/subdir011' , 'rm -r dir' will delete like this: dir/subdir01/subdir011 -> dir/subdir01 -> dir -> all gone.

>To copy files from current directory to any directory:

### Case-1: From any directory to any directory:
```
find /home/aritralikhan2001/Lia -type d -name "subdir011" -exec cp Otto.txt Rem.html {} \;
```
Here, 
-- find /home/aritralikhan2001/Lia -type d -name "subdir011" : finds the exact path for "subdir011" within the known path '/home/aritralikhan2001/Lia' (destination directory's exact path is unknown)
-- cp Otto.txt Rem.html {} \ : copies the files Otto.txt, Rem.html
-- -exec : executes the copy operation based on the path found

### Case-2: From any directory to its ancestor directory:
```
cp Otto.txt Rem.html ../Documents
```
### Case-3: From any directory to a successor directory:
Since one may reach the successor through a number of possible paths, it's impossible for the source directory to decide which path will exactly reach the successor, therefore, we have no specific way to do it. We can follow the solution for case-1 in this case. 

>To copy one directory along with all its subdirectories and files to another directory: 
```
cp -r 'My list' dir/subdir01/subdir011
```
>To copy a file to its current directory with a different name: 
```
cp Otto.txt Subaru.txt
```
>To copy to another directory with a new name: 
```
cp -r 'My list'/list.txt dir/subdir01/subdir011/mylist.txt
```
>To copy all files of a specific type to a destination directory:
```
cp *.html dir/subdir01/subdir012
```
>> All move commands are similar to cp command so not being showed



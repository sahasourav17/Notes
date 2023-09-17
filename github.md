# Github Useful Commands

## Configuring GitHub with SSH key

```bash
mkdir .ssh
cd .ssh
ssh-keygen -t rsa -b 4096
ls
cat id_rsa.pub
```

Now, copy the generated ssh key into the github's `SSH and GPG setting`

## Initialize a new git repository

```bash
git init
touch README.md # create an empty file in your local repo directory to track it as part of version control
git add --all    # stage all files for committing them later on (this is optional)
git commit -m "write your commmit message here"
git remote add origin <remote-url>   ## this will be used by other developers to clone or pull from you repository
git branch -M main
git push -u origin main
```

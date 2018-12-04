## Introduction
- Git is a free and open-source version control system, that helps you keep track of changes to files in a 
  filesystem/repository over time. It has been an industry standard for a while now. Git comes with the git-shell 
  which has a set of nifty commands that can help you do all sorts of things on your repositories.
- Github is a service that hosts your repositories online and lets you collaborate with others through it. You can 
  use Github through the browser or the git-shell on your pc.

## How to Install Git and Github
- ***Windows***: https://hackernoon.com/install-git-on-windows-9acf2a1944f0

- ***Linux***: For Debian and Ubuntu - ```sudo apt-get install git```  
and check git version using - ```git --version```

- ***MacOS***: https://hackernoon.com/install-git-on-mac-a884f0c9d32c

## Commands you'll need in this project
>First, create a github ID, then move on.

- Clone the IECSE ML Winter Project repository  
```git clone https://github.com/ramrathi/IECSE-ML-Winter18```

- Initialize a repository in directory(this is just for information, you won't need to use this for any task) 
 ```git init <Project Name>```

- Create a branch  
```git checkout -b <branch-name>```

- Change into another branch  
```git checkout <branch-name>```

- Adding Files to be committed  
```git add <filename1> <folder_name>\<filename2>``` - Adds filename1 in current directory and filename2 in the 
  folder.  
```git add .``` - Adds all files in the current directory

- Adding a commit message  
```git commit -m "<message>"```

- checking status of files  
```git status```

- Pushing the committed changes to the GitHub repository  
```git push origin <branch-name>```  
Note: Never push to the master branch, create your own branch and change into that and then push.

- Pulling changes from the GitHub repository  
```git pull origin <branch-name>```

Detailed article on Git and Github: https://medium.com/@abhishekj/an-intro-to-git-and-github-1a0e2c7e3a2f
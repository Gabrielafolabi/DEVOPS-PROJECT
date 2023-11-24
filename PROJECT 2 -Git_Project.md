# *GIT* 

This document will show basic collection of tasks that is commonly done on GIT. 
GIT is a powerful version control system widely used in software development. It is a distributed version control system. 
It might interest you to know that GIT essentially help to solve the problem of sharing source code efficiently and also keep track of any changes done on the 
source code.
Before Git there are other technologies  e.g SVN
SVN solves the problem, but poses a lot challenge. In SVN , there exist a central repository which is a major draw back. which makes it difficult for developers to collaborate because changes can only be made one at a time.
However, GIT adopted a different approach by allowing developers to make their own copy of the central repository. That is why it reffered to as a Distributed Version Control System.
Below are some of the actions done on GIT:

## *Initiaizing a Git Repository*
- Open the terminal on your computer, in this case (git bash)
- create a working directory on your terminal with command  (mmkdir DevOps)
- change in to the newly created directory above with the command ( cd DevOps)
- Then, while your are in the folder run the command (git init) ...this command initialize the Git.

![image](https://github.com/Gabrielafolabi/DEVOPS-PROJECT/assets/35296784/71330bea-a710-4e77-89fd-fec07a66086b)


## *Making a Commit*
Commit is saving the changes you have made to your file. When you make a commit, git takes a snapshot of the current state of your repository and saves a copy in the .git folder inside your working directory.

- Inside the new directory you created, create a file index.txt using the command ( touch index.txt)
- write any sentence inside the text file using the command ( echo "I like using Git hub" > index.txt )
- Add your changes to git staging area using the  command ( git add .)
- Then commit your changes to git using the command ( git commit -m "intial commit"). The -m flag is used to provide commit message or description of your commit.

 ![image](https://github.com/Gabrielafolabi/DEVOPS-PROJECT/assets/35296784/e3690c5f-e3bb-403e-b0c2-efbb7a52bdfb)

## *Working with Branches*
Git branch allows you to create a different copy of your source code. In your new branch you can make changes as you please. Your change is independent on what is in the main copy.
Git branch helps you  to develop new features of your application without interfering with the main. It is an important tool for collaboration within remote team. 

- make a new  branch with the command ( git branch  backup) or use the command (git checkout -b "backup")
  the second command will create the branch and then switch to the new branch immediately. then commit.
  

- you can then list the branch using the command (git branch)
- To change to old branch, you can use the command (git checkout main)
  


![image](https://github.com/Gabrielafolabi/DEVOPS-PROJECT/assets/35296784/ed94c402-c916-4c79-a719-9d18d88c15f2)




  
- You can also merge branch into another branch...Say you want to have branches "main" and "backup" , and you want to add content "backup" into  "main".
  Then you first make sure you are in "main" branch and then run the command (git merge backup).

  ![image](https://github.com/Gabrielafolabi/DEVOPS-PROJECT/assets/35296784/41108ba8-9eb5-43af-9459-72082236079f)











- To delete  a branch , use the command **git branch -d backup**

![image](https://github.com/Gabrielafolabi/DEVOPS-PROJECT/assets/35296784/30c8dc86-a1bb-407a-b05d-94b7f776eb4b)



## *Cloning Remote Git Repository*
The Git clone command helps you make a copy of the remote repository on your local machine. It just like downloading remote repository in to your local machine.

use the command git clone  (link  to your local repository)

![image](https://github.com/Gabrielafolabi/DEVOPS-PROJECT/assets/35296784/762d6b79-e57f-4cc1-bdd8-03c53aca2a36)

  






  

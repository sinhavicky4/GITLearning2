# GITLearning2
##Git Version
C:\Users\priya>git --version
git version 2.14.3.windows.1

##Set user name
C:\Users\priya>git config --global user.nama priyanshu


##Set user email
C:\Users\priya>git config --global user.email sinhavicky4@gmail.com

##To check the user
C:\Users\priya>git config user.email
sinhavicky4@gmail.com



#3 Phase of commit
1.Modified---Changes files not committed
2.Stagin--Add any changed file to stating that you want to commit
3.Committed--Any file in stating area are added to the commit when we make one

##All the commit history can be tracked in history tracker



E:\Git>cd GitOne

##Initialized Git for a empty project folder
E:\Git\GitOne>git init
Initialized empty Git repository in E:/Git/GitOne/.git/

E:\Git\GitOne>cd ..

E:\Git>cd GitTwo

##Initialized Git for non empty project folder
E:\Git\GitTwo>git init
Initialized empty Git repository in E:/Git/GitTwo/.git/



##Checking the files in stating area ,no files in staged are shown in red
E:\Git\GitOne>git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        index.html

nothing added to commit but untracked files present (use "git add" to track)

##Adding file to stating area
E:\Git\GitOne>git add index.html

##Again if you check the status of stagin area ,It show staged files in green

E:\Git\GitOne>git add index.html

E:\Git\GitOne>git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   index.html

##To remove the file from stagin area	,after that you can checck the status
E:\Git\GitOne>git rm --cached index.html
rm 'index.html'


##To add multiple files to stagin area
E:\Git\GitOne>git add .

E:\Git\GitOne>git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   index.html
        new file:   style.css




##Commit files in stating area to GIT
E:\Git\GitOne>git commit -m "added index and style files"
[master (root-commit) 1ef2485] added index and style files
 2 files changed, 13 insertions(+)
 create mode 100644 index.html
 create mode 100644 style.css


 ##History of Git commit
 E:\Git\GitOne>git log
commit 423940e5668286e54afd99467e3a7cc6962ce49f (HEAD -> master)
Author: Priyanshu Singh <sinhavicky4@gmail.com>
Date:   Wed Apr 18 16:07:10 2018 +0530

    change body font size

commit 368a109ff91c5f62635b79c3b38ebafa4610bc3b
Author: Priyanshu Singh <sinhavicky4@gmail.com>
Date:   Wed Apr 18 16:05:39 2018 +0530

    added index title

commit 1ef2485c0a7d7cbbac015eda20d01831f30f56cf
Author: Priyanshu Singh <sinhavicky4@gmail.com>
Date:   Wed Apr 18 16:03:35 2018 +0530

    added index and style files


##Git history in one line

E:\Git\GitOne>git log --oneline
423940e (HEAD -> master) change body font size
368a109 added index title
1ef2485 added index and style files

##UnDoing the commit in GIT
1.Checkout Commit--View the commit point
2.Revert Commit--Revert to last commit and delete the current commit
3.Reset Commit--Delete all the commit after reset point





##Checkout .Checkout using id 368a109 and code reverted to "368a109 added index title " point

E:\Git\GitOne>git log --oneline
25a0335 (HEAD -> master) added color to header in style css
78c7d0d added header to index
423940e change body font size
368a109 added index title
1ef2485 added index and style files

E:\Git\GitOne>git checkout 368a109
Note: checking out '368a109'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at 368a109... added index title

##To Go back to latest change in master
E:\Git\GitOne>git checkout master
Previous HEAD position was 368a109... added index title
Switched to branch 'master



##Revert
E:\Git\GitOne>git log --oneline
672bd46 (HEAD -> master) adding modified files
25a0335 added color to header in style css
78c7d0d added header to index
423940e change body font size
368a109 added index title
1ef2485 added index and style files

E:\Git\GitOne>git revert 423940e
[master 5a8f4f4] Revert "change body font size"
 1 file changed, 1 insertion(+), 2 deletions(-)

 #Afert revert
 E:\Git\GitOne>git log --oneline
5a8f4f4 (HEAD -> master) Revert "change body font size"
672bd46 adding modified files
25a0335 added color to header in style css
78c7d0d added header to index
423940e change body font size
368a109 added index title
1ef2485 added index and style files

##Reset

E:\Git\GitOne>git log --oneline
5a8f4f4 (HEAD -> master) Revert "change body font size"
672bd46 adding modified files
25a0335 added color to header in style css
78c7d0d added header to index
423940e change body font size
368a109 added index title
1ef2485 added index and style files

##After git reset code in editor remain the same and only the commits in git were deleted after the commit id "423940e".It will delete all the commit from history and but not from code editor
E:\Git\GitOne>git reset 423940e
Unstaged changes after reset:
M       style.css

E:\Git\GitOne>git log --oneline
423940e (HEAD -> master) change body font size
368a109 added index title
1ef2485 added index and style files

##If we use --hard in reset ,it will revert the code to that commint in editor also.  i.e It will delete all the commit from history and code editor

E:\Git\GitOne>git reset 423940e --hard
HEAD is now at 423940e change body font size




######################################GIT BRANCHING  #######################################################
If we have some new feature in our project and we want to test it.We create a brach from master git and test it if this went fine we will merger the branch to master branch.
Any commit in brach will not affect master unless you merger.
We can create multiple branch at same time and work accordingly and merge to master after successfull testing



##Create  a branch
E:\Git\GitOne>git branch featur-1

##List all brach
E:\Git\GitOne>git branch -a
  featur-1
* master
##Switch to brach
E:\Git\GitOne>git checkout featur-1
Switched to branch 'featur-1'

##Make the changes in branch and commit (same way we do priviously).This will not affect any code in master branch

##To go back to master branch
E:\Git\GitOne>git checkout master
Switched to branch 'master'


##To delete GIT branch
E:\Git\GitOne>git checkout master
Switched to branch 'master'

E:\Git\GitOne>git branch -d featur-1
error: The branch 'featur-1' is not fully merged.
If you are sure you want to delete it, run 'git branch -D featur-1'.

## -D to delelte the branch in case it was not merge with master
E:\Git\GitOne>git branch -D featur-1
Deleted branch featur-1 (was dfbc7b8).


E:\Git\GitOne>git checkout master
Switched to branch 'master'

E:\Git\GitOne>git branch -d featur-1
error: The branch 'featur-1' is not fully merged.
If you are sure you want to delete it, run 'git branch -D featur-1'.

##Create branch and switch to that branch in same step
E:\Git\GitOne>git checkout -b feature-b
Switched to a new branch 'feature-b'

##List the branches
E:\Git\GitOne>git branch -a
* feature-a
  feature-b
  master


###########################################Mergin a brach#############################################
##Switch to brach where we want to merge.Here we want to merge branch feature-a and feature-b in master branch.

##Switch to master brach
E:\Git\GitOne>git checkout master
Switched to branch 'master'

##Merge feature-a to master
E:\Git\GitOne>git merge feature-a
Updating 423940e..efa5f51
Fast-forward
 feature-a.js | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 feature-a.js


##Merge feature-b to master.Here it made a recursive strategy because feature-b does not have feature-a .
E:\Git\GitOne>git merge feature-b
Merge made by the 'recursive' strategy.
 feature-b.js | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 feature-b.js


 #################################Conflict###############################################################
 ##Someone direcly made changes in master and commit the change then at the time of merging of branch it conflict
 ##To resolve confilt see the below

 #Created new brach feature-c
 E:\Git\GitOne>git checkout -b feature-c
Switched to a new branch 'feature-c'

#Switch to masster
E:\Git\GitOne>git checkout master
Switched to branch 'master'

##Change in master and add to stating
E:\Git\GitOne>git add .

##Commit changes from stagin
E:\Git\GitOne>git commit -m "added margin to body"
[master 8425fe1] added margin to body
 1 file changed, 1 insertion(+)

 ##Switch to branch feature-c
E:\Git\GitOne>git checkout feature-c
Switched to branch 'feature-c'

#Made changes and add to staging
E:\Git\GitOne>git add .

#Commit the changes in branch
E:\Git\GitOne>git commit -m "adding padding to style in brach c"
[feature-c 7b288fd] adding padding to style in brach c
 1 file changed, 1 insertion(+)

 #Switch to master for merge
E:\Git\GitOne>git checkout master
Switched to branch 'master'

##Merge with a conflict situation
E:\Git\GitOne>git merge feature-c
Auto-merging style.css
CONFLICT (content): Merge conflict in style.css
Automatic merge failed; fix conflicts and then commit the result.

#Remove the confilt by chaning the items in master brach and add to stagin
E:\Git\GitOne>git add .

#Commit master ,it will automatically merge feature-c
E:\Git\GitOne>git commit
[master 1f46497] Merge branch 'feature-c'

E:\Git\GitOne>git log -oneline
fatal: unrecognized argument: -oneline


##Checking the log
E:\Git\GitOne>git log --oneline
1f46497 (HEAD -> master) Merge branch 'feature-c'
7b288fd (feature-c) adding padding to style in brach c
8425fe1 added margin to body
b342bae Merge branch 'feature-b'
75b08c1 (feature-b) feature-b added to branch b
efa5f51 (feature-a) adding feature-a to brach
423940e change body font size
368a109 added index title
1ef2485 added index and style files


##################################GITHUB###################################################
Github is a service that let us setup hoasted repository
A central online repository what help multiple user to connect over internet

#Check Status
E:\Git\GitOne>git status
On branch master
nothing to commit, working tree clean

##Pusing code to GITHUB
E:\Git\GitOne>git push https://github.com/sinhavicky4/GitOne.git master
fatal: HttpRequestException encountered.
   An error occurred while sending the request.
Username for 'https://github.com': sinhavicky4@gmail.com
Password for 'https://sinhavicky4@gmail.com@github.com':
Counting objects: 27, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (24/24), done.
Writing objects: 100% (27/27), 2.40 KiB | 164.00 KiB/s, done.
Total 27 (delta 10), reused 0 (delta 0)
remote: Resolving deltas: 100% (10/10), done.
To https://github.com/sinhavicky4/GitOne.git
 * [new branch]      master -> master

 ##Alising GITHUB Repository URL with name origin so that not every time we need to git big url of repository

E:\Git\GitOne>git remote add origin https://github.com/sinhavicky4/GitOne.git

##Pusing code to origin(Alias for  https://github.com/sinhavicky4/GitOne.git)
E:\Git\GitOne>git push origin master
fatal: HttpRequestException encountered.
   An error occurred while sending the request.
Username for 'https://github.com': sinhavicky4@gmail.com
Password for 'https://sinhavicky4@gmail.com@github.com':
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 346 bytes | 346.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/sinhavicky4/GitOne.git
   1f46497..e1e2622  master -> master



################################GIT CLOINNG #################################
E:\Git>git clone https://github.com/sinhavicky4/GITLearning2.git
Cloning into 'GITLearning2'...
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.

##Change DIR

E:\Git>cd GITLearning2

#Made some changes in clone code and checked status
E:\Git\GITLearning2>git status
On branch master
Your branch is up-to-date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        index.html

nothing added to commit but untracked files present (use "git add" to track)
##Added to stagin
E:\Git\GITLearning2>git add .

##Commit
E:\Git\GITLearning2>git commit -m "added index page"
[master 495e287] added index page
 1 file changed, 10 insertions(+)
 create mode 100644 index.html

 #Log
E:\Git\GITLearning2>git log --oneline
495e287 (HEAD -> master) added index page
06b04b8 (origin/master, origin/HEAD) Initial commit

##Checking for alias for remote git
E:\Git\GITLearning2>git remote -v
origin  https://github.com/sinhavicky4/GITLearning2.git (fetch)
origin  https://github.com/sinhavicky4/GITLearning2.git (push)

#Pushing to remote repo.This time we do not need to create alias "origin" as we have clone the project it automatically alias as origin
E:\Git\GITLearning2>git push origin master
fatal: HttpRequestException encountered.
   An error occurred while sending the request.
Username for 'https://github.com': sinhavicky4@gmail.com
Password for 'https://sinhavicky4@gmail.com@github.com':
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 424 bytes | 424.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/sinhavicky4/GITLearning2.git
   06b04b8..495e287  master -> master


##################################Colabration to GITHUB #######################################
##To get the latest copy of master,Usually do it before creating a branch
E:\Git\GITLearning2>git pull origin master
From https://github.com/sinhavicky4/GITLearning2
 * branch            master     -> FETCH_HEAD
Already up-to-date.

#Clone the code,create brach
E:\Git\GITLearning2>git checkout -b index.html
Switched to a new branch 'index.html'

##Change the work in brnch
E:\Git\GITLearning2>git status
On branch index.html
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")




#Add to stagin
E:\Git\GITLearning2>git add .

#Commit to local git
E:\Git\GITLearning2>git commit -m "added in index html"
[index.html 12237f8] added in index html
 1 file changed, 2 insertions(+)


# push branch to remote repo.This will generate a pull request in repos .Which can be review by other member in team and merge with master accordingly
E:\Git\GITLearning2>git push origin index.html
fatal: HttpRequestException encountered.
   An error occurred while sending the request.
Username for 'https://github.com': sinhavicky4@gmail.com
Password for 'https://sinhavicky4@gmail.com@github.com':
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 527 bytes | 527.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/sinhavicky4/GITLearning2.git
   495e287..12237f8  index.html -> index.html

E:\Git\GITLearning2>git checkout master
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.



###########################Contribute to open source0----FORK  #########################


Make a fork from origin repository and it will let origin code in your github repository.
Clone your repository ,made the changes and commit to master banch of your own github
Go to github create a pull up request and the once the owner of the code will approve this and merge the code with
their master your contribution added to opensource.

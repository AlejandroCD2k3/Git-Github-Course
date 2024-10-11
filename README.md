Here are some important documentation about my Git & GitHub course.

############ GIT ############

  1. GIT CONFIGURATION

      a. First we have to config our main user.

         $ git config --global user.name "userName"
         $ git config --global user.email "email@example.com"

         If we want to checkout some user configuration we can use: git config --global --get user.name

       b. Then we have to create a new SSH key to authenticate in our git account.

         First of all we may checkout if there are any SSH key already created.

           $ cd ~/.ssh/

           If the directory exists we can checkout if there are any SSH key inside

             Linux: $ ls -al ~/.ssh

         If there are not any SSH key we can create a new one with

           $ shh key-gen -t ed25519 -C "email@example.com"

           It will ask us to give the folder a name, by default we can use "id_rsa" to name our SSH key. And it will ask us for a passphrase, we can give it one or not.

         Then, we have to activade the SSH manually, in that way, we have to init the ssh agent

             $ Get-Service -Name ssh-agent | Set-Service -StartupType Manual
             $ Start-Service ssh-agent
             $ ssh-add c:/Users/USER/.ssh/id_rsa

         Once we completed all this steps, we can now connect our GitHub account with our SSH key, go to GITHUB configuration to continue with this config.

############ GIT HUB ############

1. GITHUB CONFIGURATION

    a. Connecting SSH key

       To connect our SSH key previously created, whe may go to our github account, after that we go to:

         -> User settings
         -> SSH and GPG keys

       And then we click on "create a new SSH key"

         After that, we give it a name and in the "key" text box we add our key previously created pub content

           This key should be in the directory where we created our ssh in the git configuration, and it's probably named "id_rsa.pub", so we open it with some plain text app and copy the content.

############ MAIN GIT COMMANDS ############

1. GIT CONFIG

   It allow us to access to git configuration

       $ git config --global user.name "User"
  
3. GIT INIT

   This command let us initiate a new version control system in a specific directory

       $ git init
       -------------
       $ git config --global init.defaultBranch "branchName" (Change main branch's name)
       $ git branch -m "branchName" (Also change main branch's name)

4. GIT STATUS

    It allow us to see the project status, like which archives has been modified, which ones are untracked (Archives that git isn't taking into account) or archives in stage area

        $ git status

5. GIT ADD

     This command let us add archives to the stage (The stage is the place where git stores the archives he's taking into account to make a commit)

       $ git add . (This add's every untracked archive -Unless it's in the git.ignore document-)

7. GIT COMMIT

     Committing is a "snapchot" of the stage, this snapchot is the one which is going to be updated to our repository.

       $ git commit -m "Commit message" (Commit message allow us to distinguish what we do in every update of our repository)

9. GIT LOG

     Git log lets us to check out the commits that have been made

       $ git log

       $ git log --graph --pretty=oneline --decorate --all --oneline (It can be editted to look better)

     Git reflog show us a more complete history

       $ git reflog

11. GIT CHECKOUT

    This let us to restore our files in our working directory by "visiting" concrete commits.

        $ git checkout "hashCommit"

12. GIT RESET

    Reseting let us to undo changes made in our repository, there are 3 kind of resets.
    
    First of all is the soft reset, it moves the HEAD pointer to a previous commit but keeps all the changes in the staging area and the working directory. It's useful if we want to undo a commit but keep our changes for furhter modifications.

        $ git reset --soft HEAD~1
   
    The second one is the mixed reset, this one just as the one before moves the pointer to a previous commit and keep the changes on the working directory, but unstages the changes.

        $ git reset HEAD~1

    The last one is the hard reset, this one is a real reset, this one ustages the changes, moves the branch pointer but this doesn't save the working directory. (This one deletes everithing)

        $ git reset --hard HEAD~1

13. GIT ALIAS

    Alias allow us to save commands as variables

        $ git config --global alias.variableName "concreteCommand"

14. GIT IGNORE

    Git ignore isn't a specific command, but this document let us specify which documents we don't want to make a commit when whe add archives to the stage. To make a new command we use

    Linux:

        $ touch .gitignore

    Windows:

        $ type nav > .gitignore

    Then inside the document we describe the archives we want to ignore like this:

        $ **/archiveName

15. GIT DIFF

    This allow us to verify the changes done in our work

        $ git diff

16. GIT TAG

    Adding tags let us to have more understandable references to the commits

        $ git tag "tagName"
        ----------------------
        $ git checkout "tagName" (Move to a specific commit by it's tag)

17. GIT REVERT

    This one command deletes a specific commit

        $ git revert "commitHash"
        $ git revert "commitTag"

18. GIT BRANCH

    Branch let us create a new branch (a paralel workflow) that can be integrated later to the main branch

         $ git branch "branchName"

    Also we can delete branches

        $ git branch -d "branchName"

20. GIT SWITCH

    This command let us move between branches

        $ git switch "branchName"

21. GIT MERGE

    Merging let us to combine changes between branches (It brings the changes to te branche where we're standing) once every conflict have been solved

        $ git merge "originBranch"

22. GIT STACH

    A stash is a temporary "chest" where we can put some code without the need of committing it, it can be useful if we want to change to another branch, but we dont have to loose the code we're making. It's like a "Hold it for a second, i'll be right back"

        $ git stash (Add the current progress to the stash)
        $ git stash list (This one allows us to see what's in the stash)
        $ git stash pop (This one let us take back the archives we have in the stash)
        $ git stash drop (This let us discard the content of the stash)


    
         
     


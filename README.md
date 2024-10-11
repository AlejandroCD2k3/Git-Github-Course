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

   

         
     


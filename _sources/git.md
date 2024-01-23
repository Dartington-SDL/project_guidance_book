
# Using Git and GitHub: Setup and basic commands for MacOS

## Git install and GitHub registration

### Check if git is installed on your computer

1.	Open a terminal and enter: `git version`
2.	If Git is present move on
3.	Otherwise go to git developer site and download latest stable version of git for Mac OS

### Setup a git repository folder

Setup a ‘git’ folder on your computer. This is where you will store all git repositories (repos). I have set mine up on my personal DSDL OneDrive. This way my repositories are always backed-up.

### Setup a GitHub account

Go to <https://github.com> and register for a free account

We have a central organisation space on GitHub for all DSDL projects <https://github.com/Dartington-SDL>

Once you have setup your own personal GitHub account, message one of your project collaborators for an invitation to join the Dartington-SDL space or the Senior Data Specialist (currently Sean Manzi).

## Linking your computer to your GitHub account using SSH

Now you need to generate an SSH key and add this to your GitHub account. SSH keys are encrypted passkeys that allow secure file transfers and access through the terminal without the need to constantly enter passwords.

### Generate an SSH key pair

1.	Open a terminal
2.	Paste or type the following into the terminal entering the email that you have registered your GitHub account with
`ssh-keygen -t ed25519 -C "your_email@example.com"`
3.	When prompted to enter a file into which to save the key simply press enter to accept the default location
4.	You will then be prompted to enter a passphrase (optional) for this key. Either enter a passphrase or press enter to not create one.

### Add the SSH private key to your local SSH-agent

1.	Start the SSH agent in the terminal  
`eval "$(ssh-agent -s)"`
2.	If you're using macOS Sierra 10.12.2 or later, you will need to modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain.
3.	First, check to see if your ~/.ssh/config file exists in the default location.
4.	open ~/.ssh/config
5.	If the file doesn't exist, create the file.  
`touch ~/.ssh/config`
6.	Open your ~/.ssh/config file, then modify the file to contain the following lines. If your SSH key file has a different name or path than the example code, modify the filename or path to match your current setup.
7.	`Host github.com`  
        `AddKeysToAgent yes`  
        `UseKeychain yes`  
        `IdentityFile ~/.ssh/id_ed25519`

8.	Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file.
9.	`ssh-add --apple-use-keychain ~/.ssh/id_ed25519`
10.	The `--apple-use-keychain` option stores the passphrase in your keychain for you when you add an SSH key to the ssh-agent. If you chose not to add a passphrase to your key, run the command without the `--apple-use-keychain` option.

### Adding the public key to your GitHub account

1.	Copy the SSH public key to your clipboard.  
`pbcopy < ~/.ssh/id_ed25519.pub`
2.	Go to <https://github.com> and sign in to your account
3.	In the upper-right corner of any page, click your profile photo, then click Settings.
4.	In the "Access" section of the sidebar, click SSH and GPG keys.
5.	Click New SSH key or Add SSH key.
6.	In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal laptop, you might call this key "Personal laptop".
7.	Select the type of key, either authentication or signing.
8.	In the "Key" field, paste your public key.
9.	Click Add SSH key.

### Test your SSH connection

1.	Open a Terminal
2.	Enter the following:  
`ssh -T git@github.com`
3.	You may see a warning like this:  
`> The authenticity of host 'github.com (IP ADDRESS)' can't be established.`  
`> ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.`  
`> Are you sure you want to continue connecting (yes/no)?`  
4.	Verify that the fingerprint in the message you see matches GitHub's public key fingerprint. If it does, then type yes:  
`> Hi USERNAME! You've successfully authenticated, but GitHub does not`  
`> provide shell access.`  
5.	Verify that the resulting message contains your username

## Working with repositories - The basics

### Creating a new repository

At the beginning of a new project, the first thing you will want to do is setup a new repository. The easiest way to create a new repository is through the GitHub website.

1. Go to <https://github.com/Dartington-SDL> and click on repositories
2. Click on the green 'New repository' button
3. Enter a repository name. This should reflect the project that you are working on
4. It is recommended to provide a brief description. This will likely comprise of the full name of the project you are working on and the type of project you are undertaking
5. You next need to decide whether your repository will be public or private. As a general rule the repository should always be public. A respository should only be made prviate if:
    - This has been requested by the client
    - There is an NDA in place for the project
    - The LabREC Ethics board has requested that the repository be made private for ethical or data governance reasons
6. Check the 'Add README file' box. All projects should have a README file, the suggested contents of the README file are discussed in more detail below
7. Select a licence type from the dropdown list. More information on choosing a licence type is given in the 'Choosing a licence' section below
8. Click the green 'Create repository' button

#### Choosing a licence

Many different licences exist for open source projects. It is important to choose a licence as this prevents anyone from claiming your work as their own.

In most instances you will be using either the MIT or GNU licence types. For more information about licence types visit <https://choosealicense.com/licenses/>. The appropriate licence type for you project can be discussed with the Senior Data Specialist (Sean Manzi) and the Operations Director (Laurence Evans).

#### Creating a README file

The README file is a markdown file that is displayed on GitHub at the top level of your repository. This file is most effectively used to provide an overview of the reason for the repository, it's contents and it's use. A suggested structure for the README file is:
- Brief project overview
- Structure of the repository
- Instructions on how to use the contents of the repository

### Cloning an existing repository

1.	In the terminal navigate to your git folder. The command to change directory is cd for example I use:  
`cd ~/’OneDrive – Warren House Group’/DSDL/git`
2.	Note that the file path starts with ~ (tilde) which indicates to the computer that you want to start at the top level of the users file structure.
3.	Also not that any folder or file names that have spaces in are enclosed in an apostrophe. Best practice is to always use an _ (underscore) rather than a space in any folder or file name to negate this issue
4.	You can also navigate in Finder to the location of your git folder, right click and select ‘New terminal at folder’. This will open a new terminal with this folder already selected.
5.	Go to GitHub and go to the repository you would like to clone
6.	Click on the green ‘Code’ button and select SSH
7.	Copy the url
8.	Return to your terminal and enter the following:  
`git clone ‘paste url’`  
`e.g. git clone git@github.com:hsma-programme/2b_principles_of_foss_and_version_control.git`
9.	You will now find a folder labelled with the repository name in your git folder which contains the repository files and folders

### Create a new branch and switch to working on it

1.	Before beginning work on a new feature you want to create an new branch and then switch to working on that branch
2.	You can work on the main branch but this becomes confusing when working on a collaborative project. This should only be done when working on solo projects where you are the only contributor
3.	In the terminal navigate to the repository folder where you want to create a new branch  
`cd ~/’OneDrive – Warren House Group’/DSDL/git/’repository_name’`
4.	Check existing local branch names  
`git branch`
5.	Create a new branch  
`git branch new_branch_name`
6.	Switch to working on that branch  
`git checkout branch_name`
7.	Any changes that you make to files or folders in the repository will be assigned to the branch
8.	When you commit changes from the branch they can be checked by the repository/project admin before being merged with the main project

### Committing changes to the main GitHub repo

When you have finished the current task assigned to you and want to upload your changes to the main project you commit your changes to the repository for review
1.	In the terminal navigate to the repository folder with the changes you want to commit  
`cd ~/’OneDrive – Warren House Group’/DSDL/git/’repository_name’`
2.	Ensure that the branch you want to commit is currently active  
`git status`
3.	Add the current branch and its changes ready to be committed
    1.	To add all changes  
        `git add *`
    2.	To add changes from specific files  
        `git add filenames`
4.	Check that the correct files have been added ready for upload  
`git status`
5.	Commit these changes and add a message describing the changes that have been made/the task completed  
`git commit -m "add your commit message here"`
6.	Push these changes to GitHub  
`git push -u origin branch_name`

### Create a pull request

Once you have committed your changes to the main repository you need to create a pull request. The pull request will notify the repository administrator that there are changes ready to be reviewed for approval and merging with the main branch
1.	Go to the main repository page on <https://github.com>
2.	Click on the ‘Pull requests’ tab
3.	Click on the green ‘New pull request’
4.	Select the ‘base’ branch that you want to merge your changes with
5.	Select the ‘compare’ branch which is the branch with the changes you want to be reviewed
6.	Give your pull request a title and description
7.	After initializing a pull request, you'll see a review page that shows a high-level overview of the changes between your branch (the compare branch) and the repository's base branch. You can add a summary of the proposed changes, review the changes made by commits, add labels, milestones, and assignees, and @mention individual contributors or teams.

### Update your local repo with changes from the remote repo

To update your local version of the repository with the latest version of the main branch you need to pull these changes.
1.	In the terminal navigate to your git folder that you want to update  
`cd ~/’OneDrive – Warren House Group’/DSDL/git/'repository_name'`
2.	Fetch the changes from the main branch of the remote repository and merge them with your local repo  
`git pull origin main`

## Resources


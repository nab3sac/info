# List of git commands frequently used

## Install git
   $ sudo apt install git-all



## (init) - Start a local git repository a .git file structure created
   $ git init
   $
     // Will create a new repository in the current working directory
     // Creates a .git directory - all files used to track changes
     // Creates an initial master branch
     // Creates a default HEAD that points to this master branch

## (add) - Add the files in local Directory to index (Staged)
   $ git add .

## (reset) - Unstage - remove from index after add before commit
   $ git reset HEAD <file1>

## (rm ) - Remove Files from stage as you don't want to commit the Added files
   $ git rm           // Removes from index
   $ git rm -f        // Removes from working Directory - f (force)
   $ git rm --cached  // Remove from working directory, keeping history . 

## (commit) - Commit from staging area to the index to for commit to local repo
   $ git commit -m "Initial Commit"
   $
     // Stages changes since last commit all modified, added and deleted files
     // Creates a commit object - that creates a pointer to the snapshot 
     //   of your changes, as well as the metadata about commit, 
     //   viz author, date, commit message.  
     // Git update the branch pointer to point to the latest commit object, 
     //   which effectively makes it the latest commit on the branch.
     // Changes are saved permanently in the Git repository. 

## -----------------------You have a git repository with tracked files and
   -----------------------  initial commit

## (status) - Check what needs adding committing or pushing (to remote)
   $ git status   // -s short version
                  // (M - Modified, A - added to staged, MM - Staged 7 modified)
                   
## (log) - View history of commits 
   $ git log --graph --decorate --abbrev -- commit --all-pretty --oneline
     // --oneline: This option displays each commit on a single line, 
     //     making it easier to read. The output includes the commit hash and the commit message.

     //  --graph: This option displays the commit history as a graph, 
     //     showing the relationships between commits.

     //  --author: This option filters the output to show only the 
     //     commits made by the specified author. You can use 
     //     a full or partial name or email address.

     //  --since and --until: These options filter the output to show 
            only the commits made between the specified dates. 
            You can use a wide range of date formats.

     //  --grep: This option filters the output to show only the commits 
            that contain the specified text in the commit message.

     //  -n: This option limits the number of commits to display. For example, 
             -n 5 will display the 5 most recent commits.

     //   These are just a few of the many options available for the 
     //     git log command. You can see a full list of options and their 
     //     descriptions by running git log --help. 

## (push) 
   $ git push origin main git@github.com:nab3sac/info.git

## (checkout) - Revert to previous version/ Move branch
   $ git checkout
   $
     // Used to switch between branches, or check out a specific commit
     // If you have changes not committed, those will be lost by the contents
     //  of the branch or commit you are checking out        

  
## (revert) - Revert to previous checkout
   $ git revert
   $
     // Creates a new commit in the history that shows the undoing the changes
     //  Previous commit.
     // This enables you to undo changes made to the previous commit, yet show
     //   the reverted changes in repository's history.

## (clone) - cloning in root directoy
   $ git clone -b branch-name --single-branch git@github.com:nab3sac/rep.git
       subdirectory-name

## (merge) - Merge the contents of clone to existing directory
   $ cd subdirectory-name
   $ git remote add existing-repo /path/to/existing/repo
   $ git fetch existing-repo
   $ git merge existing-repo/master<or-branch-name> //resolve any conflicts
   $ git commit -m "Merged changes from existing repository"
       // That's it. Your existing repository and cloned repository is merged 
       //   into a single repository in the subdirectory.

## (branch) - Create a branch
   $ git branch -a                          // List all branches, local & remote
   $ git branch <branchname>                // New branch
   $ git branch [-d | -D] ,branchname>      // Delete branch -D Force
   $ git branch -m <newnamedbranch>         // Rename current branch
   $ git branch -r                          // List all remote branches
   $ git branch -v                          // Verbose - commit msg, commit date
   $ git branch -u  [--set-upstream-to <upstream> 
   $ git branch -u  --set-upstream-to=origin/feature-branch 
      // will set the usptream br of the current branch to "origin/my-newbranch"
   $ git branch --unset-upstream            // Remove configuration


# ADVANCED
  
## SEARCH & REPLACE
   $ git grep -l | xargs sed -i "" "/s/ugly/funny-lookin/g"
        // -l Supress out put except for file names


# ADMINISTRATION and ERRORS

## (config)
    $ git config [--global] //Uses ~/.gitconfig ; for prj omit global .gitconfig
    $ git config --global user.name "John Doe"  // user.email "jd@example.com"
    $ git config --list

## ERROR: On branch main , Your branch is ahead by 2 commits, use git push
   CORRECTION: Local branch 'main' has commitment that needs to be pushed to 
               origin (Remote brach name)
   $ git push origin main git@github.com:nab3sac/info.git

## ERROR: src refspec git@github.com does not match any. 
          failed to push some refs to https://github.com/nab3sac/info.git
   CORRECTION: Does the branch exit on the remote repository?
               $ git status     // To see if all commited
               $ git remote -v  // to check the name and URL of remote rep
               $ git branch -a  // List all branches, to check if they exist
               $ git push --set-upstream origin your-branch-name //Create branch
               $ git pull      // Fetch any changes from remote and merge
                               //   w/local changes
                               // If none of the steps work then try cloning and
                               //   start again.
## (help)(man) - HELP files
    $ git help <verb>   // git help add
    $ git <verb> --help
    $ man git
          // Libera irc server  #git #github # gitlab

##  THEORY
    UNTRACKED    UNMODIFIED     MODIFIED        STAGED/INDEX
      add -------------------------------------------->
                     vim ----------->
      rm  <-----------
                                     commit ---------->
    Checkout    - from .git directory to Working directory (What's in index)
    Add         - Stage edits - Working Dir to Staging Area
    Commit      - Staging area to .git Directory

## gitignore list of regex files to ignore    

## Webpage URL
  https://nab3sac.github.io/rep-name

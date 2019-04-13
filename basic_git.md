## Setting Up

### 1. Navigate to where you want to put your local repository
`cd your_file_location`

### 2. Clone the repository
(this will create the directory inside of the directory you navigated to in step #1)
`git clone the_link_from_GitHub`

### 3.  Start the flow below!  :)


## Git Flow & Git Basics

When starting a new feature:
### 1.  Start from the `master` branch
`git branch` -> lists all branches you're tracking locally, with an asterisk by the branch you're on
`git checkout master` -> switches to `master` branch

### 2.  Pull in the latest merged changes from the remote tracking branch on GitHub
`git pull origin master` -> pulls all commits from remote `master` branch into the branch you are currently on
(in this case, into `master` branch)

### 3.  From the `master` branch, checkout a new feature branch and do your work locally in it
`git checkout -b your_feature_branch_name` -> creates new branch from current branch (with commits from current branch)
Also:
`git checkout other_branch_name` -> switches from your current branch to another branch
`git branch` -> shows you which branch you're currently working in

### 4.  Check your changes; determine out what you want to include in the commit
`git status` -> will show all files changed
`git diff` -> will show specific lines changed

### 5.  Add and commit your changes within your development/feature branch
`git add specific_files` or `git add .` (for all files) -> select files to include
`git commit -m 'your_message_in_here'` -> to include a helpful message with your commit
(if you make a mistake, you can `git reset HEAD~` to revert)

### 6.  Push changes from your local development branch up to share with others/for review to merge in
`git push origin your_feature_branch_name` -> pushes whatever changes you've saved locally in this branch to your remote tracking branch on GitHub with the same name

### 7.  Submit Pull Requests for other people to review; if approved, merge into `master` branch via GitHub site


## Handling Potential Merge Conflicts
If there are merge conflicts, GitHub will not let you merge via the site before handling them.  Hopefully this will not happen.  If it does:
* `git pull origin master` (pulls in the latest changes from master)
* `git status` -> will show any merge conflicts (specifically, the files that'll need to be resolved)
* Open the files in your selected text editor (MonoDevelop/Sublime/etc.) to intelligibly determine which changes to keep and what lines to remove.

Then, add/commit/push your new commits:
* `git add .`
* `git commit -m "your commit message"`
* `git push origin target_branch`


## Miscellaneous Commands (that you probably don't need but may be useful)

### Deleting an old local branch
`git branch -D your_branch_name` -> to delete old branches no longer in use (this isn't really necessary)

### Rebasing
`git rebase -i HEAD~` -> an example of this command... rebasing can be used to clean up your git commit history, squash multiple commits together, skip select commits, reword your commit message, etc.

### Stashing (and Applying) Changes
This is useful for many things!  Oftentimes I use this for temporarily saving my changes, merging in new changes that other people have made, then applying my changes atop those merged in changes.  There are more complex and powerful use cases than this though!
`git stash` -> temporarily saves your changes and reverts your working directory to match the HEAD commit
`git stash apply` -> re-applies those changes

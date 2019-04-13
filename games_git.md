## Setting Up

### 1. Navigate to where you want to put your local repository
`cd your_file_location`

### 2. Clone the repository
(this will create the directory inside of the directory you navigated to in step #1)
`git clone [the link from GH]`

### 3.  Start the flow below!  :)


## Git Flow & Git Basics

When starting a new feature:
### 1.  Start from the `master` branch
`git branch` -> lists all branches you're tracking locally, with an asterisk by the branch you're on
`git checkout master` -> switches to `master` branch

### 2.  Pull in the latest merged changes from the remote tracking branch on GitHub
`git pull origin master` -> pulls all commits from remote `master` branch into the branch you are currently on
(in this case, into `master` branch)

### 3.  From the `master` branch, checkout a new feature branch
`git checkout -b your_feature_branch_name` -> creates new branch from current branch (with commits from current branch)
Also:
`git checkout other_branch_name` -> switches from your current branch to another branch

### 4.  Do your work in Unity in a Test Scene/Using Prefabs
If you open the directory you're in from "On Disk", it _should_ just be using the contents of the branch you're on.
If you're not sure what branch you are working on, check with `git branch`.

If you are working on a bigger change that is not solely to styling:
*  Create a new test scene with all the objects copied over from the main scene.
*  After handling any errors in that test scene, you might want to place any new objects from that test scene into a prefab.

If you are working on a minor style change:
*  Feel free to make the changes directly in the main scene, add, commit, and push up changes.
*  Then open the PR and just merge it in (no review needed unless you anticipate a conflict).

### 5.  Check your changes; determine out what you want to include in the commit
`git status` -> will show all files changed
`git diff` -> will show specific lines changed

### 5.  Add and commit your changes within your development/feature branch
`git add specific_files` or `git add .` (for all files) -> select files to include
`git commit -m 'your_message_in_here'` -> to include a helpful message with your commit
(if you make a mistake, you can `git reset HEAD~`)

### 6.  Push changes from your local development branch up to share with others/for review to merge in
`git push origin your_feature_branch_name` -> pushes whatever changes you've saved locally in this branch to your remote tracking branch on GitHub with the same name

### 7.  Submit Pull Requests for other people to review, merge into `master` branch via GitHub site

### 8.  After Test Scene and/or Prefabs are merged into master
Integrate the test scene/prefabs that are working into the main scene on master, and push up.
* Follow the flow above to do this in a separate commit/PR, directly into the main scene.


## Reviewing Code and Handling Potential Merge Conflicts

### 1.  Retrieve all remote branches
`git fetch` -> will retrieve all remote tracking branches from GitHub

### 2.  Switch to target branch to review
`git checkout someone_elses_branch` -> checkout someone else's branch from GitHub that now has been fetched

### 3.  Check out the new features/issues in Unity!
This should've auto-updated to the contents on the branch you've checked out.

### 4.  Comment on the PR if there was one, or on Slack if there was not a PR opened yet

### 5.  (Optional) Make, commit, and push changes to `someone_elses_branch`
`git push origin someone_elses_branch`

### 6.  If there are merge conflicts, GitHub will not let you merge via the site before handling them.
Hopefully this will not happen (if we use test scenes/prefabs mostly)... if it _does_ happen:
* (while on `someone_elses_branch`) -> `git pull origin master` (pulls in the latest changes from master)
* `git status` -> will show any merge conflicts (specifically, the files that'll need to be resolved)
* Open the files in your selected text editor (MonoDevelop/Sublime/etc.) or open Unity to intelligibly
determine which changes to keep and what lines to remove.

Then, just add/commit/push your new commits and notify the PR author:
* `git add .`
* `git commit -m "your commit message"`
* `git push origin someone_elses_branch`


## Miscellaneous Commands (that you probably don't need but may be useful)

### Deleting an old local branch
`git branch -D your_branch_name` -> to delete old branches no longer in use (this isn't really necessary)

### Rebasing
`git rebase -i HEAD~` -> an example of this command... rebasing can be used to clean up your git commit history, squash multiple commits together, skip select commits, reword your commit message, etc.

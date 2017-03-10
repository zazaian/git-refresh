# Overview
I wrote this script because I go through this same procedure all the time when
using git, and it was bugging the hell out of me.

The point of this script is to refresh local branches from a remote repository
in order to create a jumping-off point for new branches.

In particular this is useful for checking out a new branch off of a fresh
`master`. This helps to avoid rebase conflicts later down the road when code
needs to be merged back into master.

# What it does
Here's the procedure used for refreshing the local branch:
* Check if the given remote name exists. If not, exit.
* Check if the given branch name exists in the local repo. If not, exit.
* Check if the given branch name exists in the remote repo. If not, exit.
* If you're starting on the branch that you want to refresh, create a temp
  branch with a unique UUID to use while manipulating your target branch.
* Delete the local instance of the given branch.
* Fetch the given branch from the given remote repo.
* Checkout the newly-fetched branch on the local machine.
* Delete the temp branch if you created one.

# Installation
Copy the BASH script into `/usr/local/bin` or any other directories that are
included in the executable path on your machine.

Be sure to set the file as executable as well: `sudo chmod +x git-refresh`.

# Usage
Usage is pretty simple. Here's the format:

`git-refresh remote_name branch_name`

So if I want to refresh my `waffles-are-great` branch on remote `origin`, then
I could just do this:

`git-refresh origin waffles-are-great`

The script will do the rest.

# Support
This script has only been tested in a BASH environment on Ubuntu 16.04 LTS
desktop edition. It should be fairly portable to other BASH, zsh, and other
shell environments by changing the first line from `#!/bin/bash` to whatever
the path of your shell executable happens to be.

# License
This script is owned by Michael Zazaian of Zopio LC and is published under
version 3 of the GNU Affero General Public License.

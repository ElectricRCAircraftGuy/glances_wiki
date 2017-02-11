Glances development factory uses the 'git flow' workflow: http://danielkummer.github.io/git-flow-cheatsheet/

## Clone the Glances repository

First of all, you have to clone the Glances repository to your computer:

`git clone git@github.com:USERNAME/glances.git`

Note: replace USERNAME by your Github login name.

Add the main repository as upstream

`git remote add upstream git@github.com:nicolargo/glances.git`

## Clone the Glances repository

Update your repository with the upstream:

`git fetch upstream`

## Add a new feature ?

Alls news features should be made from the _DEVELOP_ branch.

`git checkout develop`

Create the feature branch:

`git checkout -b NEWFEATURE`

Note: replace NEWFEATURE by your feature name

It's time to code...

Commit your branch:

`git commit -a -m "Description"`

Get latest works from others developer:

`git pull origin feature/NEWFEATURE`

Push it:

`git push origin feature/NEWFEATURE`

Send a message (in the relative issue thread), your code will be review by the Glances team. When all is good, use the [pull request function](https://help.github.com/articles/using-pull-requests) in GitHub to propose your new feature.

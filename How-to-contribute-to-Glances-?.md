Glances development factory uses the 'git flow' workflow: http://danielkummer.github.io/git-flow-cheatsheet/

## Clone the Glances repository

First of all, you have to clone the Glances repository to your computer:

`git clone git@github.com:nicolargo/glances.git`

## Add a new feature ?

Alls news features should be made on the _DEVELOP_ branch.

`git checkout develop`

Create the feature branch:

`git flow feature start NEWFEATURE`

`git flow feature publish NEWFEATURE` 

Note: replace NEWFEATURE by your feature name

`git checkout feature/NEWFEATURE`

It's time to code...

Commit your branch:

`git commit -a -m "Description"`

Get latest works from others developer:

`git pull origin feature/NEWFEATURE`


Send a message (in the relative issue thread), your code will be review by the Glances team. When all is good, use the [pull request function](https://help.github.com/articles/using-pull-requests) in GitHub to propose your new feature.

## Correct an issue on the master branch ?

`git checkout master`

Create the feature branch:

`git flow hotfix start NEWFIX`

`git flow hotfix publish NEWFIX` 

Note: replace NEWFIX by your own fix name

`git checkout hotfix/NEWFIX`

It's time to code...

Commit your branch:

`git commit -a -m "Description"`

`git push origin hotfix/NEWFIX`

Your code will be review by the Glances team. Use the [pull request function](https://help.github.com/articles/using-pull-requests) in GitHub to propose your fix.

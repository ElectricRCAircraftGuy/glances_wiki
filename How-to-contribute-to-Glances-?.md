Glances development factory uses the spirit of the the 'git flow' workflow: http://danielkummer.github.io/git-flow-cheatsheet/.

The following branches are available:
* master: this is the master and stable branch, all the continuous integration is based on this branch. *Nothing* should be pulled request on this branch.
* develop: this is the main development branch for Glances 3.x. The pull request for news features should be done on this branch.
* release/glances2: this is the maintenance branch for Glances 2.x. Only hotfix pull request could be done on this branch. 

## Clone the Glances repository

First of all, you have to fork the Glances repository to your computer using the **Fork** button on the upper right side of the Github Web site.

Then clone locally using the following command line: 

`git clone git@github.com:USERNAME/glances.git`

Note: replace USERNAME by your Github login name.

Add the main repository as upstream

`git remote add upstream git@github.com:nicolargo/glances.git`

## Add a new feature ?

Update your repository with the upstream:

`git fetch upstream`

Alls news features should be made from the _DEVELOP_ branch.

`git checkout develop`

Create the feature branch:

`git checkout -b NEWFEATURE`

Note: replace NEWFEATURE by your feature name

It's time to code...

Your code should be PEP compliant. Here are my Atom's packages:

* autocomplete-python
* linter-pycodestyle
* linter-pydocstyle
* linter-python-pep8
* python-indent
* python-tools

Commit your branch:

`git commit -a -m "Description"`

Get latest works from others developer:

`git pull origin feature/NEWFEATURE`

Push it:

`git push -u origin feature/NEWFEATURE`

Send a message (in the relative issue thread), your code will be review by the Glances team. When all is good, use the [pull request function](https://help.github.com/articles/using-pull-requests) in GitHub to propose your new feature.

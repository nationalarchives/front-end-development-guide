# Version control

## We use Git

All developers should version control their development work. We use the [Git version control system (VCS)](https://git-scm.com/) at The National Archives. While we do allow individual teams some latitude in selecting a branching strategy that is most suitable for the specific product (examples are provided below), developers across teams are expected to:

* use **feature branches** for all their work, and
* use **[pull requests](https://www.youtube.com/watch?v=d5wpJ5VimSU)** as the mechanism by which all branches are merged (so that all code has been reviewed and is understood by more than one developer)

## We use GitHub

We use [GitHub](https://github.com/) as the code hosting service for our code. Developers should ensure all repositories are associated with [The National Archives'](https://github.com/nationalarchives) organisation on GitHub.

### Using pull requests

The process for using pull requests is as follows: 

* A feature branch is made on a local development machine and pushed to GitHub (this might be from `develop` or `master`, depending on the strategy being used by the team)
* A pull request is initiated on GitHub and assigned to one or more other developers
* When the reviewer is satisfied that all standards are met and any work arising from the pull request is finished the pull request is merged on GitHub
* Developers pull the updated branch from GitHub.

Key things to bear in mind are: 

* Merges to are done via a pull request to ensure there has been some review of code before it is merged
* No development should be done outside of a feature branch.

### Selecting a branching strategy

Individual teams should identify and adopt a branching strategy that best meets their needs **while fulfilling the requirements for pull request and feature branches**. Options include: 

* [GitHub flow](https://guides.github.com/introduction/flow/)
* [Trunk based development](https://trunkbaseddevelopment.com/)
* [Git flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

#### Using pull requests with Git Flow 

The process for using pull requests with Git Flow is as follows: 

* A feature branch is made from `develop` on a local development machine and pushed to GitHub
* A pull request is initiated on GitHub and assigned to one or more other developers
* When the reviewer is satisfied that all standards are met and any work arising from the pull request is finished the pull request is merged on GitHub
* Developers pull the `develop` branch from GitHub.

#### Using pull requests with trunk-based development

The process for using pull requests with trunk-based development is as follows:

* A feature branch is made from the trunk branch (which may be named `main`, `master` or similar) and pushed to GitHub
* A pull request is initiated on GitHub and assigned to one more other developers 
* When the reviewer is satisfied that all standards are met and any work arising from the pull request is finished the pull request is merged on GitHub
* Developers pull the trunk branch from Github

### Providing useful commit messages

A considered commit message is the best way to communicate context about a change and is therefore a vital aspect of good collaboration. A particularly useful resource for understanding this is provided in [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/) which outlines the [seven rules](https://chris.beams.io/posts/git-commit/#seven-rules) of a great Git commit message as: 

* Separate subject from body with a blank line
* Limit the subject line to 50 characters
* Capitalize the subject line
* Do not end the subject line with a period
* Use the imperative mood in the subject line
* Wrap the body at 72 characters
* Use the body to explain _what_ and _why_ vs. how

We have also produced a [presentation](/supporting_material/good_commmit_messages.pdf) outlining the purpose and benefits of ensuring good commit message.
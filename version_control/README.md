# Version control

## Git

When working with Git we:
 
* follow the [Git Flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) branching methodology
* undertake code reviews using [pull requests](https://help.github.com/articles/about-pull-requests/) in GitHub to ensure all code has been reviewed before being merged into `develop`. 

### Using pull requests with Git Flow 

The process for using pull requests with Git Flow is as follows: 

* A feature branch is made from `develop` on a local development machine and pushed to GitHub
* A pull request is initiated on GitHub and assigned to one or more other developers
* When the reviewer is satisfied that all standards are met and any work arising from the pull request is finished the pull request is merged on GitHub
* Developers pull the `develop` branch from GitHub.

Key things to bear in mind are: 

* Merges to `develop` are done via a pull request to ensure there has been some review of code before it is merged to `develop`
* No development should be done on the `develop` or `master` branches. Urgent fixes can be managed via the 'Hotfix' process of in [Git flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

### Providing useful commit messages

A considered commit message is the best way to communicate context about a change and is therefore a vital aspect of good collaboration. A particularly useful resource for understanding this is provided in [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/) which outlines the [seven rules](https://chris.beams.io/posts/git-commit/#seven-rules) of a great Git commit message as: 

* Separate subject from body with a blank line
* Limit the subject line to 50 characters
* Capitalize the subject line
* Do not end the subject line with a period
* Use the imperative mood in the subject line
* Wrap the body at 72 characters
* Use the body to explain _what_ and _why_ vs. how
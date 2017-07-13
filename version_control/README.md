### Version control and code reviews

We follow the [Git Flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) branching methodology and routinely undertake code reviews using [pull requests](https://help.github.com/articles/about-pull-requests/) in GitHub to ensure all code has been reviewed before being merged into `develop`. The process is as follows: 

* A feature branch is made from `develop` on a local development machine and pushed to GitHub
* A pull request is made and assigned to one or more other developers
* When work is concluded the pull request is merged on GitHub
* Developers pull the `develop` branch from GitHub.

Key things to bear in mind are: 

* Merges to `develop` are done via a pull request to ensure there has been some review of code before it is merged to `develop`
* No development should be done on the `develop` or `master` branches. Urgent fixes can be managed via the 'Hotfix' process of in [Git flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
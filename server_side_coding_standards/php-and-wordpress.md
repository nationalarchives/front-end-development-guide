# PHP and WordPress guidance

## WordPress

As part of our efforts to ensure clean, readable and consistent code across projects and developers we follow the [WordPress PHP Coding Standards](https://make.wordpress.org/core/handbook/best-practices/coding-standards/php/)

## Testing

* PHP code is tested using PHPUnit. There is a wealth of documentation and guidance on the [PHPUnit website](https://phpunit.de/) including: a [getting started guide](https://phpunit.de/), extensive [library documentation](https://phpunit.de/manual/current/en/index.html) and [presentations and videos](https://phpunit.de/presentations.html) 


### Travis CI

* Travis CI has been integrated into many of The National Archives repositories to run PHPUnit and other tests automatically when a branch is pushed to GitHub. This is very simple to achieve via a `.travis.yml` file in the project root. Travis also has good [documentation](https://docs.travis-ci.com).
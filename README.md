# circleci-orb-bits-puppet

[![CircleCI](https://circleci.com/gh/broadinstitute/circleci-orb-bits-puppet/tree/master.svg?style=svg)](https://circleci.com/gh/broadinstitute/circleci-orb-bits-puppet/tree/master)

An orb containing useful [Puppet][1] commands and jobs for doing CI/CD in [CircleCI][2].

## Commands provided

* **prereq**: Install and cache all dependencies including any unit test fixtures
* **publish**: Publish the module to the [PuppetForge][4]
* **static**: Run all static analysis using `bundle exec rake`.  This includes:
  * check:dot_underscore
  * check:git_ignore
  * check:symlinks
  * check:test_file
  * lint
  * metadata_lint
  * rubocop
  * syntax
* **unit-tests**: Run spec tests using `bundle exec rake`
* **verify-tag**: Verify git tag vs. version specified in the `metadata.json` file for the module

## Executors provided

* **ruby_puppet**: Runs a ruby container with parameters for specifying `ruby_version` and `puppet_version`.  These parameters respectively select the tag of `circleci/ruby` to use (`2.4.6` by default) and the value of the `PUPPET_GEM_VERSION` environment variable (`< 6.0.0` by default) to select Puppet version.

## Jobs provided

* **deploy**: Verify the version and then publish a new version to [PuppetForge][4].
* **run-tests**: Install dependencies and run spec tests
* **static**: Run all static analysis checks

## pre-commit hooks

A configuration is provided for doing pre-commit hook checks using [pre-commit][3].  For all the checks to work you will need to have the following installed already:

* [https://github.com/adrienverge/yamllint](yamllint)
* [CircleCI][2] command-line utility: [https://circleci.com/docs/2.0/local-cli/](circleci)

[1]: https://puppet.com/ "Puppet"
[2]: https://circleci.com/ "CircleCI"
[3]: https://pre-commit.com/ "pre-commit"
[4]: https://forge.puppet.com/ "PuppetForge"

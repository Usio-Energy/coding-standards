# 🐍 Coding Standards

This is not "final". **Pull requests welcome** to evolve it over time.

1. [Documentation](#documentation)
2. [Testing](#testing)
3. [Coding style / Linting](#coding-style--linting)
4. [Exceptions](#exceptions)
5. [Code Organisation](#code-organisation)
6. [Python Packaging](#python-packaging)
7. [Design](#design)
8. [Pull requests](#pull-requests)
9. [Deployment](#deployment)
10. [Configuration](#configuration)
11. [Misc](#misc)

## Documentation

- Each project must have a README.md file.
- README file must provide instructions to: build project, run tests, run project locally.

## Testing

- Tests must be written using py.test (https://docs.pytest.org).
- Coverage levels should be reported in CI builds.
- Tests should be integration tests where possible. Try not to go overboard with Mocking (vague statement, judge case by case).
- ReactJS components must have unit tests.
- If the application has a front-end, user journeys should be covered with selenium (BDD style or other) tests, to ensure they continue to function.
- Unhappy paths and edge case scenarios must be tested for, not just the happy path.

## Coding style / Linting

- Each project must have a [flake8](https://pypi.python.org/pypi/flake8) linter.
- Each project must follow [PEP8](https://www.python.org/dev/peps/pep-0008/) (inc. 79 chars limit).
- Docstrings must follow PEP257 (https://www.python.org/dev/peps/pep-0257/).
- Docstrings must be in [Google style](http://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html), use [pydocstyle](https://github.com/PyCQA/pydocstyle) to validate.
- Functions with more than 1 parameter must [force keyword arguments](https://www.python.org/dev/peps/pep-3102/).
- All class `__init__` methods must [force keyword arguments](https://www.python.org/dev/peps/pep-3102/).
- Follow Python [EAFP principal](http://python.net/~goodger/projects/pycon/2007/idiomatic/handout.html#eafp-vs-lbyl) where possible.
- Use relative absolute imports within projects, full absolute imports in testing code.

  ```python
  # in testing code
  from project.subpackage import magic_beans
  # in project code
  from .sub_package import magic_beans
  ```
- Don't use single letter variable names, unless within a list comprehension.
- Never put any code in the `__init__.py` of a module (except namespace stitching imports).
- Use f-strings (https://www.python.org/dev/peps/pep-0498/) instead of `str.format`.

## Exceptions

- Only define custom exceptions when you have a need to catch it specifically.
- Use [standard libary exceptions](https://docs.python.org/3/library/exceptions.html) where possible.
- Always include a descriptive message when an exception is raised.

## Code Organisation

- Project should have a single top-level Python package.
- Project requirements must be split into `requirements.txt` `requirements-dev.txt` files etc.

## Python Packaging

- Python Packages must follow [Semantic Versioning](http://semver.org/).
- Must contain a HISTORY.rst file.
- Must use [Zest.releaser](https://zestreleaser.readthedocs.io/en/latest/) for releases.

## Deployment

- Project must contain a `Dockerfile` for deployment.
- Project must include an Ansible + AWS Cloudformation configuration for deployment.

## Configuration

- Project configration must come from environment variables, no hardcoded per-environment values in the codebase.
- Deployment Secrets must be stored in ansible-vault.

## Misc

- Use Python version 3.6 or above.

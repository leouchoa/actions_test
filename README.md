# actions_test

Testing [github actions and workflows](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions) and also [pre-commit](https://pre-commit.com/).

About the pre-commit config, the `.pre-commit-config.yaml` config file will run checks to

- format your code using the `black` formatter
- run flake8 tests (commit)
- sort and format imports
- check for docstrings with interrogate

## Pre-commit Setup

To setup the pre-commit checks:

1. Install pre-commit with `pip install pre-commit`
2. Make a copy of `.pre-commit-config.yaml` on your repo
3. Install the config with `pre-commit install`

If your installed ran correctly you should see this output:

```
pre-commit installed at .git/hooks/pre-commit
```

Now everytime you make a commit, pre-commit will scan your python files and run. If you python files are not formatted to make a flake8 score of at least 8, your commit won't be accepted and you'll need to format it corretly and re-commit.

For more information on how I've set up this repo, please refer to [this blog post](https://towardsdatascience.com/4-pre-commit-plugins-to-automate-code-reviewing-and-formatting-in-python-c80c6d2e9f5)

## **Important note**

Suppose you're commiting a file called `asd.py`. In case your commit fails because of some test and you receive the following message

```
Stashed changes conflicted with hook auto-fixes... Rolling back fixes...
```

your code won't be accepted to be commited. If you inspect the results a bit further with `git status` you'll see that a new `asd.py` has the modified status.
In that case please add the file once more and try to commit. Sometimes it takes me up to 3 times to make a commit.

## running  pylint

I've tried following [this blogpost](https://medium.com/analytics-vidhya/pylint-static-code-analysis-github-action-to-fail-below-a-score-threshold-58a124aafaa0) to also run pylint along with flake8 but it's just not worth it.

# GIT conventions

Nolu tries to follow the Gitflow approach. Currently Nolu differentiates 2 main branches:
```
- `master` branch
- `develop` branch
```

## Getting stuff done

When working on issues, always start by pulling checking out the `develop`-branch. Your next step should be to create your own branch. Make sure to put your branch in the correct git folder. We have some different git folders which indicate the issue types:

- `hotfix` - only quickfixes/issues in production (`master`-branch) should be part of this folder
- `bugfix` - fixes issues/bugs that can be part of the next release to `master`
- `feature` - new features/enhancements

When creating a branch make sure you start your branch name with a hashtag (`#`) and the git issue number. A typical branche for a feature could be `feature/#40_new-widget`.

Now what are the steps for creating new branches? These instructions apply to bugfixes and features only, since hotfixes follow a different approach:

1. `git checkout develop` - switches to the develop branch
2. `git pull` - retrieve all new changes from the remote develop branch
3. Now here are some examples for the different issue types:
    - `git checkout -b bugfix/#32_fix-for-button-tooltip`
    - `git checkout -b feature/#34_a-very-nice-feature`

### Finishing up

Before you create a pull request, make sure to merge the develop branch in your branch. Then create your pull request in Github. Make sure you merge your `bugfix` or `feature` in the `develop`-branch!!!

# libdragon integration repository

A repo for integrating changes from the various libdragon forks and submitting them
to Dragonminded's upstream repo.

## Adding a new repository

Add the respository as a remote to your local fork:

    git remote add <url> <name>

Fetch the repository:
    
    git fetch <name>

Check out the main branch (usually `master`):

    git checkout <name>/master

Give the branch a name to be used in this repo (make it descriptive):

    git checkout -b <branchname>

Push the branch to your fork of this repo and submit a pull request:

    git push origin <branchname>

Get a listing of all commits in the fork which are not included upstream. In the simple case, this is as easy as:

    git log --oneline --reverse <branchname> ^upstream

Open a tracking issue on this repository which lays out the commits from the fork and tracks whether a PR has been submitted upstream. See [the conker64 tracking issue](https://github.com/awygle/libdragon/issues/1) for an example of what this looks like.

## Integrating a commit

Check out the `upstream` branch, then create a working branch for your change:

    git checkout upstream
    git pull
    git checkout -b <branchname>

Cherry-pick the commit you wish to integrate into your new branch:

    git cherry-pick <commit>

Resolve any merge conflicts which occur. Test your change (please don't submit untested changes!), then there are two options for next steps.

### Option 1: Submit directly upstream

Submit your change directly to the upstream libdragon repo. This requires a small amount of Git knowledge but is very straightforward.

### Option 2: Submit to `integration` branch

Submit your change to the `integration` branch of this repo, and someone will open a PR for you from there. To do this, push your branch to your fork of this repo on Github:

    git push origin <branchname>

Then open your fork in Github's web interface and press the `Compare & pull request` button which pops up.

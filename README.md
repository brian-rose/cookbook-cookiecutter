# Cookbook Cookiecutter

A [cookiecutter](https://cookiecutter.readthedocs.io) template to create [Cookbooks](https://cookbooks.projectpythia.org) for [ProjectPythia](https://projectpythia.org).

*This is currently very experimental, use at your own risk!*

## Usage

We are going to use a tool called [cruft](https://cruft.github.io/cruft/) to create and update boilerplate code in the new Cookbook.

First install cruft into a local Python environment:
```
mamba install cruft
```

You can create a new Cookbook source directory by running
```
cruft create https://github.com/brian-rose/cookbook-cookiecutter/
```
or, alternatively, run this from the local directory where this `cookbook-cookiecutter` sits:
```
cruft create cookbook-cookiecutter
```

You will be prompted to enter some basic information about your cookbook. Accepting all the default values will essentially regenerate the [Pythia Cookbook Template](https://github.com/ProjectPythia/cookbook-template).

Things you may want to customize:
- Cookbook name
- Cookbook repo name
- environment name
- Author
- github org -- set this to your personal GitHub username if you want to try publishing your Cookbook on your own pages.

Then go ahead and add any notebooks, and make sure to update the `_toc.yml` file appropriately.

Edit the `environment.yml` file to add any necessary packages that your notebooks need.

To publish your new Cookbook on GitHub, there are a few steps:

1. Initialize a new git repo in your new coobook directory and commit all the new files.
2. Create an empty repo on GitHub, push your local repo up
3. Create a branch called `gh-pages` on GitHub
4. Go to "Settings" --> "Pages" and make sure it is set to "Source": "Deploy from a branch" and the branch is set to "gh-pages"
5. Go to "Settings" --> "Actions" --> "General" --> Workflow Permissions, and select "Read and write permissions", and also check the box "Allow GitHub Actions to create and approve pull requests"

Your Cookbook should now build and publish itself to <https://[github org-or-user name].github.io/[cookbook-repo-name]>

## Keeping your Cookbook infrastructure up to date

cruft has some nice automation for keeping your Cookbook files up to date with changes in the Template, or for changing any of the keys you originally selected at creation time.

### Changes in the template

Try this, from the root of your Cookbook repo:
```
git checkout -b update-my-cookbook
cruft update
```
This should suggest some changes to your code in a new git branch called `update-my-cookbook` -- which you can either push up to GitHub with 
```
git push origin update-my-cookbook
```
or merge into your main branch with 
```
git checkout main
git merge update-my-cookbook
```

### Changes to template variables

Suppose you change the title of your Cookbook. You could try this:
```
cruft update --variables-to-update '{ "project_name" : "A New Name!" }'

This should propagate the name change through to several different files in your Cookbook repository.

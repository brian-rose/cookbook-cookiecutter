# Cookbook Cookiecutter

A [cookiecutter](https://cookiecutter.readthedocs.io) template to create [Cookbooks](https://cookbooks.projectpythia.org) for [ProjectPythia](https://projectpythia.org).

*This is currently very experimental, use at your own risk!*

## Usage

First install cookiecutter into a local Python environment:
```
mamba install cookiecutter
```

You can create a new Cookbook source directory by running
```
cookiecutter cookbook-cookiecutter
```
from the directory where this `cookbook-cookiecutter` sits.

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

# Contributing to Readme-Workflow's website

First of all, thank you for considering to contribute towards the Readme-Workflow's website.

To make sure that your contribution follows certain standards did we set up these basic Guidelines that you should read and follow.
If you're unsure about a specific part of the Guidelines, use your best judgement or ask us for clarification.

## Pull request

Before submitting a Pull request should you make sure that there isn't an existing Pull request with the changes you want to provide.

To make a pull request, first fork the Repository, clone it to your PC using git, edit any files nessecary including README and CHANGELOG if those are affected by your changes, commit those changes to your fork and then create the Pull request.

### Pull request States

The Recent Activity Repository follows a simple rule where different Pull request states indicate different actions to do:

- `Draft Pull requests` are not mergable nor reviewable. a Draft indicates that you're still working on it and that the changes are not yet final.
- `Pull request` indicate that they can be reviewed by Maintainers, but can't yet be merged.
- `Pull request with "Status: Ready" label` mark your Pull request as ready to merge. You can inform a Maintainer about your Pull request's state to get this label added to it.

If at any point you need to make changes and don't want to risk getting your Pull request merged before that change, convert it back into a Draft.
A Draft Pull request with the "Status: Ready" label that gets turned into a normal Pull request again will skip the review-phase unless you request a new review from the Maintainers.

### Source branch name

It is recommended to have a descriptive branch-name to inform about the change made needed for context.

Commonly used branch-name patterns are `feature/<feature-name>` for new features and `fix/<bug-fixed>` for bug fixes, but you can use your own style of branch-naming as long as it gives clear information on what it is for.

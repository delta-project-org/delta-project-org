# The Delta Project

This is the Delta Project, aiming to improve software reliability.

The main tool for this is the integration of massive assertion support into the programming language;
assertions can state properties such as
memory and CPU usage limits,
type constraints,
absence of information leakage,
etc.

Theory says that assertion checking can be made almost fully automatic,
only one kind of help needed is loop invariants and their equivalents.  
In practice, people will want to provide more assertions,
e.g. to state the properties of internal APIs.

Building the language is just the first step.
See [the long-term plan](docs/long-term-plan.md).

## Releases

There are currently no official releases;
these will come when non-contributors start taking interest.

## Downloads

To get the code and everything else, either clone the repository, or use the "Download ZIP" button to the right.

Everything is in one repository:
- [sources](src/),
- [build helper tools](build/),
- [documentation](docs/),
- [project organization tools and configuration](org/).

## Reporting issues

Use the "Issues" link on the top right of the GitHub page.

## Contributing

1. Fork the repository on GitHub,
1. clone the repository to your local machine,
1. make a branch,
1. hack on the code,
1. push to your GitHub fork,
1. make a pull request,
1. follow the PR discussion until the PR is merged, superseded, or retracted.

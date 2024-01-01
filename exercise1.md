# Warming up

## The CI/CD setup of a .Net Blazor Wep App
The .Net ecosystem offers many tools that can also be used in the CI setup for our project. The `dotnet` CLI tool offers commands for formatting, testing and building our project. To setup dotnet CLI in our workflow we will use the `setup-dotnet` GitHub Action with our preferred .NET core sdk version.

To keep our code style consistent we can run `dotnet format` in our as a part of our GitHub Actions Workflow, we could pass arguments to the command or preferrably can use a `.editorconfig` file. This file will also serve to enforce developers to conform with our code style during development with the help of their IDEs. For our CSS files we will be using Prettier. We can have a Workflow job with `setup-node` action and steps to install and run Prettier. Configuring Prettier can be done by passing arguments to the command or through a `.prettierrc` file.

For our unit tests we will use NUnit, partially because Playwright recommends NUnit and thereby unifying our test frameworks. We will use a container image of Playwright in our GitHub Actions Workflow to have a consistent test environment. We can run both our unit tests and Playwright tests with the `dotnet test` command.

To build our application we can simply run the `dotnet build` command.

Some alternatives to GitHub Actions:
- Azure DevOps
- GitLab
- Travis CI
- Buildbot

We do not have specific needs such as a GPU for testing, therefore the convenience and the fact that .Net provides ready made templates for build Workflows makes GitHub Actions the easy choice for our project.

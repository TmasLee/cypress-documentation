# Contributing to Cypress Documentation

Thanks for taking the time to contribute! :smile:

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Writing Documentation](#writing-documentation)
  - [Tags](#tags)
  - [Adding Examples](#adding-examples)
  - [Adding Plugins](#adding-plugins)
  - [Writing the Changelog](#writing-the-changelog)
- [Committing Code](#committing-code)
  - [Linting](#linting)
  - [Pull Requests](#pull-requests)
  - [Contributor License Agreement](#contributor-license-agreement)
- [Deployment](#deployment)

## Code of Conduct

All contributors are expected to abide by our [Code of Conduct](https://github.com/cypress-io/cypress/wiki/code-of-conduct).

## Getting Started

The documentation in this repo is generated using [Hexo](https://hexo.io/).

**Fork this repository**

Using GitHub, create a copy (a fork) of this repository under your personal account.

**Clone your forked repository**

```shell
git clone git@github.com:<your username>/cypress-documentation.git
cd cypress-documentation
```

**Install dependencies:**

**Note:** at least Node 6 is required, but Node 8 with NPM v5 is preferred to take advantage of
the package lock file.

```shell
npm install
```

This will install this repo's direct dependencies.

**Then, build the `public` directory and start the app:**

```shell
npm run build
npm start
```

Visit [http://localhost:2222/](http://localhost:2222/).

**Note:** If you need to debug the documentation build step, run it this way: 

```
DEBUG=docs npm run build
```

**Note:** When Cypress generates the docs, it has to validate hundreds (thousands?) of URLs. This is expensive and the docs take a while to initialize. You can turn off validation of external URLs by passing a flag: 

```
npm start -- --no-validate
```

### Testing

We use Cypress itself to test the documentation. To start the server and run E2E tests, execute the command `npm run test-e2e`.

## Writing Documentation

### Tags

In addition to built-in Hexo tags (like `{% img ... %}`), we have written several custom ones. They help us write consistent documentation, check referenced urls, etc. You can find the list of tags and examples in [TAGS.md](TAGS.md).

### Adding Examples

To add a blog, talk or podcast to our docs, submit a [pull request](#Pull-Requests) with your data added to the corresponding [blogs.yml](https://github.com/cypress-io/cypress-documentation/blob/develop/source/_data/blogs.yml), [talks.yml](https://github.com/cypress-io/cypress-documentation/blob/develop/source/_data/talks.yml), or [podcasts.yml](https://github.com/cypress-io/cypress-documentation/blob/develop/source/_data/podcasts.yml) file.

Add an associated image with the example within the [`source/img/examples`](/source/img/examples) directory. Each image should have a resolution of **715×480**. Reference the image in the markdown document as follows:

```md
{% img /img/examples/name-of-file.jpg "alt text describing img" %}
```

### Adding Plugins

To add a plugin, submit a [pull request](#Pull-Requests) with the corresponding data added to the [plugins.yml](https://github.com/cypress-io/cypress-documentation/blob/develop/source/_data/plugins.yml) file. Your plugin should have a name, description, link to the plugins code, as well as any keywords.

### Writing the Changelog

When adding to the Changelog, be sure to follow the category structure defined below (in this order). Each bullet point in the list should *always* be associated to an issue on the [`cypress`](https://github.com/cypress-io/cypress) repo and link to that issue (except for Documentation changes).

#### Categories

- **Summary** - If it is a large release, you may write a summary explaining what the point of this release is (mostly used for breaking releases)
- **Breaking Changes** - The users current implementation of Cypress may break after updating.
- **Features** - A new feature
- **Bugfixes** - A bug existed in Cypress and a PR fixed the issue
- **Misc** - Not a feature or bugfix, but work that was done. May be internal work that was done and associated with an issue
- **Documentation Changes** - our docs were updated based on behavior changes in release

## Commiting Code

### Linting

Danger 📛: because we are minifying client-side code using a [Hexo plugin](https://github.com/mamboer/hexo-filter-cleanup) which in turn calls
`uglify`, the code should be strictly ES5. Thus everything inside the `theme` should be linted with ES5 settings and not upgraded to ES6.

### Pull Requests

You should push your local changes to your forked GitHub repository and then open a pull request from your repo to the `cypress-io/cypress-documentation` repo.

- The pull request should be from your repository to the `develop` branch in `cypress-io/cypress-documentation`
- When opening a PR for a specific issue already open, please use the `address #[issue number]` or `closes #[issue number]` syntax in the pull request description.
- Please check the "Allow edits from maintainers" checkbox when submitting your PR. This will make it easier for the maintainers to make minor adjustments, to help with tests or any other changes we may need.
![Allow edits from maintainers checkbox](https://user-images.githubusercontent.com/1271181/31393427-b3105d44-ada9-11e7-80f2-0dac51e3919e.png)

### Contributor License Agreement

We use a [`cla-assistant.io`](https://cla-assistant.io/) web hook to make sure every contributor assigns the rights of their contribution to Cypress.io. If you want to read the CLA agreement, its text is in this [gist](https://gist.github.com/bahmutov/cf22bc6c6b55219d0f9a76d04981f7ae).

After making a [pull request](#pull-requests), the CLA assistant will add a review comment. Just click on the link and accept the CLA. That's it!

## Deployment

We will try to review and merge pull requests as fast as possible. After merging, we will deploy it to the staging environment, run E2E tests (using Cypress itself of course!), and then merge it into `master`, which will deploy it to the official [https://docs.cypress.io](https://docs.cypress.io) website. If you want to know our deploy process, read [DEPLOY.md](DEPLOY.md).

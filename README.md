# Lerna Monorepos

Spliiting up large codebases into separate independently versioned packages is very useful for code sharing.
However, this quickly becomes complicated as tracking changes accross many repositories becomes messy and difficult to track.

To solve this, projects can organize their codebases into multi-package repos (called monorepos). This way all of their
packages can be developed in a single repo.

Official lerna docs:
https://github.com/lerna/lerna

Nice tutorial on creating a Lerna monorepo:
https://viewsource.io/publishing-and-installing-private-github-packages-using-yarn-and-lerna/

## Commands

To start a lerna project run:
`npx lerna init`

To link deps in a repo together run:
`npx lerna bootstrap`

To publish:
`npx lerna publish`

## Two Modes

### Fixed/Locked mode (default)

Fixed mode lerna projects operate on a single version line. The version is kept in the lerna.json file at the root of your project.
When you run `lerna publish`, if a module has been updated since the last time a release was made, it will be updated to the new versison
you're releasing.

### Independent Mode

`npx lerna init --independent`

Independent mode Lerna projects allows maintainers to increment package versions independently of each other. Each time you publish, you will get a prompt for each package that has changed to specify if it's a patch, minor, major or custom change. You can use this with the semantic-release npm package to make the process more painless.

### The setup

Once you have your repo set up, genereate a personal access token in github:
https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token#creating-a-token

Next, create a `.npmrc` file in the root of your project with the following:

```
//npm.pkg.github.com/:_authToken=ACCESS_TOKEN
@jake-ruth-qm:registry=https://npm.pkg.github.com
```

Where `ACCESS_TOKEN` is your personal access token and `jake-ruth-qm` is your github username

In each of your packages, run npm init in the root to initialize. Then in your package.json add the following fields:

`"name": "@jake-ruth-qm/test-datasource-1"`
This will match your username and package name (jake-ruth-qm username and test-datasource-1 is the package name)

```
 "repository": {
    "type": "git",
    "url": "https://github.com/jake-ruth-qm/lerna-poc.git",
    "directory": "packages/test-datasource-1"
  },
```

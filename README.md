# Learna Monorepos

Spliiting up large codebases into separate independently versioned packages is very useful for code sharing.
However, this quickly becomes complicated as tracking changes accross many repositories becomes messy and difficult to track.

To solve this, projects can organize their codebases into multi-package repos (called monorepos). This way all of their
packages can be developed in a single repo.

Official lerna docs:
https://github.com/lerna/lerna

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

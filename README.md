# Forced Conventional Commits - By Jon D Jones

A project that forces all GIT commits to adhere to the [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/) standard.  It uses [commitlint](https://github.com/conventional-changelog/commitlint) and [husky](https://www.npmjs.com/package/husky)

## Install Instructions 👾☄️👻👺🕹️

This guide will tell you how to install from scratch, manually:

Create a GIT repo:

```
git init
```

Create a new project:

```
npm init
```

Create a `.gitignore`:

```
echo node_modules  > .gitignore
```

Install stuff:

```
npm install @commitlint/cli --save-dev
npm install @commitlint/config-conventional --save-dev
npm install husky --save-dev
```

Add some config in `package.json`:

```bash
"scripts": {
    "prepare": "husky install"
}
```

Create a file called `commitlint.config.js`.  Add this config:

```bash
module.exports = {
    extends: ['@commitlint/config-conventional'],
};
```

Add a husky hook.  Create a file:

```bash
npx add .husky/commit-msg
```

In the new file `.husky/commit-msg, paste the below config:

```bash
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

npx --no-install commitlint --edit "$1"
```

### Test It Out

Make a commit.  Add your files:

```bash
git add .
```

Test a failed commit:

```bash
git commit -m "fail"
```

test a valid commit:

```bash
git commit -m "feat(JIRA-1): hi"
```

Job done!  Happy coding 🤘
# Contributing

First of all, thank you for deciding to contribute to how developers create layouts! Follow these straightforward instructions below to get started with shipping your code to Atomic layout.

## Pre-requisites

Knowledge in the following technologies is highly welcome:

1. [CSS Grid](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout)
2. [React](https://github.com/facebook/react)
3. [styled-components](https://github.com/styled-components/styled-components)
4. [Storybook](https://github.com/storybooks/storybook)

## Getting started

### 0. Prepare

1. Fork [the repository](https://github.com/kettanaito/atomic-layout),
2. Checkout the forked directory,
3. Install dependencies via `npm install`

### 1. Create a feature/bugfix branch

```bash
git checkout -b {ISSUE_NUMBER}-{BRANCH_NAME}
```

### 2. Develop!

#### Run Storybook

```bash
npm start
```

We develop in stories using [Storybook](https://github.com/storybooks/storybook). Create a story for your feature, or a bugfix scenario, and point your browser to `localhost:6020` after running the command above.

#### Run development server

```bash
npm run dev
```

This launches `webpack-dev-server` in watch mode to bundle the library upon any change. Pay attention to the useful messages and warnings in the terminal during the process.

### 3. Commit the changes

```bash
git commit -am 'Introduces ABC'
```

### 4. Rebase the feature branch

```bash
git checkout {TARGET_BRANCH}
git pull --rebase
git checkout {FEATURE_BRANCH}
git rebase {TARGET_BRANCH}
```

> Atomic layout is following rebase merge strategy. **Do not** use `git merge`.

### 5. Create a pull request

1. Go to [https://github.com/kettanaito/atomic-layout/compare](https://github.com/kettanaito/atomic-layout/compare),
2. Select the feature branch from your fork and the target branch from Atomic layout,
3. Fill in the pull request template with patience,
4. Undergo a code review,
5. Witness your changes in the repository!


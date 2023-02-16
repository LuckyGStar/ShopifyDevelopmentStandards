# Shopify Development Standards

## Shopify & Github

  We should use [shopify & github integration](https://shopify.dev/docs/themes/tools/github) for codebase management and tracking changes.
  The Shopify GitHub integration lets you connect a GitHub account or organization with a Shopify login. This connection helps you to make and track changes to online store theme code. It also helps you to collaborate with other developers and share progress in real time.

  - Automatically pull and push theme code from any organization or repository associated with your GitHub account
  - Connect one or more branches from a repository to easily develop and test new theme features or campaigns
  - Keep a theme up to date with commits to a branch, and track edits made in the Shopify admin, including the code editor and theme editor
  - Connect branches to unpublished or published themes

## Initialise repository

  1. Create a new repository in Github.
  ```bash
  $ gh repo create [ShopName]
  ```

  2. Login to partners account.
  ```bash
  $ shopify login
  ```

  3. Login to development / production store.
  ```bash
  $ shopify login --store=***.myshopify.com
  ```

  4. Pull latest theme (live theme).
  ```bash
  $ shopify theme pull
  ```

  5. Init git and set main branch.
  ```bash
  $ git init
  $ git branch -M master
  $ git remote add origin [origin url]
  ```

  6. Commit & push to the origin repository.
  ```bash
  $ git commit -m "some commit message"
  $ git push origin master
  ```

  7. Create `develop` branch from `master` branch.
  ```bash
  $ git checkout -b develop
  $ git push origin develop
  ```

  8. Repository successfully  initialised! :clap:

## Development Tools
  
  Shopify development in local could be easier with the tools below.

  > Tools doesn't include [Slate](https://github.com/Shopify/slate) while it has been archived and end of support.

  - [Shopify Themekit](https://shopify.dev/docs/themes/tools/theme-kit) (recommended for 1.0 themes)
  > Themekit is already being replaced with shopify-cli and highly recommend to use shopify-cli instead of themekit.

  - [Shopify Cli](https://shopify.dev/docs/themes/tools/cli) (recommended for existing themes & 2.0 themes)
  - [Shopify Packer](https://hayes0724.github.io/shopify-packer/) (highly recommend for existing themes & new themes)
  - [Nx Shopify](https://trafilea.github.io/nx-shopify/) (highly recommended when need to use typescript & new themes)

## Git Branching Rules

  Git branches should be connected to the online store and follow rules below.

  - Production theme (`master` branch)
  - Staging theme (`develop` branch)
  - Feature/Fix thems (`feature/fix` branches)

## Getting Started Development with [Shopify Cli](https://shopify.dev/docs/themes/tools/cli)

  This assumes you are getting started on a ticket assigned.

  1. Pull from `master` branch.
  > This will pull latest online changes made by other developers & online editor by client.

  ```bash
  $ git pull origin master
  ```

  2. Pull from `develop` branch and rebase with latest `master` branch.
  > This will pull latest online changes made by other developers & online editor by client.

  ```bash
  $ git pull origin develop
  $ git rebase master
  ```

  3. Create a new branch for getting started with development.
  > feature/*** for new feature development and fix/*** for fixing bugs.
    
  ```bash
  $ git checkout -b feature/new-design
  $ git checkout -b fix/mobile-header-responsive-issue
  ```

  4. If you already have branch worked on, just rebase with `develop` branch so that it is synced.
  > If there are conflicts in rebase, please resolve it manually.

  ```bash
  $ git checkout fix/mobile-header-responsive-issue
  $ git rebase develop
  ```

  5. Login to the shopify partners.

  ```bash
  $ shopify login
  ```

  6. Login to the store for development.

  ```bash
  $ shopify login --store=***.myshopify.com
  ```

  7. Start the development server.

  ```bash
  $ shopify theme serve
  ```

  8. Make sure you are getting this in console.

  ````
  ➜  theme git:(master) shopify theme serve

  ┏━━ Viewing theme… ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ┃ * Syncing theme #124835922035 on ***.myshopify.com
  ┃                                                                                                                                                                             100%
  ┃
  ┃ Serving .
  ┃
  ┃ Please open this URL in your browser:
  ┃ http://127.0.0.1:9292
  ┃
  ┃ Customize this theme in the Theme Editor, and use 'theme pull' to get the changes:
  ┃ https://***.myshopify.com/admin/themes/124835922035/editor
  ┃
  ┃ Share this theme preview:
  ┃ https://***.myshopify.com/?preview_theme_id=124835922035
  ┃
  ┃ (Use Ctrl-C to stop)
  ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ (21.81s) ━━
  11:14:42 Synced » update assets/yoast-active-script.js
  ````

  9. Open preview url in browser and start development.

  ```bash
  ┃ https://***.myshopify.com/?preview_theme_id=124835922035
  ```

  10. Make the updates to the codebase & `ctrl + save`. Please make sure you see below.
  > This means file you have updated has been synced with online store.

  ````
  11:14:42 Synced » update assets/yoast-active-script.js
  ````

  11. Refresh your browser and you will see the updated theme.
  12. Once made all updates, push changes.
  ```bash
  $ git add .
  $ git commit -m "some commit message"
  $ git push origin fix/mobile-header-responsive-issue
  ```

  13. Raise pull request against `develop` branch and ask for review.
  > Please put theme preview link, task link to the pull request comment. 
  Will provide standard pull request format later.
 
  14. Connect the branch to the online store.
  ````
  [ScreenShot](https://prnt.sc/0rSNZGETZcZi)
  ````
  15. Send the theme preview link to the client for review.
  > Note: Please use the link based on theme id, not preview link generated with shopifypreview.com. It expires and not up-to-date.
  ```
  https://***.com/?preview_theme_id=theme_id
  ```

## Getting Started Development with [Shopify Packer](https://hayes0724.github.io/shopify-packer/)
```
Work In Progress...
```

## Getting Started Development with [Nx Shopify](https://trafilea.github.io/nx-shopify/)
```
Work In Progress...
```

## Git Best Approaches

1. Run `git config --global push.default simple` in your terminal once. You don't need to do it every time you contribute, just once.

2. Make sure you have latest `develop` locally:
```
git checkout develop
git pull
```

3. Create a new branch based on it:
```
git checkout -b feature/my_feature_branch
```

4. Commit and open a Pull Request

5. After code review is done and you update your branch, make sure that your Pull Requests is still mergeable.
If there is a Github conflict with `develop`, and your branch is not merge-able anymore, pull the latest `develop` locally, then merge in your branch:
```
git checkout develop
git pull
git checkout feature/my_feature_branch
git merge develop
```

6. Fix the conflicts and push your branch. Try to fix it yourself by looking into `develop` branch changes and Trello cards, and figuring out what final behavior should do - only ask for help if you did all you could. That's because we are all not full-time yet, and waiting for someone else for help with things like this really delays features by a lot. Always try to finish the card by yourself and make sure you did the best you could to finish it.

7. Make sure your Github PR diff shows only changes relevant to your feature.

For more advanced developers I strongly encourage you to use `git rebase` instead of `merge`. Double-check that your git push behaviour is set to simple: `git config --global push.default simple`

## CI/CD & Tools

For advanced development we should refer below github actions and tools.

1. [Shopify LightHouse CI](https://github.com/Shopify/lighthouse-ci-action)
  - We can get google light house ci status of current theme at any time
  - We can check how much impacts new commit / pull request has for performance

2. [Shopify Theme Check Action](https://github.com/Shopify/theme-check-action)
  - We can force developers to follow development standards & best coding style guide
  - We will be able to check code quality for every commit / pull request so that we can keep clean code
  - We can automate this check with github action

3. [Shopify Theme Inspector](https://shopify.dev/docs/themes/tools/theme-inspector)
  - We can detect what part of theme code causes slow performance in live

## New Theme Development Approaches

1. Not customise legacy / premium themes and build new theme from scratch.
  Why?
  - Usually legacy / premium themes have lots of styles/scripts/liquid codes that is not being used in new design and it causes performance issues and complexity of the structure.
  - It also forces developers to stick with existing theme structure and it blocks development of new feature sometimes.
  - Premium theme versions are usually being updated and it makes things complicated and unable to sync once theme has been built.
  
2. Framework for new theme development.
  - [Shopify Packer](https://hayes0724.github.io/shopify-packer/) (highly recommend new themes)
  - [Nx Shopify](https://trafilea.github.io/nx-shopify/) (recommended when need to use typescript)

3. Framework for new theme development. (Headless)
  - [Hydrogen](https://hydrogen.shopify.dev/)
  - [Gatsby Shopify](https://github.com/gatsbyjs/gatsby-starter-shopify) (highly recommended)

4. Tools
  - [Tailwind CSS](https://tailwindcss.com/) for front-end framework
  - [React.JS](https://reactjs.org/) / [Vue.JS](https://vuejs.org/) for components

5. Suggested attempts
  - No use of jQuery, and use vanilla js instead
  - Write section scripts as module with javascript (for example, using javascript class)

## Coding Style Guide
  Please follow [GetBEM](https://getbem.com/) for front-end development

  1. HTML
  2. CSS
  3. JAVASCRIPT
  4. LIQUID

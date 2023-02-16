# Shopify Development Standards

## CodeBase Init

  We should use [shopify & github integration](https://shopify.dev/docs/themes/tools/github) for codebase management and tracking changes.
  The Shopify GitHub integration lets you connect a GitHub account or organization with a Shopify login. This connection helps you to make and track changes to online store theme code. It also helps you to collaborate with other developers and share progress in real time.

  - Automatically pull and push theme code from any organization or repository associated with your GitHub account
  - Connect one or more branches from a repository to easily develop and test new theme features or campaigns
  - Keep a theme up to date with commits to a branch, and track edits made in the Shopify admin, including the code editor and theme editor
  - Connect branches to unpublished or published themes

  1. Create a new repository in Github.
  2. Clone live theme (latest version) via shopify cli.
  3. Init git, set remote origin and push codebase to the repository.
  4. Set `master` branch as the main branch.

## Development Flow
  
  Shopify development in local could be easier with the tools below.

  - [Shopify Themekit](https://shopify.dev/docs/themes/tools/theme-kit) (recommended for 1.0 themes)
  - [Shopify Cli](https://shopify.dev/docs/themes/tools/cli) (recommended for existing themes & 2.0 themes)
  - [Shopify Packer](https://hayes0724.github.io/shopify-packer/) (highly recommend for existing themes & new themes)
  - [Nx Shopify](https://trafilea.github.io/nx-shopify/) (highly recommended when need to use typescript & new themes)

  ### Shopify Cli
  
## CI/CD
## Git Best Approaches
## Coding Style Guide
## Tools


# Lerna Monorepo Template

This repository comprises a slim monorepo template based on the following tools:

- [Node](https://nodejs.org/en)
- [TypeScript](https://www.typescriptlang.org/)
- [NPM workspaces](https://docs.npmjs.com/cli/v7/using-npm/workspaces)
- [Lerna](https://lerna.js.org/)

## Using This Template

This is a summary of how to use this template. You should refer to the documentations linked above to get more detailed information on each tool used bu this template.

### Getting Started

1. Make sure you are logged in to GitHub
2. Go to the template [GitHub repository](https://github.com/thomazmz/monorepo-template) and click the `Use This Template` button 
3. Under the drop-down menu, click `Create New Repository`
4. A new repository will be created under your GitHub account. You should clone it locally 
4. Rename the keys `name`, `author` and `description` on the `pakcage.json` file 
5. Use the examples inside the `./packages` folder to create your monorepo packages 
6. Remember to add your new packages to the `tsconfig.json` `compilerOptions.path` array 
6. Wipe out the preexisting example directories inside the `packages` folder so that they don't clutter your project

### Using Different Folders to Hold Monorepo Packages

As a starting point, this monorepo places packages under the `./packages` folder. You can place your packages under a different folder or even under multiple folders, as long as they are not outside your project's directory. To do that, go to your `package.json` file and change the globs under the  `workspaces` array.

### Installing Internal Dependencies 

Some of your monorepo packages might be dependent to each other. To install monorepo packages as dependencies of other monorepo packages you should run the following command: 

`npm install <your-dependency> --scope=<your-dependent-package>`. 

Looking into our example packages, we have `@monorepo/dependency` and `@monorepo/dependent`. To install the first as a dependency on the second, we should run the following:

`npm install @monorepo/dependency --scope=@monorepo/dependent`.

### Using TypeScript Across the Monorepo

When you open this project, your IDE might look for the `tsconfig.json` file in the project's root to resolve TypeScript's IntelliSense. If you look into the root `tsconfig.json`, though, you might realize that its values are not suitable for individual packages to run their builds. 

To accomplish individual builds, packages should have their own `tsconfig.json` file. Check the config files on the example packages of this repository to understand what are the minimum definitions you should place under your config files. It is recommended that all the nested config files extend the root `tsconfig.json` definition, this helps keep standardized compiler options across the whole monorepo.


<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="120" alt="Nest Logo" /></a>
</p>

[travis-image]: https://api.travis-ci.org/nestjs/nest.svg?branch=master
[travis-url]: https://travis-ci.org/nestjs/nest
[linux-image]: https://img.shields.io/travis/nestjs/nest/master.svg?label=linux
[linux-url]: https://travis-ci.org/nestjs/nest


## Description

This is a quick start project for setting up your own package library. It includes automated versioning using [release-it](https://github.com/release-it/release-it) and publishing the package for use in multiple applications, allowing for easy sharing of functionality and code.


## Installation

```bash
$ git clone git@github.com:Emgevorgyan/nestjs-package-quick-start.git
$ cd nestjs-package-quick-start
# install dependencies
$ npm ci
```

## Build your package 

Take a moment to poke around in the `nestjs-package-quick-start` folder. Here are a few things to notice:

1. The `lib` folder has two files: 
	 * `test.ts` is the entire functionality of our package; it exports one simple test function (getMessage) we'll import into our app to prove to ourselves that we've actually installed and are using the package.
	 *  `index.ts` exports the `test.ts` function from the folder (it's a [barrel file](https://basarat.gitbook.io/typescript/main-1/barrel)).

2. The `package.json` file has several important sections. One to pay attention to now is the different types of package dependencies that are listed:
	* `devDependencies` are packages that are only required for the development. In this case, since we are building a Nest-based package, we need Nest and other development tools such as testing utilities and TypeScript.
	* `peerDependencies`: this section is used to indicate that the package is compatible with Nest version 9 (with a minimum of 9.0.0). This ensures that the project using the package has a compatible NestJS environment. Declaring the @nestjs/common package is sufficient for this purpose. Specifying a version of ^9.0.0 allows for compatibility with any minor versions of NestJS that the user may have installed.
	* `dependencies`: this section lists the packages that are required to run the code. These should not include NestJS, but any additional packages needed for the code to function. For example, if the dotenv package is used in the code, it would belong in the dependencies section, as it is not provided by NestJS.

***
Add your modules and services...

To make the code accessible to other applications, you need to export it in the `index.ts` file, similar to how it is done for the `test.ts` file.

`export * from './test';`


##  Publish Package:

Before publishing the package to the npm registry:

* set a name for your package (chose a unique name for you package or just use scoped names)
* edit package.json
Identify your reusable library by updating the `name`, `version`, `author`, adding a link to a git `repository` etc. Additionally, to learn more about versioning your package when publishing or republishing, refer to [semantic versioning (“semver”)](https://semver.org/) which is the best practice for npm packages.

To publish your package on npm, first, [create an account](https://www.npmjs.com/signup) on npm if you don't have one. Then run the command `npm login` in the console.
Navigate to the root of your package, run `npm run prerelease` and then `npm run release` to release your package to the npm registry. By default, [release-it is](https://github.com/release-it/release-it#interactive-vs-ci-mode) interactive and allows you to confirm each task before execution.


## License

[MIT licensed](LICENSE).

# CHANGELOG

## 0.11.0

Make `VCReader` and `VCDualReader` more efficient by having `read` return only
the effective value. A new `inspect` method is available to get values from the 
other scopes.

## 0.10.0

Upgrade to ES2020 and exclude source maps from release package.

## 0.9.0

Un-expose the `validate` and `transform` properties passed to the constructors 
of `VCReader` and `VCDualReader`. This partially undoes the change we made in
0.8.0.

## 0.8.0

Expose the arguments passed to the constructors of `VCReader` and `VCDualReader`.

## 0.7.1 

Undo mistake in version 0.6.0 where comments were stripped from the output. Since
this package is meant to be used as a library, it should have comments included.

## 0.7.0

Upgrade dev dependencies and vscode engine version, but downgrade `@types/node` 
dev dependency to the current version of Node.JS used by vscode.

## 0.6.0

Revamp the code and documentation. Furthermore, add ability to transform the
effective value.

## 0.5.2

Minor code update.

## 0.5.1

Improve API documentation.

## 0.5.0

Update dev dependencies and upgrade the language version of the output Javascript. Also, change the npm `prepack` script to `prepare`.

## 0.4.0

Make the `_read` method (which should have been internal in the first place) 
internal.

## 0.3.0

Execute `npm install` before packing package.

Previously this wasn't done and made it impossible for this package to be 
pulled and built by NPM.

## 0.2.3

Fix dependency vulnerability.

## 0.2.2

Fix package manifest version number and repository url. 

## 0.2.1

Fix dependency vulnerability.

## 0.2.0 

Package renamed to `validated-configuration-reader`.

Since vscode introduced language based configuration values, the previous 
`ConfigurationHandler` class had to be expanded to read those values. However, 
it was also noticed that the previous `ConfigurationHandler` class did not 
need to have the `migrate` and `set` methods, so these were removed while
`ConfigurationHandler` was updated. 

Since `ConfigurationHandler` can no longer set values, it was renamed to
`VCReader`, and the name of the package was changed in the process. 

The overall list of changes are: 

- Rename package to `validated-configuration-reader`. 
- Rename `ConfigurationHandler` to `VCReader`.
- Rename `ConfigurationHandlerCompat` to `VCDualReader`. 
- Rename the `typecheck` parameter in `VCReader`'s constructor to `validate`.
- Rename `get` method to `read`.
- Remove `migrate` methods. 
- Remove `set` methods.
- Remove `shelljs` dev dependency and associated scripts
    * Previously `shelljs` was used to delete the `out` folder before each build. 
      However, this was deemed unnecessary since this package is always retrieved 
      from github. Since the `out` folder is set to be ignored by git, it will 
      not be uploaded to github, and thus there is no risk due to unclean files 
      in the `out` folder leaking to users of the package. 
    * `shelljs` was also previously used to pass console arguments when starting 
      tests via the command line. However, this is no longer necessary with the 
      new `vscode-test` test runner.
- Expand `VCReader` and `VCDualReader` to read language based scopes.
- Allow the user to specify the scope where the configuration values will be read 
  from.
- Rewrite tests to include the new language based scopes.
- Modify the organization of the test environment slightly.
- Synchronize the dev dependencies list with that of a project generated by the 
  latest version of 'Visual Studio Code Extension Generator'. Changes of note 
  include:
    * Replace the old test runner with the new `vscode-test` runner.
    * Replace the old `tslint` file with the newer `.eslintrc.json` file that 
      specifies typescript linting rules.
- Rename errors.

## 0.1.0

- Fix spelling for the test configuration's comments.
- Fix formatting for parts of the code.
- Tweak the readme.
- Tweak the package manifest's description.
- Update dev dependencies.

## 0.0.5

- Rename mentions of `typeCheck` to `typecheck` by removing the camel casing.
- Update dev dependencies.

## 0.0.4 

- Update dev dependencies.

## 0.0.3 

- Exclude type declarations of the test code from being packed by NPM.

## 0.0.2

- Simplify some of the internal functions used in tests. No API changes.

## 0.0.1

- Initial release
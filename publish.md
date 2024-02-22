---
share: true
---
# [scoped public packages](https://docs.npmjs.com/creating-and-publishing-scoped-public-packages)

# using yarn on npm.js
<kbd>.yarnrc</kbd>
```rc
registry: https://registry.npmjs.org/
```

# check package before publish
`npm publish --dry-run`
`npm publish --dry-run subdir`

# publish package to npmjs.com
`npm publish

# publish private package
`npm publish --access private`
To use private packages, you must have a [paid user or organization account](https://www.npmjs.com/pricing)

# package as .tar
Create a tarball from a package with [`npm pack`](https://docs.npmjs.com/cli/v8/commands/npm-pack)

# published package information

- display **latest version** available on the registry
  `npm view packageName version`
  
- display **all versions** available on the registry
  `npm view packageName versions`
  
- get owner
  `npm owner ls packageName@version`

# local packages

- display **local version**
  `npm list packageName`

- display **all local packages**
```bash
npm list --depth=0 | awk '{print $2}'
npm list --depth=0 | awk '{print $2}' | grep @user/
```

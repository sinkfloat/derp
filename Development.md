### Rebase

git remote add upstream https://github.com/directus/directus

git fetch upstream

git rebase upstream/main

```
Auto-merging app/package.json
CONFLICT (content): Merge conflict in app/package.json
error: could not apply a29f0dd70... package.json change npm registry name
```

git add app/package.json

git rebase --continue


### Foldering structure

api => core backend, to handling main logic of the directus like ItemsService, RelationsService, FieldsService, Webhook
and etc

app => the UI

packages/create-directus-extension => for scaffolding when creating extension

packages/specs => for handling Open API Documentation

packages/shared => the library for utilitas to be used globally and place to you save type interface

packages/schema => schema inspector for all supported databases

packages/drive\* => for handling storage

### Development Rule

There are something that you must to be careful. In NPM, the package can dependant to another package and we can see the
dependecy on package.json file.

In directus there are package dependency, like example the <b>api</b> package dependent to <b>app</b> package. So if you
want to modify the <b>app</b> pacakge then you must build and push the <b>app</b> package to NPM registry. After that
you must edit package.json on the <b>api</b> package build it and push to the NPM Registry.

NB: you cant push same version of package more than one to NPM registry

### Building

Example case: My current state the version of @synqueit/app is 9.18.0

- After modification of app you must upgrade your package version

```
npm version patch
```

to upgrade version to 9.18.1

```
npm version minor
```

to upgrade version to 9.19.0

```
npm version major
```

to upgrade version to 10.0.0

You must read the semantic version rule to understand that

- Build it with "npm run build" to generate static files of the app

### Push to npm registry

- run "npm login" and input your NPM credential

- if it is your first publish then you can run command bellow

```
 npm publish --access public
```

- or else you can just run that command without "--access public"

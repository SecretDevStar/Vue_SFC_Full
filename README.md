# vue-sfc-rollup

vue-sfc-rollup exists to provide the minimal setup necessary to compile a Vue Single File Component (SFC) into a form ready to share via npm.

## TL;DR
```bash
npm install -g vue-sfc-rollup
sfc-rollup-init
# fill in prompts
cd my-component
vue serve ./src/my-component.vue # Or other live-refresh coding
# Do dev stuff...
npm run build
# Ready to publish!
```


## Details

The vue-sfc-rollup wizard scaffolds 4 files for you to kick of your SFC development. These files include a minimal [rollup](https://rollupjs.org) config, a corresponding package.json file with build script and dependencies, a wrapper used by rollup when packaging your SFC, and a sample SFC to kick-start development.

If you wish to integrate this into an existing SFC, please check out [the vue-sfc-rollup source](https://github.com/mgdodge/vue-sfc-rollup). The files generated by the wizard are located inside the `templates` directory of the repository. Merge the important bits of those file with your existing code, and you'll be good to go.

### Install

To install [vue-sfc-rollup](https://www.npmjs.com/package/vue-sfc-rollup), simply open a terminal and execute the following:

```bash
npm install -g vue-sfc-rollup
```

Now, whenever you want to start a new component, you can just type `sfc-rollup-init` to run the wizard to scaffold a new SFC for you!

### Using the vue-sfc-rollup wizard

Using the vue-sfc-rollup wizard is simple:
```bash
sfc-rollup-init
# fill in prompts
```
The wizard will prompt for the following:

  - *npm name*: This is how people will find your component in npm. Please refer to [the official npm docs](https://docs.npmjs.com/files/package.json#name) for details of what to enter here
  - *component name*: This is the kebab-case version of your SFC component name - what your component's tag would be if you were to use this in an HTML page or another component. Since any kebab-case tag name would also be a safe file name, this will also be the name of the generated files.
  - *save path*: Where do you want to save this component? By default, the wizard will use your current directory and create a new folder with the same kebab-case name as your component (eg. ./my-component/).

After prompting you for this information, the wizard then creates copies of the files found in the `templates` directory and performs the forementioned {{ variables }} replacement using the information enterd.

### Developing your SFC

vue-sfc-rollup is currently focused on packaging your SFC for distribution via npm. The Vue cli is excellent for the actual development process of your SFC, and it is recommended you use the official tooling.

With v3 of the Vue cli installed globally, you can truly develop your SFC with zero conf just by entering the following commands:

```bash
cd ./my-component
vue serve ./src/my-component.vue
```

This will start up a webpack dev server with hot reloading and all the other awesomeness!

## Packaging your SFC

Once your development is done, it's time to package your component to publish to npm. The actual process of [publishing to npm](https://docs.npmjs.com/getting-started/publishing-npm-packages) is left up to you, but the whole purpose of this project is to compile your SFC so that it's packaged and ready to go.

```bash
cd ./my-component
npm run build
# rollup does its thing...done!
```

Running the build script results in 3 compiled files in the `dist` directory, one for each of the `main`, `module`, and `unpkg` properties listed in your package.json file. With these files are generated, you're ready to go!

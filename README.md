# Patch Package in newer Strapi 4 Versions

## Steps I did to reproduce this example

- Create an application
- Installed EE license
- Follow the instructions to setup patch-package from their [documentation](https://www.npmjs.com/package/patch-package)
- Manually edit the module `node_modules/@strapi/admin/dist/ee/server/index.js` Lines 1562 to 1565 to comment out code and add custom code
- Run the command `npx patch-package @strapi/admin` to generate the [patch file](patches/@strapi+admin+4.25.12.patch)

## Testing the patches

- Delete your `node_modules` folder
- Delete any lock files (package-lock.json or yarn.lock)
- Run `npm install` or `yarn install`
- Check the `node_modules/@strapi/admin/dist/ee/server/index.js` file to see if the patch was applied

## Expected behavior

When the patch file exists, any time the node_modules are installed, the postinstall script should be executed and the patch should be applied.

## Actual behavior

- Node modules are installed
- Postinstall script is executed
- Patch is applied and custom logic is now used in place of original logic

## Warnings

It's quite likely that any update to Strapi could break your patches and they will need to be regenerated. This is a manual process and should be done with caution.



# Demo to demonstrate https://github.com/microsoft/rushstack/issues/3033

`/app` - Home of the plain package.

`/rush-managed` - Home of the rush managed package.

First, setup rush managed package:

```
cd ./rush-managed
rush update
```

Then, try to link "rush package" into "plain package"

```
cd ./app
npm run link:libs # Shorthand for `npm link ../rush-managed/packages/lib`
```

Here's the output:

```
PS X:\Temp\rush-demo\app> npm run link:libs

> app@1.0.0 link:libs X:\Temp\rush-demo\app> npm link ../rush-managed/packages/lib


> lib@1.0.0 preinstall X:\Temp\rush-demo\rush-managed\packages\lib
> echo 'Debug: installing lib-a'

'Debug: installing lib-a'
npm WARN lib@1.0.0 No description
npm WARN lib@1.0.0 No repository field.
npm WARN lib@1.0.0 No license field.

npm ERR! code EEXIST
npm ERR! path X:\Temp\rush-demo\rush-managed\packages\lib\node_modules\.bin\tsc.ps1
npm ERR! Refusing to delete X:\Temp\rush-demo\rush-managed\packages\lib\node_modules\.bin\tsc.ps1: containing path X:\Temp\rush-demo\rush-managed\packages\lib\node_modules\typescript isn't under npm's control
npm ERR! File exists: X:\Temp\rush-demo\rush-managed\packages\lib\node_modules\.bin\tsc.ps1
npm ERR! Remove the existing file and try again, or run npm
npm ERR! with --force to overwrite files recklessly.

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\Leslie Leigh\AppData\Roaming\npm-cache\_logs\2021-11-26T05_40_44_502Z-debug.log
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! app@1.0.0 link:libs: `npm link ../rush-managed/packages/lib`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the app@1.0.0 link:libs script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\Leslie Leigh\AppData\Roaming\npm-cache\_logs\2021-11-26T05_40_44_521Z-debug.log
```
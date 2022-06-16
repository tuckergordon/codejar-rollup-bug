# Codejar - Rollup Bug

This repo demonstrates a bug that occurs when trying to use the latest versions of [Codejar](https://github.com/antonmedv/codejar), [@rollup/plugin-commonjs](https://github.com/rollup/plugins/tree/master/packages/commonjs), and [@rollup/plugin-node-resolve](https://github.com/rollup/plugins/tree/master/packages/node-resolve).

If you update either of the @rollup libraries to their latest versions (as of 6/16/2022), you will see an error when you try to build the application.

#### Works

```json
"@rollup/plugin-commonjs": "21.0.1",
"@rollup/plugin-node-resolve": "13.2.1",
```

#### Does not work

```json
"@rollup/plugin-commonjs": "22.0.0",
"@rollup/plugin-node-resolve": "13.3.0",
```

## To see repo working as expected

1. `npm ci`
2. `npm run dev`
3. Navigate to [localhost:8080](localhost:8080) to see a working Codejar text editor

## To see the bug

1. Run either `npm i -D @rollup/plugin-commonjs@latest` or `npm i -D @rollup/plugin-node-resolve@latest`
2. `npm run build`


You will see the following error:

```zsh
[!] (plugin commonjs--resolver) Error: Unexpected token (Note that you need plugins to import files that are not JavaScript)
node_modules/codejar/codejar.ts (3:5)
1: const globalWindow = window
2: 
3: type Options = {
        ^
4:   tab: string
5:   indentOn: RegExp
Error: Unexpected token (Note that you need plugins to import files that are not JavaScript)
    at error (/Users/tuckergordon/Desktop/svelte-typescript-app/node_modules/rollup/dist/shared/rollup.js:198:30)
    at Module.error (/Users/tuckergordon/Desktop/svelte-typescript-app/node_modules/rollup/dist/shared/rollup.js:12553:16)
    at Module.tryParse (/Users/tuckergordon/Desktop/svelte-typescript-app/node_modules/rollup/dist/shared/rollup.js:12930:25)
    at Module.setSource (/Users/tuckergordon/Desktop/svelte-typescript-app/node_modules/rollup/dist/shared/rollup.js:12835:24)
    at ModuleLoader.addModuleSource (/Users/tuckergordon/Desktop/svelte-typescript-app/node_modules/rollup/dist/shared/rollup.js:22309:20)

```
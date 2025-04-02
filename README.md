Running `node in.mjs` passes perfectly.
Running `node out.js` throws this error:

```js
/Users/skn0tt/dev/tmp/repro-rollup-no-treeshake-react/out.js:1879
createContext();
^

TypeError: createContext is not a function
    at Object.<anonymous> (/Users/skn0tt/dev/tmp/repro-rollup-no-treeshake-react/out.js:1879:1)
    at Module._compile (node:internal/modules/cjs/loader:1546:14)
    at Object..js (node:internal/modules/cjs/loader:1689:10)
    at Module.load (node:internal/modules/cjs/loader:1318:32)
    at Function._load (node:internal/modules/cjs/loader:1128:12)
    at TracingChannel.traceSync (node:diagnostics_channel:315:14)
    at wrapModuleLoad (node:internal/modules/cjs/loader:218:24)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:170:5)
    at node:internal/main/run_main_module:36:49

Node.js v22.11.0
```

`out.mjs` was created by running this command:

```bash
npx rollup -i in.mjs --no-treeshake -p @rollup/plugin-node-resolve -p @rollup/plugin-commonjs -o out.js
```

If you run the same command with `--treeshake` instead of `--no-treeshake`, it works fine.

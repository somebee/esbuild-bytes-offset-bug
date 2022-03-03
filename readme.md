
Run the command:
```
esbuild --bundle index.js --outdir=dist --loader:.svg=file --metafile=dist/meta.json --public-path=/some-long-public-path/
```

Output of meta is incorrect:
```
"dist/index.css": {
      "imports": [],
      "inputs": {
        "styles.css": {
          "bytesInOutput": 61
        }
      },
      "bytes": 94
    }
  }
```
bytesInOutput does not take the public-path into account. It is correct when public-path is not set.

## Testing

Run `npm run test`. If it logs out `"bytesInOutput": 56` at the end, the test passes.
## How to reproduce

```bash
# Checkout and install dependencies
git clone git@github.com:pp0rtal/swc-bug-node_modules-interfer.git
cd swc-bug-node_modules-interfer/backend
npm install
cd ../

# Reproduce error
./backend/node_modules/.bin/swc ./backend/ --out-dir ./backend_dist
```

## Output

```
failed to load file

Caused by:
    stream did not contain valid UTF-8
failed to load file

Caused by:
    stream did not contain valid UTF-8
Successfully compiled: 1 file with swc (70.04ms)
Failed to compile 2 files with swc.
Error: Failed to compile:
backend/node_modules/map-or-similar/map-or-similar.min.gzip.js
backend/node_modules/memoizerific/memoizerific.min.gzip.js
    at initialCompilation (/swc-bug-node_modules-interfer/backend/node_modules/@swc/cli/lib/swc/dir.js:163:19)
    at async dir (/swc-bug-node_modules-interfer/backend/node_modules/@swc/cli/lib/swc/dir.js:228:5)
# exited with code 1
```

## Expected

- SWC compilation should not throw for excluded files.
- For instance, [`excluded_file.ts`](backend%2Fexcluded_file.ts) is properly excluded and prevents compiler to throw

# eslint-plugin-import bug report

## Bug description

When an export is used right after an import statement ``newline-after-import`` will break ``eslint-plugin-import``

### Broken
```

import stub from './stub';

export {
    stub
}
```

### Fine
```

import stub from './stub';

console.log('Hello');

export {
    stub
}
```

## Exception stack

```
Oops! Something went wrong! :(

ESLint: 7.26.0

TypeError: Cannot read property 'type' of null
Occurred while linting C:\Users\carlos.nakane\_repos\_temp\tp\eslint-plugin-import-bug-report\src\index.ts:1
    at isExportNameClass (C:\Users\carlos.nakane\_repos\_temp\tp\eslint-plugin-import-bug-report\node_modules\eslint-plugin-import\lib\rules\newline-after-import.js:51:69)
    at checkForNewLine (C:\Users\carlos.nakane\_repos\_temp\tp\eslint-plugin-import-bug-report\node_modules\eslint-plugin-import\lib\rules\newline-after-import.js:79:45)
    at checkImport (C:\Users\carlos.nakane\_repos\_temp\tp\eslint-plugin-import-bug-report\node_modules\eslint-plugin-import\lib\rules\newline-after-import.js:133:9)
    at C:\Users\carlos.nakane\_repos\_temp\tp\eslint-plugin-import-bug-report\node_modules\eslint\lib\linter\safe-emitter.js:45:58
    at Array.forEach (<anonymous>)
    at Object.emit (C:\Users\carlos.nakane\_repos\_temp\tp\eslint-plugin-import-bug-report\node_modules\eslint\lib\linter\safe-emitter.js:45:38)
    at NodeEventGenerator.applySelector (C:\Users\carlos.nakane\_repos\_temp\tp\eslint-plugin-import-bug-report\node_modules\eslint\lib\linter\node-event-generator.js:256:26)
    at NodeEventGenerator.applySelectors (C:\Users\carlos.nakane\_repos\_temp\tp\eslint-plugin-import-bug-report\node_modules\eslint\lib\linter\node-event-generator.js:285:22)
    at NodeEventGenerator.enterNode (C:\Users\carlos.nakane\_repos\_temp\tp\eslint-plugin-import-bug-report\node_modules\eslint\lib\linter\node-event-generator.js:299:14)
    at CodePathAnalyzer.enterNode (C:\Users\carlos.nakane\_repos\_temp\tp\eslint-plugin-import-bug-report\node_modules\eslint\lib\linter\code-path-analysis\code-path-analyzer.js:711:23)
```

## Steps to reproduce

1. npm install
2. npm run lint

## Additional information

The problem shows up when using ``eslint-plugin-import`` version ``2.23.0``.


When running ``eslint-plugin-import`` version ``2.22.1`` there is no bug;
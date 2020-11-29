## ts-node

定义test.ts 文件

```typescript
import { empty } from '../src/utils/core';
import assert = require('assert');

let a = null;
console.log(123);
assert.strictEqual(empty(a),true);
```

运行test.ts文件`ts-node test.ts`

## tsconfig.json

```typescript
{
  "compilerOptions": {
    "module": "commonjs",
    "declaration": true,
    "removeComments": true,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "target": "es2017",
    "sourceMap": true,
    "outDir": "./dist",
    "baseUrl": "./",
    "incremental": true
  },
  "exclude": ["node_modules", "dist"]
}
```

## 调式ts文件

`"test": "node --inspect-brk -r ts-node/register ./test/aa.test",`

## 参考

[npmjs文档](https://www.npmjs.com/package/ts-node)


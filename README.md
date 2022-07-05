# rejection-tracking-polyfill

针对 Hippy iOS(JSCore) Promise 对 `unhandledRejection` 异常错误处理的插件。由于 `rejection-tracking` 有一定的性能损耗，业务可按需引入。

## 使用

1. `npm install -D @hippy/rejection-tracking-polyfill`

2. 引入脚本

可以在打包脚本里直接引入，也可以在业务代码里引入

+ webpack 配置

```javascript

// iOS webpack 配置
module.exports = {
    entry: {
        index: ['@hippy/rejection-tracking-polyfill', 'dist/dev/index.js']
    },
}
```

+ 业务代码配置

```javascript
import { Hippy } from '@hippy/react';
import '@hippy/rejection-tracking-polyfill';

new Hippy({
    appName: 'Demo',
    entryPage: App,
}).start();
```

3. 监听错误

```javascript
global.Hippy.on('unhandledRejection', (error) => {
  console.error('unhandledRejection', error.stack, error.message);
});
```

## 支持版本

Hippy 终端 SDK 版本: `>= 2.14.1`


# pp

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

## 项目介绍
```
该项目目前第一个工具为注释加密工具，目标为两个方向，一个为增加更多的工具方便前端程序员，另一个为提高适用性，做到开箱即用，如做成vscode插件等。
欢迎各位大佬前来指点
```
## 解决打包找不到文件的问题
参考网址（https://blog.csdn.net/kyq0417/article/details/111266776）
打开 node_module/app-builder-lib/out/targets/nsis/NsisTarget.js文件，在 executeMakensis 方法中加入我们所需的参数。
````
//node_module/app-builder-lib/out/targets/nsis/NsisTarget.js
async executeMakensis(defines, commands, script) {
const args = this.options.warningsAsErrors === false ? [] : ["-WX"];
//此处新增
args.push("-INPUTCHARSET", "UTF8");
//结束
for (const name of Object.keys(defines)) {
    const value = defines[name];

    if (value == null) {
    args.push(`-D${name}`);
    } else {
    args.push(`-D${name}=${value}`);
    }
}
````
打包后.exe的文件在dist_electron/win-unpacked/pp.exe
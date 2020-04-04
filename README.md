## 修复 crate-react-app 的 bug


```
const entrypointFiles = entrypoints.main.filter(  // <--- This line here 单页面的时候是{main: []}, 但是多页的时候是 {index:[], other:[]}
  fileName => !fileName.endsWith('.map')
);
```

修改成这样就ok了
```
const entrypointFiles = {};
Object.keys(entrypoints).forEach(entrypoint => {
  entrypointFiles[entrypoint] = entrypoints[entrypoint].filter(fileName => !fileName.endsWith('.map'));
});
```

心累 。。。。
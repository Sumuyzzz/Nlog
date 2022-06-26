


在tsconfig.json里添加

```json
// tsconfig.json
{
  "compilerOptions": {
    // ...
    "types": ["vue/ref-macros"]
  },
}
```


虽然编译器没有报错，但

![[Pasted image 20220626131530.png]]

浏览器没有骗人。

一开始怀疑是，valor的问题，查了半天，没找到相应的 issue。
接着去看rfcs，确定没用错，
然后去，Vue SFC Playground，验证写法没错。

最后锁定vite的问题

```ts
//vite.config.ts
export default defineConfig({

    plugins: [vue({
        script: {
            refSugar: true,
            refTransform: true,
        },
    })],
    resolve: {
        alias: [{
            find: '@',
            replacement: '/src'
        }],
    },
})
```



[# Types for "ref sugar (take 2)" not available](https://github.com/johnsoncodehk/volar/issues/521)

[# fix: Ref transform being applied to variables named `hasOwnProperty`](https://github.com/vuejs/core/pull/4515)
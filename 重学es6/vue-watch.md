watch

vue文档介绍:

`watch` API 与选项式 API [this.$watch](https://vue3js.cn/docs/zh/api/instance-methods.html#watch) (以及相应的 [watch](https://vue3js.cn/docs/zh/api/options-data.html#watch) 选项) 完全等效。`watch` 需要侦听特定的 data 源，并在单独的回调函数中副作用。默认情况下，它也是惰性的——即，回调是仅在侦听源发生更改时调用。

- 与 [watchEffect](https://vue3js.cn/docs/zh/api/computed-watch-api.html#watcheffect) 比较，`watch` 允许我们：
  - 惰性地执行副作用；
  - 更具体地说明应触发侦听器重新运行的状态；
  - 访问侦听状态的先前值和当前值。


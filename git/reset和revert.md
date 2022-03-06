

## reset：丢弃提交

定义：会回退到提交的上次版本，删除这次版本，但注意的是，在reset之后，

```bash
git reset HEAD
```

> 在reset后， `C2` 所做的变更还在，但是处于未加入暂存区状态



![gitResetDemo](E:\个人笔记\git\gif\gitResetDemo.gif)

Git 把 main 分支移回到 `C1`；现在我们的本地代码库根本就不知道有 `C2` 这个提交了





## revert:撤销提交

```bash
git revert HEAD
```

![gitRevertDemo](E:\个人笔记\git\gif\gitRevertDemo.gif)

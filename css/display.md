### table

**【特征】**

　　[1]不设置宽度时，宽度由内容撑开

　　[2]独占一行

　　[3]支持宽高

　　[4]默认具有表格特征，可设置table-layout、border-collapse、border-spacing等表格专有属性

　　[注意]对于display为table和inline-table，若处于分隔边框模型即border-collapse:separate;，margin和padding都可设置；若处于合并边框模型即border-collapse:collapse，只可设置margin

### table-cell

**【特征】**

　　[1]不设置宽度时，宽度由内容撑开

　　[2]非独占一行

　　[3]支持宽高

　　[4]垂直对齐

　　[5]同级等高

　　[注意]display:table-cell的元素不可以设置margin，但可以设置padding
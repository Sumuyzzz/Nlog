# 前言
### 为什么学习 jQuery
使用 jQuery 是为了方便开发，它帮开发者解决了原生 JS 的诸多缺点和麻烦，以下是它相比原生的几大优点：

* 选择器，使用原生 JS 操作 DOM 选择元素是比较麻烦的一件事，而 jquery 支持大部分 css 选择器，写起来超级方便，非常强大。
* 兼容性，jQuery 为不同浏览器进行了适配，1.x 能兼容到 IE6，省去了开发者在这方面的麻烦。
* 动画，封装了一些动画效果，很方便使用。
* 隐式迭代，jQuery 很多时候会替你做遍历，节省代码量。
* 简洁，使用原生 JS 很容易写出非常冗余的代码，jQuery 避免了这点。

### 什么是jQuery

一个快速、轻量级、功能丰富、易用、可扩展的 JS 库，它使 DOM、事件处理、动画、ajax 等操作变得简单，并且将各个浏览器统一为一套简单的 API。它让开发者**写的更少，做的更多**。



### $ 到底是什么

$ 是一个函数，根据参数的不同，其作用也不同，它常见的用法有四种：

1. **入口函数**，传入函数，作为 jq 代码的起点。
2. **转换 DOM 对象为 jq 对象**，传入 DOM 对象，将 DOM 对象转换为 jq 对象。
3. **根据 HTML 字符串生成 jq 对象**，传入 HTML 字符串就能生成 jq 对象，该 jq 对象包含对应的 DOM 对象。
4. **jQuery 选择器**，传入字符串，jq 支持大部分 css 选择器。

### jQuery 选择器

jQuery 支持大部分 css 选择器，所以这里不记与 css 选择器重叠的部分，只记 jQuery 独有的选择器。

#### 伪元素选择器

1. **:first**，获取匹配到的第一个元素。
2. **:last()**，获取匹配到的最后一个元素。
3. **:not(selector)**，去除满足条件的元素。
4. **:even**，匹配所有索引值为偶数的元素，从 0 开始计数。
5. **:odd**，匹配所有索引值为奇数的元素，从 0 开始计数。
6. **:eq(index)**，匹配一个给定索引值的元素。
7. **:gt(index)**，匹配所有大于给定索引值的元素。
8. **:lt(index)**，匹配所有小于给定索引值的元素。
9. **:animated**，匹配所有正在执行动画效果的元素。
10. **:focus**，匹配当前获取焦点的元素。
11. **:target**，匹配 url 中的锚点元素，例如 http://...#a，该选择器将匹配 <div id="a"></div>。
12. **:contains(text)**，匹配包含给定文本的元素。
13. **:empty**，匹配所有空节点，即不包含子元素、文本的元素。
14. **:has(selector)**，匹配 selector 的父元素。
15. **:parent**，匹配非空节点，即含有子元素、文本的元素。
16. **:hidden**，匹配所有不可见元素，即 none、hidden。
17. **:visible**，匹配所有可见元素。
18. **:first-child**，获取第一个子元素，':first' 只匹配一个元素，而此选择器将匹配每个父元素的第一个子元素。
19. **:last-child**，获取最后一个子元素，':last' 只匹配一个元素，而此选择器将匹配每个父元素的最后一个子元素。
20. **:nth-child(n)**，匹配每个父元素下的第 N 个子元素。
21. **:nth-last-child(n)**，与 :nth-child(n) 相反，从末尾开始计数。
22. **:only-child**，如果某个元素只有一个子元素，该子元素将会被选择。

#### 属性选择器

1. **[attribute]**，匹配包含给定属性的元素。
2. **[attribute=value]**，匹配给定的属性是某个特定值的元素。
3. **[attribute!=value]**，匹配所有不含有指定的属性、属性不等于特定值的元素。。
4. **[attribute^=value]**，匹配给定的属性的属性值是以某些值开头的元素。
5. **[attribute$=value]**，匹配给定的属性的属性值是以某些值结尾的元素。
6. **[selector1][selector2][selectorN]**，复合属性选择器，匹配同时满足多个属性选择器的元素。

#### 表单选择器

以下选择器专用于表单，与 css 有重复，不过还是写上了。

1. **:input**，匹配所有 input、textarea、select、button。
2. **:text**，匹配所有 type = 'text' 的 input。
3. **:password**，匹配所有 type = 'password' 的 input。
4. **:radio**，匹配所有 type = 'radio' 的 input。
5. **:checkbox**，匹配所有 type = 'checkbox' 的 input。
6. **:submit**，匹配所有 type = 'submit' 的 input。
7. **:image**，匹配所有 type = 'image' 的 input。
8. **:reset**，匹配所有 type = 'reset' 的 input。
9. **:button**，匹配所有 type = 'button' 的 input 和 button 标签。
10. **:file**，匹配所有 type = 'file' 的 input。
11. **:enabled**，匹配所有可用元素。
12. **:disabled**，匹配所有不可用元素。
13. **:checked**，匹配所有被选中的元素(复选框、单选框等，不包括 select 的 option)。
14. **:selected**，匹配所有被选中的 option 元素。
1. 引入[Splide](https://splidejs.com/guides/getting-started/)插件，也就是上面轮播图实现的插件
2.

代码实现

```vue

      <Splide :options="options" role="group" aria-label="Splide Basic HTML Example">
        <SplideSlide class="xxx" v-for="foods in pages">
          <div class="icon-wrapper" v-for="food in foods">
            <Icon :icon="food.name" width="32" height="32" :key="food.id" class="icon" />
            <div class="title">
              {{ food.title }}
            </div>
          </div>
        </SplideSlide>
      </Splide>

```

Slide：根元素，将数据列表放入根元素内，可有用轮播效果。
SplideSlide：轨迹，每个轮播页面显示的内容。
Icon:使用iconify插件导入的icon组件，可通过icon属性来获取对应的icon图标

```js
const foods = ref([{
    name: 'fluent:food-carrot-20-filled',
    id: 1,
    title: 'carrot'
}, {
    name: 'fluent:food-fish-20-filled',
    id: 2,
    title: 'fish'
}, {
    name: 'ion:fast-food-outline',
    id: 3,
    title: 'fast-food'
}, {
    name: 'material-symbols:emoji-food-beverage-sharp',
    id: 4,
    title: 'beverage'
}, {
    name: 'fluent:food-toast-16-filled',
    id: 5,
    title: 'toast'
}])


const pages = computed(() => {
  const pages = []
  foods.value.forEach((item, index) => {
    const page = Math.floor(index / 4)
    if (!pages[page]) {
      pages[page] = []
    }
    pages[page].push(item)
  })
  return pages
})

```

pages：数据分页，根据数据生成二维数组，每个数组限制规定个数。


```scss

.icons {
  height: 200px;
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  &:deep(.splide) {
    .splide__track {
      width: 100vw;
    }
    .splide__arrow,
    .splide__pagination {
      display: none;
    }
    .xxx {
      display: flex;
      flex-wrap: wrap;
      .icon-wrapper {
        width: 25%;
        display: flex;
        overflow: hidden;
        flex-direction: column;
        font-size: 16px;
        align-items: center;
        justify-content: center;

      }
    }
  }
}


```

**&:deep(.splide):** splide组件里的样式，
**.splide__arrow, .splide__pagination：**  splide组件里的箭头按钮和分页按钮


效果如下

![](https://cdn.jsdelivr.net/gh/Sumuyzzz/pictures/img/202207130223288.gif)


新增

实现icon图标描述过长省略符号。


```scss

        .title {
          white-space: nowrap;
          width: 60px;
          overflow: hidden;
          text-overflow: ellipsis;
        }



```

要注意的是要给div加上宽度，不然会自动延伸，导致没有效果

### 抽离css样式

把text-overflow方法，作为模块封装起来复用

1. 创建`ellipsis.scss`
2. 抽离样式
```scss
@mixin ellipsis {

 white-space: nowrap;

 overflow: hidden;

 text-overflow: ellipsis;

}
```
3. 导入`@import "../../assets/style/ellipsis.scss"`
4. 使用
```scss
 .title {

 @include ellipsis;

 width: 60px;

 }
 ```
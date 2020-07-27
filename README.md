# uniapp悬浮窗菜单，快捷导航

|[ImageView](https://img.cdn.aliyun.dcloud.net.cn/stream/plugin_screens/35a07ca0-bd0c-11ea-ba75-ff18aea1b9b3_0.png?v=1595580107)|[ImageView](https://img.cdn.aliyun.dcloud.net.cn/stream/plugin_screens/35a07ca0-bd0c-11ea-ba75-ff18aea1b9b3_1.png?v=1595580107)|
|:---:|:---:|:---:|

## 导入组件
`import hoverMenu from '@/components/hover-menu/hover-menu.vue'`;

## 引入
```
export default {
    components: {
        hoverMenu
    }
}

```
## 在对应页面进行引用
`<hover-menu></hover-menu>`

## 组件传值, 通过props接收
`<hover-menu :id="id"></hover-menu>`

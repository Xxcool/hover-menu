# uniapp悬浮窗菜单，快捷导航

|[JPImageresizerView](https://github.com/Rogue24/JPImageresizerView)|[InfiniteeUI](https://github.com/Rogue24/InfiniteeUI)|[JPFloatingWindow](https://github.com/Rogue24/JPFloatingWindow)|

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

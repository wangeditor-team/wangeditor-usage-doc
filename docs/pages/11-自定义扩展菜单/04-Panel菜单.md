# Panel 菜单

Panel 菜单，点击菜单时，弹出 panel ，如下图。

![](../../images/panel.png)

开发一个 Panel 菜单，可直接参考[视频菜单的源码](https://github.com/wangeditor-team/wangEditor/tree/master/src/menus/video)，比较好理解。看源码过程中需注意：

- 忽略 typescript 的类型
- 忽略 `index.ts` 中的 `MenuActive`
- 忽略 `create-panel-conf.ts` 中的 `getRandom` 方法，自己定义字符串即可
- 总之，看主流程，不要被一些不重要的事情所影响

另，注册菜单，和上文过程一样，不再赘述。

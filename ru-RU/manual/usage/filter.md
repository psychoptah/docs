# 过滤器

很多时候，我们会希望某些功能只能对于某些群聊或私聊使用。使用权限管理意味着引入数据库，而更轻量的方式是通过 **过滤器 (Filter)** 直接影响插件的作用范围。

## 插件过滤器

::: tip
少数插件与聊天平台无关，例如控制台、数据库插件等。这些插件也因此没有过滤器设置。
:::

大部分插件都提供了过滤器设置，就位于插件详情页的顶部。点击「添加条件」按钮可以创建一个过滤条件。可以通过设置过滤条件来包含或排除任意平台 / 用户 / 群组 / 频道 / 机器人。

::: tip
如果不知道这些 ID 是什么，可以使用 [获取会话信息](./platform.md#获取会话信息) 中介绍的 [inspect](../../plugins/common/inspect.md) 插件。
:::

添加一个条件后，你会发现下方的按钮变成了「添加『与』条件」和「添加『或』条件」两个。Koishi 的过滤器支持二级结构，内层的一系列条件以「与」的逻辑关系组成条件组，外层的一系列条件组以「或」的逻辑关系组成最终的过滤条件。

## 计算属性

Koishi 不仅支持在插件层级设置过滤器，某些配置项还支持在不同的会话下取不同的值。以全局设置为例，我们可以看到 `prefix`, `autoAssign` 等配置项的右侧有一个「…」按钮：

![computed](/manual/console/computed.dark.webp) {.dark-only}

![computed](/manual/console/computed.light.webp) {.light-only}

点击这个「…」按钮，即可将普通的配置项变成一个计算属性。我们可以配置一系列满足某个过滤器以后的取值，以及一个不满足任何情况下的默认值。

利用此特性，我们可以实现一些比较复杂的功能，例如：

- 屏蔽某些群组内的一切消息
- 在不同的平台下使用不同的指令前缀
- 对特定的用户开放额外的使用额度

# Icon 图标

### 介绍

基于字体的图标集，可以通过 Icon 组件使用，也可以在其他组件中通过 icon 属性引用。

### 引入

在 Taro 文件中引入组件

```js
import { Icon } from "@antmjs/vantui"; 
```

## 代码演示

### 基础用法

`Icon`的`name`属性支持传入图标名称或图片链接。

```jsx
<View>
  <Icon name="close" />
  <Icon name="https://b.yzcdn.cn/vant/iconDemo-1126.png" />
</View>
 
```

### 提示信息

设置`dot`属性后，会在图标右上角展示一个小红点。设置`info`属性后，会在图标右上角展示相应的徽标。

```jsx
<View>
  <Icon
    name="chat"
    dot={ true }
  />
  <Icon
    name="chat"
    info="9"
  />
  <Icon
    name="chat"
    info="99+"
  />
</View>
 
```

### 图标颜色

设置`color`属性来控制图标颜色。

```jsx
<View>
  <Icon
    name="chat"
    color="red"
  />
</View>
 
```

### 图标大小

设置`size`属性来控制图标大小。

```jsx
<View>
  <Icon
    name="chat"
    size="50px"
  />
</View>
 
```

### 自定义图标

如果需要在现有 Icon 的基础上使用更多图标，可以引入第三方 iconfont 对应的字体文件和 CSS 文件，之后就可以在 Icon 组件中直接使用。例如，可以在 `app.wxss` 文件中引入。

```css
/* 引入第三方或自定义的字体图标样式 */
@fontFace {
  fontFamily: 'myIcon';
  src: url('./myIcon.ttf') format('truetype');
}

.myIcon {
  fontFamily: 'myIcon';
}

.myIconExtra::before {
  content: '\e626';
}
```

```jsx
<View>
  {/*  通过 classPrefix 指定类名为 myIcon  */}
  <Icon
    classPrefix="myIcon"
    name="extra"
  />
</View>
 
```
### IconProps [[详情]](https://github.com/AntmJS/vantui/tree/main/packages/vantui/types/icon.d.ts)   

| 参数 | 说明 | 类型 | 默认值 | 必填 |
| --- | --- | --- | --- | --- |
| dot | 是否显示图标右上角小红点 | _&nbsp;&nbsp;boolean<br/>_ | - | `false` |
| info | 图标右上角文字提示 | _&nbsp;&nbsp;number&nbsp;&brvbar;&nbsp;string<br/>_ | false | `false` |
| size | 图标大小，如 20px，单位为px | _&nbsp;&nbsp;number&nbsp;&brvbar;&nbsp;string<br/>_ | - | `false` |
| color | 图标颜色 | _&nbsp;&nbsp;string<br/>_ | - | `false` |
| style | 自定义样式 | _&nbsp;&nbsp;string<br/>_ | - | `false` |
| classPrefix | 类名前缀 | _&nbsp;&nbsp;string<br/>_ | vant-icon | `false` |
| name | 图标名称或图片链接 | _&nbsp;&nbsp;string<br/>_ | - | `false` |


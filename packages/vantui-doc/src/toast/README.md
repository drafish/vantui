# Toast 轻提示

### 介绍

在页面中间弹出黑色半透明提示，用于消息通知、加载提示、操作结果提示等场景。

### 引入

在 Taro 文件中引入组件

```js
import { Toast } from "@antmjs/vantui"; 
```

## 代码演示

### 文字提示

须要在JSX里面申明后，才能用命令式调用

```javascript
import { Toast } from 'vantui';

Toast.show('我是提示文案，建议不超过十五字~');
```

```jsx
<View>
  <Toast id="vanToast" />
</View>
 
```

### 加载提示

使用 `Toast.loading` 方法展示加载提示，通过 `forbidClick` 属性可以禁用背景点击，通过 `loadingType` 属性可以自定义加载图标类型。

```javascript
Toast.loading({
  message: '加载中...',
  forbidClick: true,
});

// 自定义加载图标
Toast.loading({
  message: '加载中...',
  forbidClick: true,
  loadingType: 'spinner',
});
```

### 成功/失败提示

```javascript
Toast.success('成功文案');
Toast.fail('失败文案');
```

### 动态更新提示

```javascript
const toast = Toast.loading({
  duration: 0, // 持续展示 toast
  forbidClick: true,
  message: '倒计时 3 秒',
  selector: '#customSelector',
});

let second = 3;
const timer = setInterval(() => {
  second--;
  if (second) {
    toast.setData({
      message: `倒计时 ${second} 秒`,
    });
  } else {
    clearInterval(timer);
    Toast.clear();
  }
}, 1000);
```

```jsx
<View>
  <Toast id="customSelector" />
</View>
 
```

### OnClose 回调函数

```javascript
Toast.show({
  type: 'success',
  message: '提交成功',
  onClose: () => {
    console.log('执行OnClose函数');
  },
});
```
### ToastProps [[详情]](https://github.com/AntmJS/vantui/tree/main/packages/vantui/types/toast.d.ts)   

| 参数 | 说明 | 类型 | 默认值 | 必填 |
| --- | --- | --- | --- | --- |
| zIndex | 弹出层的层级 | _&nbsp;&nbsp;number<br/>_ | 1000 | `false` |
| duration | 展示时长(ms)，值为 0 时，toast 不会消失 | _&nbsp;&nbsp;number<br/>_ | 2000 | `false` |
| mask | 是否有蒙层 | _&nbsp;&nbsp;boolean<br/>_ | false | `false` |
| forbidClick | 是否禁止背景点击 | _&nbsp;&nbsp;boolean<br/>_ | false | `false` |
| type | 提示类型 | _&nbsp;&nbsp;attr:<br/>&nbsp;&nbsp;&nbsp;&nbsp;&brvbar;&nbsp;"loading"<br/>&nbsp;&nbsp;&nbsp;&nbsp;&brvbar;&nbsp;"success"<br/>&nbsp;&nbsp;&nbsp;&nbsp;&brvbar;&nbsp;"fail"<br/>&nbsp;&nbsp;&nbsp;&nbsp;&brvbar;&nbsp;"html"<br/>&nbsp;&nbsp;&nbsp;&nbsp;&brvbar;&nbsp;"text"<br/>_ | text | `false` |
| position | 展示位置 | _&nbsp;&nbsp;"top"&nbsp;&brvbar;&nbsp;"middle"&nbsp;&brvbar;&nbsp;"bottom"<br/>_ | middle | `false` |
| message | 内容 | _&nbsp;&nbsp;string&nbsp;&brvbar;&nbsp;ReactNode<br/>_ | - | `false` |
| loadingType | 加载图标类型 | _&nbsp;&nbsp;"circular"&nbsp;&brvbar;&nbsp;"spinner"&nbsp;&brvbar;&nbsp;undefined<br/>_ | spinner | `false` |
| selector | 自定义选择器, 对应元素id | _&nbsp;&nbsp;string<br/>_ | van-toast | `false` |
| id | 设置id,配合selector使用 | _&nbsp;&nbsp;string<br/>_ | - | `false` |
| children | - | _&nbsp;&nbsp;ReactNode<br/>_ | - | `false` |
| onClose | 关闭时的回调函数 | _&nbsp;&nbsp;()&nbsp;=>&nbsp;any<br/>_ | - | `false` |

### Toast下命令式调用方法 [[详情]](https://github.com/AntmJS/vantui/tree/main/packages/vantui/types/toast.d.ts)   
调用方式传入ToastProps或者ToastProps.message执行
| 参数 | 说明 | 类型 | 默认值 | 必填 |
| --- | --- | --- | --- | --- |
| show | - | _&nbsp;&nbsp;(options:&nbsp;ToastProps&nbsp;&brvbar;&nbsp;string)&nbsp;=>&nbsp;any<br/>_ | - | `true` |
| loading | - | _&nbsp;&nbsp;(options:&nbsp;ToastProps&nbsp;&brvbar;&nbsp;string)&nbsp;=>&nbsp;any<br/>_ | - | `true` |
| success | - | _&nbsp;&nbsp;(options:&nbsp;ToastProps&nbsp;&brvbar;&nbsp;string)&nbsp;=>&nbsp;any<br/>_ | - | `true` |
| fail | - | _&nbsp;&nbsp;(options:&nbsp;ToastProps&nbsp;&brvbar;&nbsp;string)&nbsp;=>&nbsp;any<br/>_ | - | `true` |
| clear | - | _&nbsp;&nbsp;(options?:&nbsp;ToastProps)&nbsp;=>&nbsp;void<br/>_ | - | `true` |
| setDefaultOptions | - | _&nbsp;&nbsp;(options:&nbsp;ToastProps)&nbsp;=>&nbsp;void<br/>_ | - | `true` |
| resetDefaultOptions | - | _&nbsp;&nbsp;(options:&nbsp;any)&nbsp;=>&nbsp;void<br/>_ | - | `true` |


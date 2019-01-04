# wx-miniprogram-actionsheet
微信小程序自定义组件——底部菜单ActionSheet

[![](https://img.shields.io/npm/dm/wx-miniprogram-actionsheet.svg?style=popout)](https://www.npmjs.com/package/wx-miniprogram-actionsheet)[![](https://img.shields.io/badge/dynamic/json.svg?label=version&url=https%3A%2F%2Fraw.githubusercontent.com%2FJaimeCheng%2Fwx-miniprogram-actionsheet%2Fmaster%2Fpackage.json&query=version&colorB=blue&prefix=%20&suffix=%20)](https://www.npmjs.com/package/wx-miniprogram-actionsheet)

**写这个自定义ActionSheet组件，和自定义modal一样，有些开放能力必须绑定在button上，而我们有时候又会有在底部上拉菜单中实现转发功能的需求，或者别的微信开放能力，小程序原生的ActionSheet依然无法实现，故此组件应运而生。**

## 安装
#### 1.使用npm安装
直接使用小程序开发工具自带的[```构建npm```](https://developers.weixin.qq.com/miniprogram/dev/devtools/npm.html)，请按下面几个步骤引入：
- 确保项目目录下有package.json文件，已有的跳过这一步
``` bash
$ npm init
```
- 安装
``` bash
$ npm i wx-miniprogram-actionsheet
```
- 在小程序开发者工具中依次找到并点击`工具`->`构建npm`，构建完成后你的项目目录会多出一个`miniprogram_npm`目录，请确保项目设置已勾选`使用npm模块`

- 在使用组件的页面配置json中使用
```js
{
  "usingComponents": {
    "action-sheet": "wx-miniprogram-actionsheet"
  }
}
```
#### 2.不使用任何构建工具的普通小程序安装
直接拷贝[wx-miniprogram-actionsheet](https://github.com/JaimeCheng/wx-miniprogram-actionsheet)仓库中的`miniprogram_dist`目录下的代码到项目中的放组件的目录中去，之后使用方法和小程序自定义组件一样了。同样需要在页面配置json中声明：
```js
{
  "usingComponents": {
    "action-sheet": "../components/mysheet/index"
  }
}
```

## 使用
**wxml文件中**

```html
<action-sheet actionShow="{{showStatus}}" closeText="关闭" bind:actionHide="onActionHide">
  <!-- slot ActionSheet 菜单项 只能是button 或 navigator -->
  <navigator url="/pages/index/index">我是navigator: 回首页</navigator>
  <button bindtap="handleBtn">我是普通按钮</button>
  <button open-type="share">开放能力: 转发</button>
</action-sheet>
```
**js文件中**

```js
// 只列出核心代码
Page({
  data: {
    actionStatus: false
  },
  onActionHide: function () {
    console.log('ActionSheet关闭了')
  }
})
```
菜单项写进`<action-sheet></action-sheet>`标签里即可，菜单项 只能是button 或 navigator。
![action-sheet效果](https://upload-images.jianshu.io/upload_images/3981371-d235e85bfb9cf211.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 参数
|    属性    | 数据类型 |        说明        | 选项 | 默认值 |
| :--------: | :------: | :----------------: | :--: | :----: |
| actionShow | Boolean  | 组件的初始显隐状态 | 必填 |   —    |
| closeText  |  String  |   取消按钮的文字   | 选填 |  取消  |
## 触发事件

| eventName  |                             说明                             |
| :--------: | :----------------------------------------------------------: |
| actionHide | action-sheet组件被关闭时触发的事件，除了点关闭按钮会触发外，点其他按钮都会关闭组件，都会触发该事件，按需使用 |

## 示例Demo
[微信小程序自定义组件使用示例整合](https://github.com/JaimeCheng/weapp-components)
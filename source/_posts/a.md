---
title: 修改weui组件库的样式
date: 2021-12-02 10:04:46
tags: 小程序
---
## 背景

本文介绍如何修改weui组件库的样式。这里拿修改button的样式为例， 用一种侵入性低的方式，达到设计稿想要的效果。

## 案例

### 问题
![issue](/images/default-weui-button.png "默认button效果图")
```bash
<!--pages/nativeLogin/native_login.wxml-->
<view class="remote-login-containier">
        <button type="primary" open-type="getPhoneNumber" bindgetphonenumber="bindLoginButtonTap">微信一键登录</button>
</view> 
```
我们可以发现，weui的button背景是绿色，样式的风格和微信APP一致。这里我们需要把这个样式替换成我们自己的设计稿做的。
### 添加自定义class属性
第一步， 在button标签中，class属性设置为我们自定义样式“tn-button”，则可以修改weui其原有的样式。如果想回退成weuid的默认样式，则声明button标签时，不写这个class属性即可。
```bash
<view class="remote-login-containier">
        <button class="tn-button" type="primary" open-type="getPhoneNumber" bindgetphonenumber="bindLoginButtonTap">微信一键登录</button> 
</view>
```
### tn-button 文本居中样式
第二步，利用flex布局，定义一个文本居中的button样式。并设置设计稿对应的圆角和背景色。
```bash
.tn-button {
  display: flex; //button内的文本设置成弹性布局
  flex-direction: column; //文本垂直布局方向
  justify-content: center;//文本垂直居中
  height: 128rpx;
  width: 578rpx;
  font-family: PingFang SC;
  font-style: normal;
  font-weight: normal;
  font-size: large;
  /* Applet/type_highlight */
  background: linear-gradient(180deg, #9A8979 0%, #9A8979 100%);
  border-radius: 128rpx;
}
```
### 最终效果
![result](/images/final-weui-button.png "修改样式后的效果图")

## 总结
在标签button中，直接引用自定义的wxss样式，就可以覆盖原有的样式。

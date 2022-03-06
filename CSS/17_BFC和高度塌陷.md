### BFC (Block formatting context)

BFC是 CSS中隐含的属性

开启BFC 以后，该元素会变成一个独立的布局区域

1.  开启BFC的元素不会被浮动元素所覆盖
2.  启BFC的元素，子元素和父元素外边距不会重叠
3.  开启BFC的元素，可以包含浮动子元素，避免高度塌陷

<br>

**开启BFC的方式：**

1. float浮动
2. overflow: 非visible
3. 设置元素绝对定位 position: absolute;
4. 设置元素display为inline-block

<br>

### 高度塌陷

父元素高度默认被子元素撑开

当子元素设置浮动后，其脱离文档流，会导致无法撑起父元素，父元素高度丢失
  
# 超链接  
1.HTML 超链接<a>标签跳转笔记
核心属性：
href：指定跳转的目标链接（必填）
target：控制链接打开方式
target常用取值及效果：
不写target / target="_self"
效果：在当前标签页打开跳转页面（默认行为）
target="_blank"
效果：在新标签页 / 新窗口打开跳转页面
代码示例说明：
html
<a href="https://github.com/dashboard" target="_blank">去GitHub</a>
点击后会在新标签页打开 GitHub 页面
2.锚点的作用
在同一个页面内，点击一个链接，直接跳到页面里的某个内容位置（比如点 “目录 1” 跳转到 “第一章内容”）

锚点写法
目标位置加 id="名"
跳转链接写 <a href="#名">点我跳</a>
<!-- 跳转链接 -->
<a href="#internet">跳互联网原理</a>
<a href="#brain">跳脑图</a>

<!-- 目标位置（加id） -->
<p id="internet">互联网原理</p>
<p id="brain">脑图</p>

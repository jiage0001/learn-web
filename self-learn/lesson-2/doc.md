# 超链接  
HTML 超链接<a>标签跳转笔记
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
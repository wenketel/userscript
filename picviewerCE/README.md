picviewerCE.user.js
===================

[picViewer By NLF](http://userscripts-mirror.org/scripts/show/105741) 修改版。[直接安装地址](https://github.com/ywzhaiqi/userscript/raw/master/picviewerCE/picviewerCE.user.js)

## 修改说明

- 修改了默认的设置
    - 修改为**双击**关闭图片窗口，还可用 esc 键关闭。
- 新增了几个查看大图的站点规则
- 新增了几个库的命令
    - 重载。跟下面的自动重载类同，这是手动重载。
    - `导出所有图片到新窗口`
    - 显示隐藏底部条
- ~~新增库浏览时，当滚动到最后一个，会自动滚动原页面到最底部，如果有新的图片会自动重载。例如百度图片库浏览时。~~ 已被默认禁用，有待进一步完善。

## 鼠标手势调用（FireGesture）

### 打开原图

    var srcNode = window.FireGestures ? FireGestures.sourceNode : event.target,
        document = srcNode.ownerDocument;

    var actualBtn = document.querySelector('#pv-float-bar-container > .pv-float-bar-button-actual');
    if (actualBtn) {
        actualBtn.click();
    }

### 打开库

    var srcNode = window.FireGestures ? FireGestures.sourceNode : event.target,
        document = srcNode.ownerDocument;

    var galleryBtn = document.querySelector('#pv-float-bar-container > .pv-float-bar-button-gallery');
    if (galleryBtn) {
        galleryBtn.click();
    }

### chrome 的鼠标手势实现

思路：使用外部鼠标手势软件调用按键执行 js 代码。

步骤

1. 先用 [Shortcut Manager](https://chrome.google.com/webstore/detail/mgjjeipcdnnjhgodgjpfkffcejoljijf) 定义 2 个按键。js 代码要舍弃前 2 行，例如：
    ![chrome_shortkey_manager_1](img/chrome_shortkey_manager_1.png)
2. 然后用 WGestures 或 StrokeIt 或 StrokesPlus 等软件发送按键。
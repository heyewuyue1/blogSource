---
title: 在Electron中使用IPC广播实现主进程和渲染进程的通信
date: 2021-10-18 08:20:43
tags:
 - Electron
---
- 要实现一个主页面和子页面来回跳转的功能，试图使用`mainWindow.loadFIle()`来加载子页面。但是这是主进程才能进行的操作，于是需要在渲染进程里当需要跳转的时候就广播出一个信号，当主进程监听到这个信号，就开始`loadFile()`。
# 代码实现
1. 在主进程中和渲染进程中加入`ipcMain`和`ipcRenderer`。
    - 在`main.js`中
    ```javascript
    var {ipcMain} = require('electron')
    ```
    - 在`index.js`和`dataset.js`中
    ```javascript
    var {ipcRenderer} = require('electron')
    ```
2. 在渲染进程中定义每次返回，跳转时需要发出信号的函数。
    - 在`index.js`中
    ```javascript
    function newPage(){
        ipcRenderer.send('openDatasetPage');
    }
    ```
    - 在`dataset.js`中
    ```javascript
    function backToMain(){
        ipcRenderer.send('comeBackToMain')
    }
    ```
3. 在主进程中定义接收到信号之后的行为。
    - 在`main.js`中
    ```javascript
    ipcMain.on('openDatasetPage', ()=>{
        mainWindow.loadFile('./dataset.html');
    })

    ipcMain.on('comeBackToMain', ()=>{
        mainWindow.loadFile('./index.html')
    })
    ```
4. 在HTML文件中把按钮和功能联系起来。
    - 在`index.html`中
    ```html
    <a class="more" href="#" onclick="showWindow()">
    更多...
    </a>
    ```
    - 在`dataset.html`中
    ```html
        <a href="#" onclick="backToMain()" class="backButton">
        <img src="image/返回.png" class="backImage" />
        </a>
    ```

<script src="//unpkg.com/valine/dist/Valine.min.js"></script>
<div id="vcomments"></div>
<script>
    new Valine({
        el: '#vcomments',
        appId: 'pYVxUdjGaaE4WkIo9yulsMpw-gzGzoHsz',
        appKey: 'k5IXm5eqTCqoajlqYcc8F39c'
    })
</script>
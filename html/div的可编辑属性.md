#### 用div实现input输入框效果
``` html
<div id="edit-box" contenteditable="true"></div>
<button onclick="getText()">获取自定义输入框内容</button>
//给div盒子加上contenteditable="true"时，可实现div的编辑
```
但是想获得输入框的内容，我想到了innerHTML；
``` js
function getText(){
    const edit = document.querySelector('#edit-box');
    console.log(edit.innerHTML);
}
```
使用innerHTML也确实是达到了获取内容的效果，但是获取它需要
一个按钮操作，并不能实时获取，所以暂时先放弃。我就在想input
有change、input等事件，那么可编辑div呢？尝试一下。
``` html
<div id="edit-box" contenteditable="true" oninput="getText()"></div>
<script>
    function getText(){
        const edit = document.querySelector('#edit-box');
        console.log(edit.innerHTML);
    }
</script>
```
此时不需要按钮也能获取，实现了随时获取，但是还能不能更精简呢？
答案肯定是有，上面我们需要一遍遍的获取节点，能不能传个参数呢？
尝试一下
```html
<div id="edit-box" contenteditable="true" oninput="getText(event)"></div>
<script>
    function getText(e){
        console.log(e);
    }
</script>
```
控制台打印出来的结果如图
![An image](/可编辑div控制台输出.png)
此时就成功地实现了div实现input效果

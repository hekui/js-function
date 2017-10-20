# 图片本地预览

使用了HTML5的 `FileReader()` 方法，[详细介绍](https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader)
> 注: IE10以下的版本不支持FileReader()构造函数.不过可以利用滤镜来兼容旧版本的IE:[兼容IE的图片本地预览](https://mdn.mozillademos.org/files/3699/crossbrowser_image_preview.html).


demo实例，[在线预览](http://runjs.cn/detail/h3ctof1l)

```html
<input type="file" id="File">
<div class="img">
  <img alt="img preview" id="ImgPreview" width="200" height="200" />
</div>
```
```javascript
function previewImg({file, preview}){
	var reader = new FileReader();
	reader.addEventListener('load', function(){
		preview.src = reader.result
	}, false)
	reader.readAsDataURL(file)
}

document.getElementById('File').addEventListener('change', function(e){
	var preview = document.getElementById('ImgPreview')
	var file = this.files[0]
	previewImg({
		file, preview
	})
}, false)
```
```css
.img{
	width: 200px;
	height: 200px;
	border: 1px solid #ddd;
	border-radius: 3px;
	background-color: #f3f3f3;
	margin-top: 10px;
}
```
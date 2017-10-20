# 图片本地预览

demo: [在线预览](http://runjs.cn/detail/h3ctof1l)

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
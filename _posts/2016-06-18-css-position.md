---
layout: post
title: position的值及区别
date: 2016-06-18
tags: [CSS]
---
* auto-gen TOC:
{:toc}

### Static
这个是元素的默认定位方式，元素出现在正常的文档流中，会占用页面空间。不能使用top，bottom，left，right和z-index。

### Relative
相对定位方式，相对于其父级元素（无论父级元素此时为何种定位方式）进行定位，准确地说是相对于其父级元素所剩余的未被占用的空间进行定位（在父元素由多个相对定位的子元素时可以看出），且会占用该元素在文档中初始的页面空间，即在使用top，bottom，left，right进行移动位置之后依旧不会改变其所占用空间的位置。可以使用z-index进行在z轴方向上的移动。

### Absolute
绝对定位方式，脱离文档流，不会占用页面空间。以最近的不是static定位的父级元素作为参考进行定位，如果其所有的父级元素都是static定位，那么此元素最终则是以当前窗口作为参考进行定位。可以使用top，bottom，left，right进行位置移动，亦可使用z-index在z轴上面进行移动。当元素为此定位时，如果该元素为内联元素，则会变为块级元素，即可以直接设置其宽和高的值；如果该元素为块级元素，则其宽度会由初始的100%变为auto。

注意：当元素设置为绝对定位时，在没有指定top，bottom，left，right的值时，他们的值并不是0，这几个值是有默认值的，默认值就是该元素设置为绝对定位前所处的正常文档流中的位置。（可能我没有描述的很清楚，建议自己写个示例看看效果）

### Fixed
绝对定位方式，直接以浏览器窗口作为参考进行定位。其它特性同absolute定位。

小结论：

1. 对于使用position:relative的子类元素而言，width:100%也始终是基于基父级元素而并不会基于其上层元素中的relative。
2. 对于绝对定位的子无素，要是其外层的所有元素中都没有用position:relative，则width:100%是基于body，否则就是离基最近的一个position:relative的元素。
3. 对于position:fixed的元素，其一直是基于body,所以其宽度100%就是基于body。

<html>
<style>
	.home{
		background: red;
		height: 350px;
		width: 500px;
	}
	
	.parent{
		width: 100%;
		background: blue;
		height: 100px;
		padding: 10px;
		margin: 10px;
		border: 5px solid;
		position: relative;
	}
	
	.child{
		width: 100%;
		background: grey;
		height: 50%;
		position: absolute;
	}
</style>

<body>
	<div class="top">
		<div class="home">home
			<div class="parent">parent
				<div class="child">child</div>
			</div>
		</div>
	</div>
</body>
</html>

# test1
<style>
* {
	box-sizing: border-box;
}
body {
	background: red;
}
.layer0 {
	--layer0-width: 1440px;
	background: blue;
	overflow: show;
	margin: 0 auto;
	width: var(--layer0-width);
}
.layer1 {
	--layer1-width: 2000px;
	background-image: url(bg.jpg);
	width: var(--layer1-width);
	height: 1000px;
	position: relative;
	left: calc(
		/* 親が中寄せにされている位置を基準に、相対位置としてブラウザの左端を計算 */
		((100vw - var(--layer0-width)) / -2)
		/* そこから、この要素を中央寄せにする */
		+ ((100vw - var(--layer1-width)) / 2)
		);
}
</style>

<body>
	<div class="layer0">
		前景物
		<div class="layer1">
			前景物2
		</div>
	</div>
</body>

# test2

<style>
/* 背景に1440pxを超える幅の背景を敷き、レスポンシブする */
.bg-layer {
	--bg-offset: -200px;				/* 背景の開始位置を左右にシフトする量 */
	--contents-layer-width: 1440px;		/* コンテンツが流し込まれるエリアの幅 */
	background: no-repeat url(bg.jpg);
	background-position: calc( (100vw - var(--contents-layer-width)) / 2 + var(--bg-offset)) 0;
	width: 100%;
	height: 100%;
}
.contents-layer {
	margin: 0 auto;
	width: var(--contents-layer-width);
}

.contents-layer {
	background: blue;
	padding: 2rem;
}
</style>

<body>
	<div class="bg-layer">
		<div class="contents-layer">
			<h1>背景に1440pxを超える幅の背景を敷き、レスポンシブする</h1>
		</div>
	</div>
</body>


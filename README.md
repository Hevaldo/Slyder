# Slyder
SlyderShow
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title>SlideShow</title>
	<link rel="stylesheet" href="style.css"/>
</head>
<body>
	<header>
		<div class="header"></div>
		<div class="slider">
			<div class="slider--controls">
				<div class="slider--control" onclick="goPrev()">voltar</div>
				<div class="slider--control" onclick="goNext()">próxima</div>
			</div>
			<div class="slider--width">
				<div class="slider--item" style="background-image: url('fotos1.jpg');">Paisagem - 01</div>
				<div class="slider--item" style="background-image: url('fotos2.jpg');">Paisagem - 02</div>
				<div class="slider--item" style="background-image: url('fotos3.jpg');">Paisagem - 03</div>
				<div class="slider--item" style="background-image: url('fotos4.jpg');">Paisagem - 04</div>
				<div class="slider--item" style="background-image: url('fotos5.jpg');">Paisagem - 05</div>
				<div class="slider--item" style="background-image: url('fotos6.jpg');">Paisagem - 06</div>
            </div>
		</div>
	</header>
	<section>
		<h1>Final do site</h1>
	</section> 


    <script src="script.js"></script>
</body>
</html>

 * {
 	box-sizing: border-box;
 }
 body {
 	margin: 0;
 }
 header {
 	margin: 0;
 	display: flex;
 	flex-direction: column;
 	height: 100vh;
 	background-color: #ccc;
 }
 .header {
 	height: 50px;
 	background-color: #333;
 }
 .slider {
 	flex: 1;
 	overflow: hidden;
 }
 .slider--width {
 	height: 100%;
 	display: flex;
 	transition: all ease 0.3s;
 }
 .slider--item {
 	width: 100vw;
 	height: inherit;
 	background-position: center;
 	background-size: cover;
 	display: flex;
 	justify-content: center;
 	align-items: height;
 	color: #fff;
 	text-shadow: 0px 1px 1px #333;
 	font-size: 30px;
 }
 .slider--controls {
 	position: absolute;
 	z-index: 99;
 	width: 100%;
 	display: flex;
 	justify-content: space-between;
 	align-items: center;
 	display: flex;
 	color: #fff;
 	text-shadow: 0px 1px 1px #333;
 	font-size: 15px;
 }
 .slider--control {
 	width: 60px;
 	height: 20px;
 	background-color: #333;
 	border-left: 5px solid transparent;
    border-right: 5px solid transparent;
 	overflow: hidden;
 	cursor: pointer;
 }
 
 let totalSlides = document.querySelectorAll('.slider--item').length;
let currentSlide = 0;

document.querySelector('.slider--width').style.width = `calc(100vw * ${totalSlides})`;
document.querySelector('.slider--controls').style.height = `${document.querySelector('.slider').clientHeight}px`;

function goPrev() {
    currentSlide--;
    if(currentSlide < 0) {
	    currentSlide = totalSlides - 1;
    }
    updateMargin();
}
function goNext() {
	currentSlide++;
	if(currentSlide > (totalSlides - 1)) {
		currentSlide = 0;
	}
	updateMargin();

}

function updateMargin() {
	let sliderItemWidth = document.querySelector('.slider--item').clientWidth;
	let newMargin = (currentSlide * sliderItemWidth);
	document.querySelector('.slider--width').style.marginLeft = `-${newMargin}px`;

}

setInterval(goNext,5000);

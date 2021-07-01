---
layout: None
title: Projects
---
<html>
<head>
	<title>Circles</title>
	<!-- SCRIPT A: PREVENTS FOUC -->
	<script type="text/javascript">
    var elm=document.getElementsByTagName("html")[0];
    elm.style.display="none";
    document.addEventListener("DOMContentLoaded",function(event) { elm.style.display="block"; });
	</script>
	<!-- SCRIPT A -->
	<script type="text/javascript" src="{{ site.url }}/js/paper-full.js"></script>
	<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/howler/2.0.12/howler.js"></script>
	<link rel="stylesheet" type="text/css" href="{{ site.url }}/stylesheets/circles.css">
</head>
<body>
	<script type="text/paperscript" canvas="myCanvas">

	var keyData = {

	q: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/bubbles.mp3']
	}),
	color: '#1abc9c'
	},
	w: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/clay.mp3']
	}),
	color: '#2ecc71'
	},
	e: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/confetti.mp3']
	}),
	color: '#3498db'
	},
	r: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/corona.mp3']
	}),
	color: '#9b59b6'
	},
	t: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/dotted-spiral.mp3']
	}),
	color: '#34495e'
	},
	y: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/flash-1.mp3']
	}),
	color: '#16a085'
	},
	u: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/flash-2.mp3']
	}),
	color: '#27ae60'
	},
	i: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/flash-3.mp3']
	}),
	color: '#2980b9'
	},
	o: {
	sound: new Howl({
	src: ['{{ site.url }}/sounds/glimmer.mp3']
	}),
	color: '#8e44ad'
	},
	p: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/moon.mp3']
	}),
	color: '#2c3e50'
	},
	a: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/pinwheel.mp3']
	}),
	color: '#f1c40f'
	},
	s: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/piston-1.mp3']
	}),
	color: '#e67e22'
	},
	d: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/piston-2.mp3']
	}),
	color: '#e74c3c'
	},
	f: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/prism-1.mp3']
	}),
	color: '#95a5a6'
	},
	g: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/prism-2.mp3']
	}),
	color: '#f39c12'
	},
	h: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/prism-3.mp3']
	}),
	color: '#d35400'
	},
	j: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/splits.mp3']
	}),
	color: '#1abc9c'
	},
	k: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/squiggle.mp3']
	}),
	color: '#2ecc71'
	},
	l: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/strike.mp3']
	}),
	color: '#3498db'
	},
	z: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/suspension.mp3']
	}),
	color: '#9b59b6'
	},
	x: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/timer.mp3']
	}),
	color: '#34495e'
	},
	c: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/ufo.mp3']
	}),
	color: '#16a085'
	},
	v: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/veil.mp3']
	}),
	color: '#27ae60'
	},
	b: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/wipe.mp3']
	}),
	color: '#2980b9'
	},
	n: {
	sound: new Howl({
	src: ['{{ site.url }}/sounds/zig-zag.mp3']
	}),
	color: '#8e44ad'
	},
	m: {
	sound: new Howl({
	  src: ['{{ site.url }}/sounds/moon.mp3']
	}),
	color: '#2c3e50'
	}
	}




	var circles = [];
	function onKeyDown(event) {
		if(keyData[event.key]){
		var maxPoint = new Point(view.size.width, view.size.height);
		var randomPoint = Point.random();
		var point = maxPoint * randomPoint;
		var newCircle = new Path.Circle(point, 500)
		newCircle.fillColor = keyData[event.key].color
		keyData[event.key].sound.play();
		circles.push(newCircle);
		}
	}

	function onFrame(event){
		for(var i = 0; i < circles.length; i++){
			circles[i].scale(.93);
			circles[i].fillColor.hue += 3;
			if(circles[i].area < 1){
				circles[i].remove();
				circles.splice(i, 1);
				i--;
				console.log(circles);
			}
		}
	}
	

</script>
  <div class="btn_container">
    <a class="open_button" href="#">Get Started!</a>
  </div>
  <div class="modal_info" id="myModal">
    <h1>How To Play</h1>
    <p>Every character on your keyboard(A ~ Z) corresponds to a sound. Have fun making music!</p>
  </div>
  <div class="modal_overlay">
  </div>
  <div class="btn_container">
    <a class="github_link" href="https://github.com/khairulslt">GitHub</a>
  </div>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.js"></script>
<script type="text/javascript" src="{{ site.url }}/js/circles.js"></script>
<canvas id="myCanvas" resize></canvas>
</body>
</html>
#Software #Hacking #WebExplotation #Web #Internet 
# Definición
The flag is somewhere on this web application not necessarily on the website. Find it.Check [this](http://saturn.picoctf.net:58814/) out.
# Hints
(None)
# Solución
Al entrar lo primero que hacemos en inspeccionar la página pero no tenemos suerte encontrando la bandera.
```bash
|   |   |
|---|---|
||<!DOCTYPE html>|
||<html lang="en">|
|||
||<head>|
||<!-- basic -->|
||<meta charset="utf-8">|
||<meta http-equiv="X-UA-Compatible" content="IE=edge">|
||<!-- mobile metas -->|
||<meta name="viewport" content="width=device-width, initial-scale=1">|
||<meta name="viewport" content="initial-scale=1, maximum-scale=1">|
||<!-- site metas -->|
||<title>flexed</title>|
||<meta name="keywords" content="">|
||<meta name="description" content="">|
||<meta name="author" content="">|
||<!-- bootstrap css -->|
||<link rel="stylesheet" href="[css/bootstrap.min.css](http://saturn.picoctf.net:58814/css/bootstrap.min.css)">|
||<!-- owl css -->|
||<link rel="stylesheet" href="[css/owl.carousel.min.css](http://saturn.picoctf.net:58814/css/owl.carousel.min.css)">|
||<!-- style css -->|
||<link rel="stylesheet" href="[css/style.css](http://saturn.picoctf.net:58814/css/style.css)">|
||<!-- responsive-->|
||<link rel="stylesheet" href="[css/responsive.css](http://saturn.picoctf.net:58814/css/responsive.css)">|
||<!-- awesome fontfamily -->|
||<link rel="stylesheet" href="[https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css](https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css)">|
||<!--[if lt IE 9]>|
||<script src="https://oss.maxcdn.com/html5shiv/3.7.3/html5shiv.min.js"></script>|
||<script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script><![endif]-->|
||</head>|
||<!-- body -->|
|||
||<body class="main-layout">|
||<!-- loader -->|
||<div class="loader_bg">|
||<div class="loader"><img src="[images/loading.gif](http://saturn.picoctf.net:58814/images/loading.gif)" alt="" /></div>|
||</div>|
|||
||<div class="wrapper">|
||<!-- end loader -->|
|||
||<div id="content">|
||<!-- header -->|
||<header>|
||<!-- header inner -->|
||<div class="head-top">|
||<div class="container">|
|||
||<div class="row">|
||<div class="col-xl-4 col-lg-4 col-md-4 col-sm-4">|
||<div class="email">|
||<a href="[#](http://saturn.picoctf.net:58814/#)"><img src="[images/mail_icon.png](http://saturn.picoctf.net:58814/images/mail_icon.png)" /> Email : demo@gmail.com</a>|
||</div>|
||</div>|
||<div class="col-xl-4 col-lg-4 col-md-4 col-sm-4">|
||<div class="logo">|
||<a href="[index.html](http://saturn.picoctf.net:58814/index.html)"><img src="[images/logo.png](http://saturn.picoctf.net:58814/images/logo.png)" /></a>|
||</div>|
||</div>|
||<div class="col-xl-4 col-lg-4 col-md-4 col-sm-4">|
||<div class="contact_nu">|
||<a href="[#](http://saturn.picoctf.net:58814/#)"> <img src="[images/phone_icon.png](http://saturn.picoctf.net:58814/images/phone_icon.png)" /> Contact : +71 71234567</a>|
||</div>|
||</div>|
||</div>|
||</div>|
||</div>|
||<div class="bg">|
||<div class="container">|
||<nav class="navigation navbar-expand-md navbar-dark ">|
|||
||<button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarsExample04" aria-controls="navbarsExample04" aria-expanded="false" aria-label="Toggle navigation">|
||<span class="navbar-toggler-icon"></span>|
||</button>|
|||
||<div class="collapse navbar-collapse" id="navbarsExample04">|
||<ul class="navbar-nav mr-auto">|
||<li class="nav-item active">|
||<a class="nav-link" href="[index.html](http://saturn.picoctf.net:58814/index.html)">Home <span class="sr-only">(current)</span></a>|
||</li>|
||<li class="nav-item">|
||<a class="nav-link" href="[#about](http://saturn.picoctf.net:58814/#about)">About </a>|
||</li>|
||<li class="nav-item">|
||<a class="nav-link" href="[#yoga](http://saturn.picoctf.net:58814/#yoga)"> Yoga</a>|
||</li>|
||<li class="nav-item">|
||<a class="nav-link" href="[#pricing](http://saturn.picoctf.net:58814/#pricing)">Pricing</a>|
||</li>|
||<li class="nav-item">|
||<a class="nav-link" href="[#online](http://saturn.picoctf.net:58814/#online)">Yoga Online</a>|
||</li>|
|||
||<li class="nav-item">|
||<a class="nav-link" href="[#contact](http://saturn.picoctf.net:58814/#contact)">Contact us</a>|
||</li>|
|||
||</ul>|
||</div>|
||</nav>|
||</div>|
||</div>|
||<!-- end header inner -->|
||</header>|
||<!-- end header -->|
||<!-- start slider section -->|
||<div class="slider_section banner_main">|
||<div id="myCarousel" class="carousel slide" data-ride="carousel">|
||<ol class="carousel-indicators">|
||<li data-target="#myCarousel" data-slide-to="0" class="active"></li>|
||<li data-target="#myCarousel" data-slide-to="1"></li>|
||<li data-target="#myCarousel" data-slide-to="2"></li>|
||</ol>|
||<div class="carousel-inner">|
||<div class="carousel-item active">|
||<img class="first-slide" src="[images/banner.jpg](http://saturn.picoctf.net:58814/images/banner.jpg)" alt="First slide">|
||<div class="container">|
||<div class="carousel-caption relative">|
||<h1>Gather<br>|
||<strong class="dark_brown">New Body Energy</strong></h1>|
|||
||<a href="[#](http://saturn.picoctf.net:58814/#)">contact us</a>|
||</div>|
||</div>|
||</div>|
||<div class="carousel-item">|
||<img class="second-slide" src="[images/banner.jpg](http://saturn.picoctf.net:58814/images/banner.jpg)" alt="Second slide">|
||<div class="container">|
||<div class="carousel-caption relative">|
||<h1>Gather<br>|
||<strong class="dark_brown">New Body Energy</strong></h1>|
|||
||<a href="[#](http://saturn.picoctf.net:58814/#)">contact us</a>|
||</div>|
||</div>|
||</div>|
||<div class="carousel-item">|
||<img class="third-slide" src="[images/banner.jpg](http://saturn.picoctf.net:58814/images/banner.jpg)" alt="Third slide">|
||<div class="container">|
||<div class="carousel-caption relative">|
||<h1>Gather<br>|
||<strong class="dark_brown">New Body Energy</strong></h1>|
|||
||<a href="[#](http://saturn.picoctf.net:58814/#)">contact us</a>|
||</div>|
||</div>|
||</div>|
||</div>|
||<a class="carousel-control-prev" href="[#myCarousel](http://saturn.picoctf.net:58814/#myCarousel)" role="button" data-slide="prev">|
||<span class="carousel-control-prev-icon" aria-hidden="true"></span>|
||<span class="sr-only">Previous</span>|
||</a>|
||<a class="carousel-control-next" href="[#myCarousel](http://saturn.picoctf.net:58814/#myCarousel)" role="button" data-slide="next">|
||<span class="carousel-control-next-icon" aria-hidden="true"></span>|
||<span class="sr-only">Next</span>|
||</a>|
||</div>|
||</div>|
||<!-- end slider section -->|
|||
||<!-- six_box|
||end six_box The flag is not here but keep digging :)-- >|
|||
||<!-- We Do Yogas -->|
||<div id="yoga" class="weyoga">|
||<div class="container">|
||<div class="row">|
||<div class="col-md-12">|
||<div class="title">|
||<h2>How to <strong class="black"> We Do Yogas</strong></h2>|
||</div>|
||</div>|
||</div>|
||<div class="row">|
||<div class="col-xl-3 col-lg-3 col-md-3 col-sm-12">|
||<div class="yogo_three_box">|
||<figure><img src="[images/1.png](http://saturn.picoctf.net:58814/images/1.png)" alt="#" /></figure>|
||<h3>Ashtanga Yoga</h3>|
||<p>simply dummy text of the printing and typesetting industry. Lorem </p>|
||</div>|
||</div>|
||<div class="col-xl-4 col-lg-4 col-md-4 col-sm-12">|
||<div class="yogo_three_box">|
||<figure><img src="[images/2.png](http://saturn.picoctf.net:58814/images/2.png)" alt="#" /></figure>|
||<h3>Hatha Yoga</h3>|
||<p>simply dummy text of the printing|
||<br>and typesetting industry. Lorem </p>|
||</div>|
||</div>|
||<div class="col-xl-5 col-lg-5 col-md-5 col-sm-12">|
||<div class="yogo_three_box">|
||<figure><img src="[images/3.png](http://saturn.picoctf.net:58814/images/3.png)" alt="#" /></figure>|
||<h3>Kundalini Yoga</h3>|
||<p>simply dummy text of the printing|
||<br>and typesetting industry. Lorem </p>|
||</div>|
||</div>|
||<a class="readmore" href="[#](http://saturn.picoctf.net:58814/#)">Read More</a>|
||</div>|
||</div>|
||</div>|
||<!-- end We Do Yogas -->|
|||
||<!-- footer -->|
||<div id="contact" class="contact">|
||<div class="container">|
||<div class="row">|
||<div class="col-md-12">|
||<div class="title">|
||<h2>Contact<strong class="black"> Us</strong></h2>|
||</div>|
||</div>|
||</div>|
||</div>|
||</div>|
||<div class="container-fluid">|
|||
||<div class="row">|
||<div class="col-xl-6 col-lg-6 col-md-6 col-sm-12 padding">|
|||
||<form class="main_form">|
||<div class="row">|
|||
||<div class="col-xl-12 col-lg-12 col-md-12 col-sm-12">|
||<input class="form-control" placeholder="Name" type="text" name="Name">|
||</div>|
||<div class="col-xl-12 col-lg-12 col-md-12 col-sm-12">|
||<input class="form-control" placeholder="Email" type="text" name="Email">|
||</div>|
||<div class="col-xl-12 col-lg-12 col-md-12 col-sm-12">|
||<input class="form-control" placeholder="Phone" type="text" name="Phone">|
||</div>|
||<div class="col-xl-12 col-lg-12 col-md-12 col-sm-12">|
||<textarea class="textarea" placeholder="Message" type="text" name="Message"></textarea>|
||</div>|
||<div class="col-xl-12 col-lg-12 col-md-12 col-sm-12">|
||<button class="send">Send</button>|
||</div>|
||<div class="col-xl-12 col-lg-12 col-md-12 col-sm-12">|
||<ul class="mail-icon">|
||<li><img src="[images/phone_icon.png](http://saturn.picoctf.net:58814/images/phone_icon.png)" /> (+71) 75896472 (+72) 258963475</li>|
||<li><img src="[images/mail_icon.png](http://saturn.picoctf.net:58814/images/mail_icon.png)" /> Demo@gmail.com</li>|
|||
||</ul>|
||</div>|
||<div class="col-xl-12 col-lg-12 col-md-12 col-sm-12">|
||<ul class="social_icon">|
||<li> <a href="[#](http://saturn.picoctf.net:58814/#)"><i class="fa fa-facebook-f"></i></a></li>|
||<li> <a href="[#](http://saturn.picoctf.net:58814/#)"><i class="fa fa-twitter"></i></a></li>|
||<li> <a href="[#](http://saturn.picoctf.net:58814/#)"><i class="fa fa-instagram"></i></a></li>|
||</ul>|
||</div>|
||</div>|
||</form>|
||</div>|
|||
||<div class="col-xl-6 col-lg-6 col-md-6 col-sm-12 padddd">|
||<div class="map_section">|
||<div id="map">|
||</div>|
||</div>|
||</div>|
||</div>|
||</div>|
||</div>|
|||
||</div>|
||<footer>|
||<div class="footer">|
||<div class="copyright">|
||<div class="container">|
||<div class="row">|
||<div class="col-xl-12 col-lg-12 col-md-12 col-sm-12">|
||<p>© 2019 Flexed Design by<a href="[https://html.design/](https://html.design/)"> Free Html Template</a></p>|
||</div>|
||</div>|
||</div>|
||</div>|
||</div>|
||</footer>|
||<!-- end footer -->|
||</div>|
||</div>|
||<div class="overlay"></div>|
||<!-- Javascript files-->|
||<script src="[js/jquery.min.js](http://saturn.picoctf.net:58814/js/jquery.min.js)"></script>|
||<script src="[js/popper.min.js](http://saturn.picoctf.net:58814/js/popper.min.js)"></script>|
||<script src="[js/bootstrap.bundle.min.js](http://saturn.picoctf.net:58814/js/bootstrap.bundle.min.js)"></script>|
||<script src="[js/owl.carousel.min.js](http://saturn.picoctf.net:58814/js/owl.carousel.min.js)"></script>|
||<script src="[js/custom.js](http://saturn.picoctf.net:58814/js/custom.js)"></script>|
||<script src="[js/jquery.mCustomScrollbar.concat.min.js](http://saturn.picoctf.net:58814/js/jquery.mCustomScrollbar.concat.min.js)"></script>|
|||
||<script src="[js/jquery-3.0.0.min.js](http://saturn.picoctf.net:58814/js/jquery-3.0.0.min.js)"></script>|
||<script type="text/javascript">|
||$(document).ready(function() {|
||$("#sidebar").mCustomScrollbar({|
||theme: "minimal"|
||});|
|||
||$('#dismiss, .overlay').on('click', function() {|
||$('#sidebar').removeClass('active');|
||$('.overlay').removeClass('active');|
||});|
|||
||$('#sidebarCollapse').on('click', function() {|
||$('#sidebar').addClass('active');|
||$('.overlay').addClass('active');|
||$('.collapse.in').toggleClass('in');|
||$('a[aria-expanded=true]').attr('aria-expanded', 'false');|
||});|
||});|
||</script>|
|||
||<script>|
||// This example adds a marker to indicate the position of Bondi Beach in Sydney,|
||// Australia.|
||function initMap() {|
||var map = new google.maps.Map(document.getElementById('map'), {|
||zoom: 11,|
||center: {|
||lat: 40.645037,|
||lng: -73.880224|
||},|
||});|
|||
||var image = 'images/maps-and-flags.png';|
||var beachMarker = new google.maps.Marker({|
||position: {|
||lat: 40.645037,|
||lng: -73.880224|
||},|
||map: map,|
||icon: image|
||});|
||}|
||</script>|
||<!-- google map js -->|
||<script src="[https://maps.googleapis.com/maps/api/js?key=AIzaSyA8eaHt9Dh5H57Zh0xVTqxVdBFCvFMqFjQ&callback=initMap](https://maps.googleapis.com/maps/api/js?key=AIzaSyA8eaHt9Dh5H57Zh0xVTqxVdBFCvFMqFjQ&callback=initMap)"></script>|
||<!-- end google map js -->|
|||
||</body>|
|||
||</html>|
```

Por lo que vemos si [[robots.txt]] nos dice algo.
Y vemos lo siguiente:
```
User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/
```

Lamentablemente esto no nos da una pista clara, pero vemos que esto esta en [[Codificación Base 64]], por lo que nos apoyamos de cyberchef para ver que se esconde.
Y vemos esto:
flag1.txtjs/myfi
js/myfile.txt
²û,²ðzè°¡¡»/u«%z8

Probamos suerte con la primera pero no existe la página, pero al probar con la segunda, encontramos la bandera:
picoCTF{Who_D03sN7_L1k5_90B0T5_032f1c2b}
## Respuesta
picoCTF{Who_D03sN7_L1k5_90B0T5_032f1c2b}
function openNav() {
  document.getElementById("myNav").style.width = "100%";
}

function closeNav() {
  document.getElementById("myNav").style.width = "0%";
}

function openGaleria() {
  document.getElementById("galeria").style.width = "100%";
}

function closeGaleria() {
  document.getElementById("galeria").style.width = "0%";
}

function openModal() {
  document.getElementById("myModal").style.display = "block";
}

function closeModal() {
  document.getElementById("myModal").style.display = "none";
}

function closeFooldal() {
  document.getElementById("myFooldal").style.width = "0%";
}

function openBeker() {
  document.getElementById("mybekerooldal").style.width = "100%";
}

function closeBeker() {
  document.getElementById("mybekerooldal").style.width = "0%";
}

function openContact() {
  document.getElementById("myContact").style.width = "100%";
}

function closeContact() {
  document.getElementById("myContact").style.width = "0%";
}

function imageZoom() {
  document.getElementById("zoom").style.width = "100%";
}

function imageZoom() {
  document.getElementById("zoom").style.width = "0%";
}

var timerID = null;
var timerRunning = false;

function stopclock (){
if(timerRunning)
clearTimeout(timerID);
timerRunning = false;
}
function showtime () {
var now = new Date();
var hours = now.getHours();
var minutes = now.getMinutes();
var seconds = now.getSeconds()
var timeValue = "" + ((hours >24) ? hours -24 :hours)


timeValue = ((timeValue <10)? "0":"") + timeValue
timeValue += ((minutes < 10) ? ":0" : ":") + minutes
timeValue += ((seconds < 10) ? ":0" : ":") + seconds
timeValue += (hours >= 12) ? " pm" : " am"
document.clock.digiora.value = timeValue;
timerID = setTimeout("showtime()",100);
timerRunning = true;
}
function startclock() {
stopclock();
showtime();
}
// óra indítása, az oldal betöltésekor
window.onload = startclock;



var slideIndex = 1;
showSlides(slideIndex);

function plusSlides(n) {
  showSlides(slideIndex += n);
}

function currentSlide(n) {
  showSlides(slideIndex = n);
}

function showSlides(n) {
  var i;
  var slides = document.getElementsByClassName("mySlides");
  var dots = document.getElementsByClassName("demo");
  var captionText = document.getElementById("caption");
  if (n > slides.length) {slideIndex = 1}
  if (n < 1) {slideIndex = slides.length}
  for (i = 0; i < slides.length; i++) {
      slides[i].style.display = "none";
  }
  for (i = 0; i < dots.length; i++) {
      dots[i].className = dots[i].className.replace(" active", "");
  }
  slides[slideIndex-1].style.display = "block";
  dots[slideIndex-1].className += " active";
  captionText.innerHTML = dots[slideIndex-1].alt;
}

function tartalmaz(adat,minta){
  for (var i=0; i<adat.length; i++)
    if (minta.indexOf(adat.charAt(i)) != -1)
      return true;
  return false;
}

function uresCheck(mezo){
  if (mezo.value != "") {
	return true;
  }
  else{                                                                                                            
    alert("A(z) "+ mezo.name +" mező üres!");
    return false;
  }
}

function teszt(adat,minta){
  for (var i=0; i<adat.length; i++)
    if (minta.indexOf(adat.charAt(i)) == -1)
      return false;

  return true;
}

function eletkorCheck(mezo){
  if (!uresCheck(mezo)) return false;
  if (!teszt(mezo.value,"-1234567890")){
    alert("Ez nem numerikus érték!");
    return false;
  }
  if (mezo.value < 1 || mezo.value > 100){
	alert("A szám az értéktartomány kívül van! 0 < x <= 100");
	return false;
  }

  else{
	alert("Az életkor ok");
    return true;
  }
}

function numerikusCheck(mezo){
  if (!uresCheck(mezo)) return false;
  if (!teszt(mezo.value,"-1234567890")){
    alert("Ez nem numerikus érték!");
    return false;
  }
  if (mezo.value < 1 || mezo.value > 100){
	alert("A szám az értéktartomány kívül van! 0 < x <= 100");
	return false;
  }

  else{
    return true;
  }
}

function emailCheck(mezo)
{
	szoveg = mezo.value;
	szoveghossza=(szoveg.length);
  if ((szoveghossza>9) && (szoveghossza<52))
    { 
		reszek=szoveg.split(" ");
		egy=reszek[0];
		ketto=reszek[1];
		
		if(ketto != undefined)
		{
			alert("Nem elfogadott! Szokoz nem lehet az e-mail-ben!"); return  false;
		}
		else{
			 kukac_pozicio=szoveg.indexOf('@');
			 kukac_pozicio02=szoveg.lastIndexOf('@');
				
				if ((kukac_pozicio>2 && kukac_pozicio==kukac_pozicio02))
					{
						 pont=szoveg.indexOf('.');
						 pont_pozicio=(kukac_pozicio+3);
							if ((pont>pont_pozicio && szoveg.indexOf('.')>szoveg.length-5))
							{
								alert("Ez elfogadhato e-mail nev!"); return true;
							}
							else{ alert("Nincs pont, vagy rossz pozicioban van!"); return false; }
						
					}
					else
						{ alert("Problema a @ karakter:NINCS, rossz helyen van, vagy tobbet is beirtal!"); 
								return  false; 
						}
			}
		
	}

	else{ alert("Rovid, vagy tul hosszu e-mail nev!"); return  false; }
}

function telefonCheck(mezo){
  if (!uresCheck(mezo)) return false;
  if (!teszt(mezo.value,"1234567890()/- ") ||
    !tartalmaz(mezo.value,"1234567890")){
    alert("Ez nem jó telefonszám!");
    return false;
  }
  else{ 
	return true;
	alert("Megfelelő a telefonszám");
  }
}


function ellenoriz(){
  if (uresCheck(document.form1.nev) && telefonCheck(document.form1.telefon) 
	  && numerikusCheck(document.form1.eletkor) && emailCheck(document.form1.email)){
    document.form1.action = "mailto:"+document.form1.email.value;

    return true;
  }
  else return false;
}

function Ujablaknyit() 
{
WindowAblak = window.open('','NewWin','toolbar=no, status=no, width=600, height=200, top=200, left=400' )

adat = "<ul><li><b>ŰRLAP NEVE: </b>" + document.form1.name + "</li>";
<!--adat += "<li><b>ELEMEK SZÁMA: </b>" + document.form1.length;-->
adat += "<ul><li><b>NÉV: </b>" + document.form1.nev.value + "</li>";
<!--adat += "<li><b>LAKCÍME: </b>" + document.form1.address.value + "</li>";-->
adat += "<li><b>TELEFONSZÁM: </b>" + document.form1.telefon.value + "</li>";
adat += "<li><b>ÉLETKOR: </b>" + document.form1.eletkor.value + "</li>";
adat += "<li><b>EMAIL: </b>" + document.form1.email.value + "</li></ul></li></ul>";


WindowAblak.document.write(adat);
WindowAblak.document.bgColor="#E0FFFF";
}

function Ablakbezar(){
  close();
}

function ujablakImage(){
  ablak = open("pld041.htm", "uj_ablak", 
    "width=1000,height=750,status=no,menubar=no");
	imageZoom("myimage", "myresult");
}

function imageZoom(imgID, resultID) {
  var img, lens, result, cx, cy;
  ablak = open("kep_nagyit.html", "uj_ablak", 
    "width=1000,height=750,status=no,menubar=no");
  img = document.getElementById(imgID);
  result = document.getElementById(resultID);
  /* Create lens: */
  lens = document.createElement("DIV");
  lens.setAttribute("class", "img-zoom-lens");
  /* Insert lens: */
  img.parentElement.insertBefore(lens, img);
  /* Calculate the ratio between result DIV and lens: */
  cx = result.offsetWidth / lens.offsetWidth;
  cy = result.offsetHeight / lens.offsetHeight;
  /* Set background properties for the result DIV */
  result.style.backgroundImage = "url('" + img.src + "')";
  result.style.backgroundSize = (img.width * cx) + "px " + (img.height * cy) + "px";
  /* Execute a function when someone moves the cursor over the image, or the lens: */
  lens.addEventListener("mousemove", moveLens);
  img.addEventListener("mousemove", moveLens);
  /* And also for touch screens: */
  lens.addEventListener("touchmove", moveLens);
  img.addEventListener("touchmove", moveLens);
  function moveLens(e) {
    var pos, x, y;
    /* Prevent any other actions that may occur when moving over the image */
    e.preventDefault();
    /* Get the cursor's x and y positions: */
    pos = getCursorPos(e);
    /* Calculate the position of the lens: */
    x = pos.x - (lens.offsetWidth / 2);
    y = pos.y - (lens.offsetHeight / 2);
    /* Prevent the lens from being positioned outside the image: */
    if (x > img.width - lens.offsetWidth) {x = img.width - lens.offsetWidth;}
    if (x < 0) {x = 0;}
    if (y > img.height - lens.offsetHeight) {y = img.height - lens.offsetHeight;}
    if (y < 0) {y = 0;}
    /* Set the position of the lens: */
    lens.style.left = x + "px";
    lens.style.top = y + "px";
    /* Display what the lens "sees": */
    result.style.backgroundPosition = "-" + (x * cx) + "px -" + (y * cy) + "px";
  }
  function getCursorPos(e) {
    var a, x = 0, y = 0;
    e = e || window.event;
    /* Get the x and y positions of the image: */
    a = img.getBoundingClientRect();
    /* Calculate the cursor's x and y coordinates, relative to the image: */
    x = e.pageX - a.left;
    y = e.pageY - a.top;
    /* Consider any page scrolling: */
    x = x - window.pageXOffset;
    y = y - window.pageYOffset;
    return {x : x, y : y};
  }
}

function hatterszin_kek()
{ 
	document.getElementById("foform").style.backgroundColor = "lightblue";
}
function hatterszin_darksalmon()
{ 
	document.getElementById("foform").style.backgroundColor = "darksalmon";
}
function hatterszin_zold()
{ 
	document.getElementById("foform").style.backgroundColor = "lightgreen";;
}
function hatterszin_feher()
{ 
	document.getElementById("foform").style.backgroundColor = "white";
}
function hatterszin_gold()
{ 
	document.getElementById("foform").style.backgroundColor = "gold";
}
function hatterszin_aqua()
{ 
	document.getElementById("foform").style.backgroundColor = "aqua";
}
function hatterszin_lightpink()
{ 
	document.getElementById("foform").style.backgroundColor = "lightpink";
}

function hattervalaszto(){
		document.getElementById("main").style.backgroundColor = "white";
}

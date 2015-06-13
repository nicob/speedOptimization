<h2>Project04</h2>
<h3>Page speed optimizations</h3>
<h4>index.html</h4>
<p>My project is hosted at http://www.beligiannis.net/cameron</p>
<p>I made some changes that helped page render faster</p>
<p>Running PageSpeed insights for index.html I get 98/100 for mobile & 99/100 for desktop</p>
<h4>Changes I made at index.html</h4>
<ol>
<li>Emebed css style inside the index.html file so it is not render blocking</li>
<li>Optimised all images so the browser does not has to spend time resizing them. Used Fireworks to resize images.</li>
<li>Also placed async inside <script async src="js/perfmatters.js"></script> so js file is not render blocking.</li>
</ol>
<hr/>
<h4>pizza.html - main.js</h4>
<p>Regarding the pizza.html did some changes that led pizzas scrolling happen at less than 60FPS and pizzas size change happen at almost 1ms</p>
<p>When I recorded scroll and change size events I realised that some functions were generating Forced layout events. So I made some changes that prevented the Force layout events to happen</p>
<ol>
<li>When recording the scroll event, saw that it was happening inside main.js by the function update positions at line 520. This function was causing a Forced layout event. What I did instead of calculating document.body.scrollTop / 1250 inside the for loop, I created, outside the for loop, a var phase1=document.body.scrollTop / 1250. Then I am using this phase1 var inside the for loop of the update positions function </li>
<li>Regarding the pizza resize, when recording the resize event, I noticed that a  Forced layout event was created by a function called resizepizzas() at line 101 of pizza.html.  Back to main.js located function resizepizzas(). Inside there there is another function changeSliderLabel(). Inside this function there is a switch statement which in each case calls document.querySelector("#pizzaSize").  What I did to optimize this function was to create a var pizzaInnerValue=document.getElementById("pizzaSize") outside the switch statement. Then used this var inside the switch statement  . </li>
<li>Another last optiomization I did inside pizza.html was to optimize the pizzeria.jpg. I resized the browser to check which is the biggest size I need for the responsive layout (it was 360x270) and then optimized this image to this size so the browser does not spend time resizing a bigger image.</li>
</ol>
=======

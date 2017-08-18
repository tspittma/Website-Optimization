## Website Performance Optimization portfolio project
[live link](https://tspittma.github.io/Website-Optimization/)

### Optimized the provided online portfolio for speed using Google's PageSpeed tools.

Optimization was focused on the critical rendering path to make the page render as quickly as possible via implementing techniques learned in Udacity's [Critical Rendering Path course](https://www.udacity.com/course/ud884).

### INDEX.HTML

* The original PageSpeed Insights score for index.html was 28/100 for mobile and 47/100 for desktop. After optimizing, the scores are 95 for mobile and 96 for desktop. The following changes were made to to achieve these scores:

** Images **
Resized and compressed pizzeria.jpg.

** CSS **
Main: eliminated render blocking allow the browser to proceed with rendering the page.
Print: added media="print" attribute to unblock rendering.

** JS **
Added async tag to stop script from blocking parsing.

*** MODIFIED - INDEX.HTML ***

* Pizzeria Image - createed an optimized resized image copy of the pizzeria.jpg.

* Updated img src to reflect optimized image.

* Removed script tag from header and replaced it with a style tag since it contains styles.

* Fixed syntax error

** JS **

* Minified code - source: http://www.willpeavy.com/minifier/

### PIZZERIA.HTML

* Google Chrome DevTools - used to measure frames per second (fps) via the performance timeline, debug, and optimize the JavaScript.

** JS **

* function changeSliderLabel(size) updated for faster loading for changing pizza slider size

* Eliminated the scrollTop from for loop by caching the value before function updatePositions().

* function changePizzaSizes(sizes) - Moved variables out of the for loop to prevent unnecessary calculations.

* Calls for style elements were minimized to prevent the browser from optimizing reflows.

* Enhanced speed by replacing querySelectorAll with getElementsByClassName.

*** MODIFIED 1 - PIZZA.HTML ***

* Pizzaria Image - fixed size to make bigger, also optimized and compressed the image, maintaining the original/provided size.

* Replaced document.querySelector("#pizzaSize") with document.getElementById("pizzaSize").innerHTML for each case.

* Removed the leading dash (#) from the selector above to make it ("pizzaSize") since using this JavaScript API call.

* Used getElementsByClassName in replace of querySelectorAll for added load speed.

* Removed the determineDx() function becasue the functionality was simplified by changeSliderLabel - var dx = changeSliderLabel(size);

* Restored "for" value from for (var i = 2; i < 30; i++) to for (var i = 2; i < 100; i++).

* Declared the pizzasDiv variable outside the loop, so only DOM call is made one.
	var pizzasDiv = document.getElementById('randomPizzas');
	for (var i = 2; i < 100; i++) {
     pizzasDiv.appendChild(pizzaElementGenerator(i));
	}

* Createed a local variable to save document.getElementsByClassName('randomPizzaContainer') outside the loop so that the DOM is not explicitly touched in every iteration.

* Outside the for statement/loop - var randomPizzaContainer =  document.getElementsByClassName('randomPizzaContainer');

* Inside the for statement/loop - for (/** expressions */) {
    randomPizzaContainer[i].style.width = newwidth;
}

* Updated elem.src image filename.

* Replaced for from the following:

  for (var i = 0; i < items.length; i++) {
    //using transform instead of using style.left to change position.
    var phase = Math.sin((theScrollTop / 1250) + (i % 5));
    var newPos = items[i].basicLeft + 100 * phase - 600 + 'px';
    items[i].style.transform = "translateX(" + newPos + ")";
  }

  to

   for (var i = 0; i < items.length; i++) {
    //using transform instead of using style.left to change position.
    var phase = Math.sin((theScrollTop / 1250) + (i % 5));
    items[i].style.transform = 'translateX(' + 100 * phase + 'px)';
  }

  * Restored column value from the following:
    var cols = 6;

    to (cover background with pizzas)

    var cols = 8;

  * Changed element style line from the following:
     elem.basicLeft = (i % cols) * s;

     to

     elem.style.left = i % cols * s + 'px';

### Command Prompt and ngrok for localhost server

* Used the public link provided by ngrok to test optimizations in my browser and the Google PageSpeed analysis tool
* ngrok proved a public localhost:8000 link (http://c81297c4.ngrok.io)

*** Additional Notes: Optimization Tips and Tricks ***

* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>

*** Customization with Bootstrap ***
The portfolio was built on Twitter's <a href="http://getbootstrap.com/">Bootstrap</a> framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* <a href="http://getbootstrap.com/css/">Bootstrap's CSS Classes</a>
* <a href="http://getbootstrap.com/components/">Bootstrap's Components</a>

### Google PageSpeed Scores
* Good
* Mobile and Desktop are above 90

*** SOURCING ***
Project example referenced: https://github.com/jshanks24/Udacity-Website-Optimization.git

## Website Performance Optimization portfolio project

My challenge was to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

To get started, check out the repository and inspect the code.

### Getting started

1. Download the zip file
2. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

3. Open a browser and visit localhost:8080
4. Download and install [ngrok](https://ngrok.com/) to the top-level of your project directory to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ./ngrok http 8080
  ```

5. Copy the public URL ngrok gives you and try running it through [PageSpeed Insights!](https://developers.google.com/speed/pagespeed/insights/) Optional: [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)


#### Part 1: Optimize PageSpeed Insights score for index.html

Some useful tips to help you get started:

Changes made to optimize index.html are :

1. Set analytics.js to run asynchronously

2. Set media query for print style sheet

3. Removed the Google fonts as it affects the rendering process.

4. Optimized image sizes for profilepic.jpg, pizza.png, pizzeria.jpg

5. Moved the content of style.css to "inline" (enclosed in '<style>' tags withing the index.html file) to speed loading of the initial page.

6. Minified the HTML file and all the CSS and JS files linked to it.

Follow-up checks on the Pagespeed score indicate the largest gain from 4) Optimized images and 5) inlining the styles.css.

#### Part 2: Optimize Frames per Second in pizza.html

To optimize views/pizza.html, you will need to modify views/js/main.js until your frames per second rate is 60 fps or higher. You will find instructive comments in main.js. 

Changes made to the views/js/main.js file are :

1. In the function (document.addEventListener('DOMContentLoaded', function() ) that generates the sliding pizza, I changed the   maximum value of i in the for loop from 200 to 20, as that seemed a sufficient numeber of sliding pizzas to be displayed on any one frame. This reduced the load time by making the function more efficient.

2. In function updatePositions():

   - Changed querySelectorAll to getElementsByClassName as it is more efficient (has fewer elements to search).

   - Calculation of top variable is taken out of the loop to prevent DOM query on every iteration.

   - Declared phase varibale outside the loop, so it is not created every time the loop is executed. 

3. In function changePizzaSizes(size):

    - Moved the getElements (pizzaContainers) into a variable outside of the loop so it does both need to be processed for each element re-size.

    - Changed querySelectorAll to getElementsByClassName as it is more efficient (has fewer elements to search).

    - Both the dx and the newwidth is calculated outside the loop as the pizzas are all the same size

4. In the function changeSliderLabel(size)
 
   - Changed all the querySelector to getElementById as it takes fewer searches     

You might find the FPS Counter/HUD Display useful in Chrome developer tools described here: [Chrome Dev Tools tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks).

### Optimization Tips and Tricks
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

### Customization with Bootstrap
The portfolio was built on Twitter's <a href="http://getbootstrap.com/">Bootstrap</a> framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* <a href="http://getbootstrap.com/css/">Bootstrap's CSS Classes</a>
* <a href="http://getbootstrap.com/components/">Bootstrap's Components</a>

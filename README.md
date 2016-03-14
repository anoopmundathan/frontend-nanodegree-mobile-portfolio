## Website Performance Optimization portfolio project - Solution

## Part 1 Solution: Optimize PageSpeed Insights score for index.html
Following optimisation methods are applied to reduce CRP. Build tool [gulp](http://gulpjs.com/) is used for this purpose.

### Minimize Number of Bytes
1.Minify index.html using [gulp-htmlmin](https://www.npmjs.com/package/gulp-htmlmin/) plugin.

2.Uglify JS using [gulp-uglify](https://www.npmjs.com/package/gulp-uglify/) plugin.

3.Optimised images using [imagemin](https://www.npmjs.com/package/imagemin) plugin.

### Minimize the use of rendering block resources (CSS)
1.Minify and Inline CSS using [critical](https://github.com/addyosmani/critical/) plugin.

2.Media Queries on <link> tag to unblock rendering in print.css

### Minimize use of parser blocking JS
1.Defer java script execustion using async attribute.

2.Google webfont is loaded asynchronously using JS.

## Part 2 Solution: Optimize Frames per Second in pizza.html- Improve site scrolling perfo

###Change Pizza Size 
To increase Response time, I have declared new variable newWidth in function changePizzaSizes and hard coded width of small, medium and large Pizzas. So when the slider changes I am assaigning newWidth to all random Pizzas according to the newWidth. Removed unnessary fuction determineDx.

###Scrolling Pizzas##

Orignally 200 pizzas were being created no matter how many were to be displayed on screen. So changed to create only 24 pizzas in DOMContentLoaded.

1. To achieve 60FPS while scrolling, I have done following optimisation in updatePositions function

2. All mover pizza selected using getElementsByClassName rather than querySelectorAll.

3. Calculated and cache length variable outside of the for loop.

4. In Original code there was Force synchronised Layout happening as scollTop causes Layout to run inside the loop and that gets invalidated in style.left property assiagnment, also scollTop always same and there is no reason that calculation should exists inside the loop. So I decided to move the srollTop calculation outside the for loop and uses ScrollTop value from previous frame, which gave me good performance improvement in Javascript part of the frame.

5. Since I reduced number of pizza to 24, browser has to apply recalculated style only for those 24 pizzas rather than 200 pizzas. That imp

## Part 3 How to run the application:
1. Check out the repository
  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok http 8080
  ```
---

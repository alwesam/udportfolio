### Web Optimization Project
----------------------------------

### The goals of this project:

1) Optimizing index.html to achieve a PageSpeed score of 90 on both mobile and desktop platforms
2) Optimizing views/pizza.html to achieve a consistent frame rate of 60fps when scrolling in the page
3) Optimizing views/pizza.html so that the time to resize pizzas (using slider) is less than 5 ms.

----------------------------------

### To visit the project website:

The optimized pages are hosted at: alwesam.github.com/udportfolio

------------------------------------

### To verify the optimizations made:

#### Verifying the PageSpeed score of index.html

1) Visit Google PageSpeed Insights on your web browser
2) Enter the following website: alwesam.github.com/udportfolio/index.html
3) Take note of the scores for both mobile and desktop

#### Verifying frame rate of views/pizza.html

1) On your chrome browser, visit alwesam.github.com/udportfolio/views/pizza.html or follow the link from index.html
2) Enter Ctrl+Shift+I, this will show the chrome dev tool
3) Click on the Timeline tab
4) Click on the record (red circle) button
5) scroll the webpage for few seconds and then stop recording
6) Take note of the frame rate view

#### Verifying time to resize pizzas on views/pizza.html

1) On your chrome browser, visit alwesam.github.com/udportfolio/views/pizza.html or follow the link from index.html
2) Enter Ctrl+Shift+I, this will show the chrome dev tool
3) Click on the Console tab
4) On pizzas.html page, find the slider and click to change resize pizzas
5) Take note of the values logged in the Console.

-------------------------------------------

### Optimizations made to index.html

a) Reduced number of unnecessary pixels for pizzeria image by resizing the image to a natural size that's equal to its display size.  Number of unnecessary pixels that was transmitted (2048-115)*(1536-75) = 1933x1461, which greatly slowed down the rendering of the index.html page.

b) Minifed style.css by removing white spaces (used the http://cssminifier.com tool).  Then Base64 encoded the css file and embeded directly in the index.html file

c) Removed comments and line spaces from index.html

d) Added media attribute to print.css link

e) Added async attribute to google analytics JS script

f) Moved google analytics code to an external script file and added async attribute to script

g) Moved google fonts css link to end of body file


--------------------------------------------------

### Optimization to main.js to improve frame rate when scrolling in views/pizza.html

a) Calculated a unique set of 5 values (phases) outside the For loop in the updatePositions function.

b) Reduced the number animating pizzas in the background from 200 to 24 since this will be maximum number rendered on a 1600x900 screen at any give time.

c) Replaced document.querySelectorAll() to access DOM elements with document.getElementsByClassName(). 

d) Defined an array variable 'items' (that references to all pizzas in the 'mover' class) outside updatePositions function.  Hence, there will be no need to access DOM elements at every scroll.

e) Used transform:translateX() function to change positions of animated pizzas (instead of triggering a relayout event by assiging abosolute values to items.style.left).

f) To reduce paint time, defined the css property (backface-visibility) of the 'mover' class and assigned it the value of 'hidden'.

For more details, check comments on main.js

Optimization to main.js to reduce resizing time in views/pizza.html

a) Ensured that the DOM is being accessed outside the FOR loop in changePizzaSizes function as well as used getElementsByClassName() instead of querySelectorAll().

b) Calculated dx and newwidth outside the FOR loop since it's the same for all pizzas.

c) windowwidth variable is calculated outside determineDX function (or rather outisde the FOR loop in changePizzaSizes function) since it's constant.

For more details, check comments on main.js



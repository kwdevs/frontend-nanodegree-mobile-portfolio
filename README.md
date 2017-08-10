## What is this repo about?

This is the final product of a project intended to help myself fully understand the Critical Rendering Path (CRP) by implenting various fixes to improve the performance of the site.

### How do you access this website?

Simple. The project is being hosted on GitHub Pages. Just follow this [link](https://kwdevs.github.io/frontend-nanodegree-mobile-portfolio/) to view the site's homepage. Or this [link](https://kwdevs.github.io/frontend-nanodegree-mobile-portfolio/views/pizza.html) to view the pizza section of this site.

#### Optimizations Performed on the Homepage(index.html @ root directory).

* Google Analytics now uses an async tag, which previously was render blocking.
* Google Analytics is now served over https, preventing mixed content errors.
* Images were compressed and resized accordingly. This was done manually. (Still learning Gulp).
* A media query was added to the print.css in index.html head. This unblocked rendering.
* WebFontLoader was implented to help fonts load better.
* style.css was inlined for the homepage.  The css was compressed.

#### Optimizations Performed on the Pizza Page (main.js).

* Changed .container background to green.
* Fixed a Forced Synchronous Layout (FSL) caused by function changePizzaSizes. A for loop was repeatedly accessing the DOM unnecessarily. Now, DOM elements are collected outside the for loop, & styles are applied within the for loop.
* Lowered the amount of background pizzas generated onload to 32 from 200.  This keeps the same "look" with less DOM elements being created onload.
* The anonymous function which generates sliding pizzas now calls buildBackgroundPizzas, which is a one off function to draw the pizzas to the screen.
* Fixed updatePositions function which caused a FSL. The DOM was being accessed too often in a for loop. updatePositions now just accepts a variable from the function onScroll.  onScroll lives outside updatePositions and keeps track of the numeric values needed to slide background pizzas side to side smoothly.


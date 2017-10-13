## Website Performance Optimization portfolio project

### Running Pizza Web App

The src folder contains the adapted course code forked from https://github.com/udacity/frontend-nanodegree-mobile-portfolio
The dist folder contains the minified/compressed version.

To run the dist code

```
cd \dist

Run the server
python -m SimpleHTTPServer 8080

Create a dns to run in pageSpeed
ngrok http 8080
```

Minifier used - https://www.minifier.org/ and https://www.willpeavy.com/minifier/

Optimisations made :-

html, css and js minified.

**index.html**
- changed the analytics file to load asynchronously
- changed the google font to load via javascript using webfontloader
- added media="print" to only load print.css if printing
- added style.css into a style tag in head - all were considered  critical at https://jonassebastianohlsson.com/criticalpathcssgenerator
- created a reduced 100X75 pixel version of views/pizzeria.jpg to use in this page.

**views/pizza.html**
- included styles.css in html document to reduce the number of server calls - all were considered  critical at https://jonassebastianohlsson.com/criticalpathcssgenerator


**views/main.js**
- replaced document.querySelector with faster getElementById
- replaced document.querySelectorAll with faster getElementsByClassName
- replaced document.querySelector with faster getElementsByClassName
- define pizzaItemLen outside the for loop so that it only calculates once
- take the pizzasDiv selector search outside the for loop (line 460)
- define phase variable and the items array lenth used in the loop, inside initialization section rather than in the loop
- use a style.transform instead of setting the .left position in updatePositions() function, to prevent FSL in the loop in UpdatePositions function.
- dynamically calculate the no. of moving Pizza's to save on creating non visible ones
- define the definition of elem in the initialisation of the for loop to prevent it from being created every loop
- define the moving pizza image left most position to enable the style.transform to work of the base position

**views/images**
- reduced the size of images/pizza.png to create a small jpg for the moving pizzas.
- reduced the size of images/pizzeria.png - the original size is over the maximum ever displayed.
- created a reduced 100X75 pixel version of views/pizzeria.jpg to use in the index.html page.



**style.css**
- Ran css through https://jonassebastianohlsson.com/criticalpathcssgenerator/ and all styles were critical
- included this small stylesheet in the pizza.html and index.html definitions
- set backface to hidden on .mover class to improve performance




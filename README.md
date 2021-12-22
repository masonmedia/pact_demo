# Mason pact Design Project

This is the repo for a design assignment for PACT by Andrew Mason.

### Notes:

#### Framework and build tools

The project is built with Vue.js, scss, and Bootstrap 5 for UI framework. For styling and layout I use Bootstrap's Atomic, utility class approach.

#### Carousel

-    I used Swiper for the carousel for a mix of speed and functionality.
-    A note on responsiveness: I found resizing the browser would have an odd resizing effect on the carousel, reducing slides and shifting it to the right slightly, but refreshing the page at different breakpoints achieves normal/desired layout behaviour. 

**Animation** 

For the "Latest Stories" element, I chose to simply hide the title element on first drag/swipe of the carousel.  I played with adding another title element on the top of the carousel in addition to active slide styling, but for simplicity went with this method.

**Images/Content**

For a range of options, I used two different methods for carousel data:
1. Version One uses the json placeholder API as a data source to mockup dummy content. I used axios and a get request to pull in the data.
2. Version Two uses JSON and local images as the data source, which are imported into the page.

#### Animation

1. Page transition animations make use of native Vue animation classes and plain css.
2. Text entrance animations are a combination of animate.css and plain css keyframes.
3. In an ideal state I would use GSAP for timeline animations - in the case of longer pages with more scrolling I would also use GSAP for scroll animations. 

#### Future/ideal state

I initially wanted to hook up API data to the carousel which would navigate dynamically to detail pages for each slide. Time didn't allow in this case but this was the intention with buttons/links.
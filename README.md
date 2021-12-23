# Mason pact Design Project

This is the repo for a design assignment for PACT by Andrew Mason.

### Notes:

#### Framework and build tools

The project is built with Vue.js, scss, animate.css, and Bootstrap 5 for UI framework. For styling and layout I use Bootstrap's Atomic, utility class approach.

#### Carousel

For the carousel I used the Swiper library for a mix of speed and functionality.

**Animation** 

For the "Latest Stories" element, I chose to simply hide the title element on first drag/swipe of the carousel.  I played with adding another title element on the top of the carousel in addition to active slide styling, but for simplicity went with this method.

**Images**

Images are sourced from Unsplash.

#### Animation

1. Page transition animations make use of native Vue animation classes and plain css.
2. Text entrance animations are a combination of animate.css and plain css keyframes.
3. In an ideal state I would use GSAP for timeline animations - in the case of longer pages with more scrolling I would also use GSAP for scroll animations. 

#### Future/ideal state

I initially wanted to hook up API data to the carousel which would navigate dynamically to detail pages for each slide. Time didn't allow in this case but this was the intention with buttons/links.
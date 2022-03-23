<img width="1520" alt="Screen Shot 2021-12-23 at 7 07 21 PM" src="https://user-images.githubusercontent.com/39093481/147300974-7877dffd-ff61-464c-a389-dbcc07e2bd55.png">

# Mason pact Design Project

A repo housing a design/build project for PACT.  Aside from notes below, this project uses Bootstrap 5 directly without the BootstrapVue library. The removal of jQuery and transition to plain js remove the need for the BootstrapVue wrapper.  This allows use of all the newest utility classes and components in the latest version of Bootstrap.  

### Notes:

#### Framework and build tools

The project is built with Vue.js, Vue CLI, SCSS, animate.css, and Bootstrap 5 for UI framework. For styling and layout I use Bootstrap's Atomic, utility class approach.

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

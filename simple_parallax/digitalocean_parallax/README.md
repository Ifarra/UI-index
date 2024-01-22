# Parallax Scrolling Effect by <a href="https://www.digitalocean.com/">digitalocean</a>  
<p>In this markdown and demo i edited some code because the original tutorial is not working properly <a href="https://www.digitalocean.com/community/tutorials/css-pure-css-parallax">Link to tutorial</a>  </p>

## Introduction
Modern CSS is a powerful tool you can use to create many advanced User Interface (UI) features.    
In the past, these features relied on JavaScript libraries.

In this guide, you will set up a few CSS lines to create a scrolling parallax effect on a web page.    
You will use images from placekitten.com as placeholder background images.

You will have a webpage with a pure CSS scrolling parallax effect once you’ve completed the tutorial.

## Setting Up the Application Structure
In this step, you will add the HTML needed to create the structure of the project.    
Inside your index.html file add the following code:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="stylesheet" href="styles.css" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>CSS Scrolling Parallax</title>
  </head>
  <body>
    <main class="wrapper">
      <section class="section parallax bg1">
        <h1>Cute Kitten</h1>
      </section>
      <section class="section static">
        <h1>Boring</h1>
      </section>
      <section class="section parallax bg2">
        <h1>Fluffy Kitten</h1>
      </section>
    </main>
  </body>
</html>
```

## Creating a CSS File and Adding Initial CSS
In this step, you will create a CSS file.     
Then you will add in the initial CSS needed to style the website and create the parallax effect.

```css
.wrapper {
  height: 100vh;
  overflow-x: hidden;
  overflow-y: auto;
  perspective: 2px;
}
```

The .wrapper class sets the perspective and scroll properties for the whole page.

The height of the wrapper needs to be set to a fixed value for the effect to work.    
You can use the viewport unit `vh` set to `100` to get the full height of the screen’s viewport.

When you scale the images, they will add a horizontal scrollbar to the screen,    
so you can disable it by adding `overflow-x: hidden;`.    
The perspective property simulates the distance from the viewport to the pseudo-elements    
you will create and transform further down in the CSS.

In the next step, you will add more CSS to style your webpage.

```css
.section { 
  position: relative;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  text-shadow: 0 0 5px #000;
}
```

The `.section` class defines the size, display, and text properties for the main sections.

Set a position of relative so that the child, `.parallax::after` can be absolutely    
positioned relative to the parent element `.section`.

Each section has a `view-height(vh)` of `100` to take up the viewport’s full height.    
This value can be changed and set to whatever height you prefer for each section.

Finally, the remainder CSS properties are used to format and add styling to the text inside each section.``    
It positions the text in the center of each section and adds a color of white.

Next, you will add a pseudo-element and style it to create the parallax effect on two of the sections in your HTML.

```css
.parallax::after {
  content: " ";
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}

.parallax {
  transform: translateZ(-1px) scale(1.5);
  background-size: 100%;
  z-index: -1;
}
```

The `.parallax` class adds an `::after` pseudo-element to the background image and provides    
the transforms needed for the parallax effect.

The pseudo-element is the last child of the element with the class `.parallax`.

The first half of the code displays and positions the psuedo-element.    
The transform property moves the pseudo-element back away from the camera on the z-index,    
then scales it back up to fill the viewport.

Because the pseudo-element is further away, it appears to move more slowly.

In the next step, you will add in the background images and static background style.

```css
.static {
  background: red;
}
```

The `.static` class adds a background to the static section that does not have an image.

The two sections with the `.parallax` class also have an extra class that is different for each.    
Use the `.bg1` and `.bg2` classes to add the Kitten background images.

```css
.bg1::after {
  background-image: url('https://placekitten.com/g/900/700');
}

.bg2::after {
  background-image: url('https://placekitten.com/g/800/600');
}
```

The `.bg1`, `.bg2` classes add the respective background images for each section.

The images are from the placekitten website. It is a service for getting pictures of kittens for use as placeholders.


## full html code
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="stylesheet" href="styles.css" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>CSS Parallax</title>
  </head>
  <body>
    <main class="wrapper">
      <section class="section parallax bg1">
        <h1>Cute Kitten</h1>
      </section>
      <section class="section static">
        <h1>Boring</h1>
      </section>
      <section class="section parallax bg2">
        <h1>Fluffy Kitten</h1>
      </section>
    </main>
  </body>
</html>
```

## full css code
```css
body{
margin: 0;
padding: 0;
}

.wrapper {
  /* The height needs to be set to a fixed value for the effect to work.
   * 100vh is the full height of the viewport. */
  height: 100vh;
  /* The scaling of the images would add a horizontal scrollbar, so disable x overflow. */
  overflow-x: hidden;
  /* Enable scrolling on the page. */
  overflow-y: auto;
  /* Set the perspective to 3px. This is essentailly the simulated distance from the viewport to transformed objects.*/
  perspective: 3px;
}

.section {
  /* Needed for children to be absolutely positioned relative to the parent. */
  position: relative;
  /* The height of the container. Must be set, but it doesn't really matter what the value is. */
  height: 100vh;

  /* For text formatting. */
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  text-shadow: 0 0 5px #000;
}

.parallax::after {
  /* Display and position the pseudo-element */
  content: " "; 
 /* Force the background image to fill the whole element. */
  background-size: 100%;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}

.parallax {
  /* Move the pseudo-element back away from the camera,
   * then scale it back up to fill the viewport.
   * Because the pseudo-element is further away, it appears to move more slowly, like in real life. */
  transform: translateZ(-1px) scale(1.5);
  /* Keep the image from overlapping sibling elements. */
  z-index: -1;
}

/* The styling for the static div. */
.static {
  background: red;
}

/* Sets the actual background images to adorable kitties. This part is crucial. */
.bg1::after {
  background-image: url("https://placekitten.com/g/900/700");
}

.bg2::after {
  background-image: url("https://placekitten.com/g/800/600");
}
```

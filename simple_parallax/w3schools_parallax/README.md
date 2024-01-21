# Parallax Scrolling Effect by <a href="https://www.w3schools.com/">w3schools</a>
<a href="https://www.w3schools.com/howto/howto_css_parallax.asp">Link to tutorial</a>

Use a container element and add a background image to the container with a specific height.    
Then use the `background-attachment: fixed` to create the actual parallax effect.    
The other background properties are used to center and scale the image perfectly:

```html
<style>
.parallax {
  /* The image used */
  background-image: url("img_parallax.jpg");

  /* Set a specific height */
  min-height: 500px;

  /* You can also use percent 
  height: 100%;
  */
  
  /* Create the parallax scrolling effect */
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>

<!-- Container element -->
<div class="parallax"></div>
```

Some mobile devices have a problem with `background-attachment: fixed`.     
However, you can use media queries to turn off the parallax effect for mobile devices:

```css
/* Turn off parallax scrolling for all tablets and phones. Increase/decrease the pixels if needed */
@media only screen and (max-device-width: 1366px) {
  .parallax {
    background-attachment: scroll;
  }
}
```

<a href="https://www.w3schools.com/howto/tryhow_css_parallax_demo.htm">link to demo</a>

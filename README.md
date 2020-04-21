# Vanilla Image Slider

I just realised when writing this readme that this is equivalent to what's called a "carousel" in most frameworks. Screw it, I'm calling it a slider.

[Click for demo!](https://pseudomon.github.io/img-slider)

This is one way of implementing a slider using only vanilla HTML/CSS/JS (no jQuery! No utility libraries!). It's designed to keep the HTML simple and mutable, the CSS customizable, and the JS a black box that you don't have to tinker with at all. It can be easily plopped into any webpage written by hand. The dafault CSS is also responsive by default!

It uses modern HTML/CSS/JS features that are probably not available for e.g. Internet Explorer or Netscape. But all modern browsers shouldn't have any trouble with it.

If you're using a framework like React, there's probably a more effective way of implementing this. This is just one way to do it.

## Usage
I made this just for educational purpose, really, but you can also inject it into your project if you want to.

From this repository, grab *img-slider.js* and include it into your webpage. Just using `<script src="img-slider.js">` is fine. It will let you use the class ImageSlider.

Also grab *img-slider.css* and include that. You can `@import` it into your existing stylesheet, or just go wild and copy everything in there and pasting it to your page.

In your script, you should create an ImageSlider for every slider you made in your page. I recommend doing it this way:

```js
document.addEventListener("DOMContentLoaded",  () => {

	var allSliders = []

	document.querySelectorAll('.slider-container').forEach( (slider) => {

		allSliders.push(new ImageSlider(slider)) 

	})
})
```

Or if you only have one slider, you can also use the old-fashioned getElementById
```js
var slider = new ImageSlider(document.getElementById('my-slider'))
````

### In the HTML
You can look at `index.html` in this repository for example on how to use it, but in general, your slider's HTML should look like this:
```html
<div class="slider-container">
	<div class="arrow left">
		<!-- Insert arrow here -->
	</div>

	<div class="arrow right">
		<!-- Insert arrow here -->
	</div>

	<div class="slider-inner">
		<!-- Insert slider element here -->
	</div>
</div>
```
The arrow can be an image, a text, whatever. A slider element can be either straight up an `<img>`, a flexbox containing them, or a grid containing them. Technically it can probably fit regular ol' blocks, too but I haven't tried that yet.

Class name is important. Don't change it!

You can change the first image being shown using the `data-current-image` attribute. `<div class="slider-container" data-current-image="2">` will set it to show the third image (i.e. image with id 2) on page load.

### Interacting with the slider within the script
You don't have to bother with this section if you don't want to manipulate the slider programatically. 

The ImageSlider object will have the following methods that you can use:

- `changePos(id)` will slide it to the image with that id. The leftmost image has the id 0, the one to its right is 1, and so on.
- `toggleAnimation()` will toggle the slider's animation on and off.
- huh I guess that's it

Changing the current image shown with `changePos()` will automatically update the element's `data-current-image` attribute. Accessing that attribute is the recommended way of checking which image is currently showing.

## Credits

The images I use for this sample came from the official page of the mobile game [SinoAlice](https://sinoalice.global/). I believe using it in this way fall under educational fair use.


## More

I wrote a lengthy blog post about creating this in [my blog](https://pseudomon.wordpress.com/2020/04/12/creating-an-image-slider-with-vanilla-html-css-js/). It's based on the 'simpler' branch of this repository, so it doesn't get into using objects yet. 

It's probably useful learning-material to people who are just starting out with front-end development! Maybe!
---
title: Images
date: 2021-07-09T18:57:34.427Z
permalink: /dev/images.html
eleventyNavigation:
  order: 100
  key: Images
  parent: Dev
  title: Images
---
# Images

You can use [Squoosh.app](https://squoosh.app/) for image resizing.

Instructions (Or watch [this how-to video](https://www.loom.com/share/83e9c3a78d684551a19c7150a36f2fff)):
1. Drag your image into Squoosh
2. Turn on the "Resize" slider, select "Browser High Quality" under "Method".
3. Change width to your desired size, making sure "maintain aspect ratio" box is checked
4. Under compression settings, use default of MozJPEG (a type of optimized jpeg) and 75% quality.
5. Use the slider to view the original image vs the preview of your new image. If quality is noticeably degraded, adjust quality slider settings. 
6. Download image and repeat as needed for extra sizes. 

Example Image - Height and width attributes are set, as well as alt text. Decoding is set to "async", or asynchronous, which helps to avoid user impact of the CPU-time used to decode images.

```html
<img src="img-url.jpg" width="300" height="200" decoding="async" alt="Example text, can use [company] if no good descriptor is available">
```

Add Lazy Loading To Images Below The Fold (Typically safe to use on anything under the service boxes) 

```html
<img src="" width="" height="" loading="lazy" decoding="async">
```

### Responsive Images

For Inline Images That Require Multiple Sizes (I.e., non-svg logos, footer logos, badges, accent photos)

```html
<img srcset="115w.png 115w,
220w.png 200w,
400w.png 400w" sizes="(max-width: 640px) 115px,(max-width: 1024px) 200px,400px" 
src="400w.png" alt="">
```


### Background Images

[https://web.dev/optimize-css-background-images-with-media-queries/](https://web.dev/optimize-css-background-images-with-media-queries/)

```css
/* Non-Media Query instance of MM doesn't need a background-image, but has other background styles */
#main-message {
    overflow:hidden;
    background-size:cover;
    background-repeat:no-repeat;
    background-position:center top;
    position:relative;
    width:100%;
}

/* OR IF SLIDER */

.main-slide {
    overflow:hidden;
    background-size:cover;
    background-repeat:no-repeat;
    background-position:center top;
    position:relative;
    width:100%;
}

@media screen and (min-width:1025px) {
    #main-message {
    /*Save out bg with 1300px width*/
        background-image:url('image-1300.jpg');
    }
	
/*OR IF SLIDER */
    .slide-1 {
	background-image:url('img-1300.jpg');
    }
    .slide-2 {
	background-image:url('img-1300.jpg');
    }
    .slide-3 {
	background-image:url('img-1300.jpg');
    }
    .slide-4 {
	background-image:url('img-1300.jpg');
    }
}
@media screen and (min-width:768px) and (max-width:1024px) {
    #main-message {
        /*Save out bg with 1100px width*/
        background-image:url('img-1100.jpg');
    }
	
    /* Or repeat for slider with 1100px width images */
}
@media screen and (min-width:401px) and (max-width:767px) {
    #main-message {
        /*Save out bg with 800px width*/
        background-image:url('img-800.jpg');
    }
	
    /* Or repeat for slider with 800px width images */
}
@media screen and (max-width:400px) {
    #main-message {
        /*Save out bg with 450px width*/
     background-image:url('img-450.jpg');
    }
	
    /* Or repeat for slider with 450px width images */
}
```

### SVGs

If SVGs are small and used for decorative purposes and below 10 lines of codes just inline them


# Tools 

https://www.responsivebreakpoints.com/<br/>
https://avif.io/<br/> 
https://squoosh.app/<br/>
https://www.industrialempathy.com/posts/image-optimizations/<br/>
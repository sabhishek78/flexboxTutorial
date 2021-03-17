# FlexBox
The “Flexible Box” or “Flexbox” layout mode offers an alternative to Floats for defining the overall appearance of a web page. Whereas floats only let us horizontally position our boxes, flexbox gives us complete control over the alignment, direction, order, and size of our boxes.

The float property can have one of the following values:

* left - The element floats to the left of its container
* right - The element floats to the right of its container
* none - The element does not float (will be displayed just where it occurs in the text). This is default
* inherit - The element inherits the float value of its parent


The following two images demonstrate the additional control that flexbox provides you as compared to float.

![float](https://www.1keydata.com/css-tutorial/example-float-right-float-left.jpg)
![flexbox](https://css-tricks.com/wp-content/uploads/2018/10/justify-content.svg)
# FlexBox Example
## SetUp
For starters, we need an empty HTML document that contains nothing but a menu bar. Make a new  project called flexbox and create a file named 'flexbox.html' and add the following markup:
```HTML
<!DOCTYPE html>
<html lang='en'>
  <head>
    <meta charset='UTF-8'/>
    <title>Some Web Page</title>
    <link rel='stylesheet' href='styles.css'/>
  </head>
  <body>
    <div class='menu-container'>
      <div class='menu'>
        <div class='date'>Aug 14, 2016</div>
        <div class='signup'>Sign Up</div>
        <div class='login'>Login</div>
      </div>
    </div>
  </body>
</html>
```
Create a stylesheet named styles.css and save it in the same folder
```CSS
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.menu-container {
  color: #fff;
  background-color: #5995DA;  /* Blue */
  padding: 20px 0;
}

.menu {
  border: 1px solid #fff;  /* For debugging */
  width: 900px;
}
```
The output for your html file should look like this:

[images](1.jpg)

Create an images folder and download the images from here: [images](https://www.internetingishard.com/html-and-css/flexbox/flexbox-images-449705.zip)

Your project should look like this before moving on:

![project](https://www.internetingishard.com/html-and-css/flexbox/project-files-5cb6e0.png)

Flexbox uses two types of boxes that we’ve never seen before:
* Flex Containers 
* Flex Items : Direct children of a flex container.These items can be flex containers themselves.

The job of a flex container is to group a bunch of flex items together and define how they’re positioned.

![flex container](https://www.internetingishard.com/html-and-css/flexbox/flex-container-and-flex-items-6234bb.png)

# Flex Containers
The first step in using flexbox is to turn one of our HTML elements into a flex container.

To do this we add a 'display' property to the 'menu-container' and assign it a value of 'flex' to turn it into a 'Flex Container'
```CSS
.menu-container {
  /* ... */
  display: flex;
}
```
The next step is to 


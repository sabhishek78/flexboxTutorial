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
## Objective
Our objective is to design this layout

![project](images/target.png)
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

![project](images/1.png)

Create an images folder and download the images from here: [images](https://www.internetingishard.com/html-and-css/flexbox/flexbox-images-449705.zip)

Flexbox uses two types of boxes that we’ve never seen before:
* Flex Containers 
* Flex Items : Direct children of a flex container.These items can be flex containers themselves.

The job of a flex container is to group a bunch of flex items together and define how they’re positioned.

# Flex Containers
The first step in using flexbox is to turn one of our HTML elements into a flex container.

To do this we add a 'display' property to the 'menu-container' and assign it a value of 'flex' to turn it into a 'Flex Container'
```CSS
.menu-container {
  /* ... */
  display: flex;
}
```
So now,we have a flex container with one flex item in it. However, our page will look exactly like it did before because we haven’t told the container how to display its item.

The output for your html file still looks like this:

![project](images/1.png)

# Aligning a Flex Item

'justify-content' property is used to horizontally align the items inside a flex-container.

Add the following line of code to 'centre' the menu
```CSS
.menu-container {
  /* ... */
  display: flex;
  justify-content: center;    /* Add this */
}
```
Notice that we are  adding a property to the parent element (the flex container) instead of directly to the element we wanted to center (the flex item).
This is a diversion from 'float' where we used to manipulate the item and not the container.

The output for your html file now looks like this:

![image](images/2.png)

Other possible values for justify-content are shown below:
* center
* flex-start
* flex-end
* space-around
* space-between

Try experimenting with each of the values and observe how the output changes.

Now we add a 'display' property to the 'menu' and assign it a value of 'flex' to turn it into a 'Flex Container'.
We add a 'justify-content' property to the 'menu' and assign it a value of 'space-between'.
```CSS
.menu {
  /* ... */
  display: flex;
  justify-content: space-between;    /* Add this */
}
```
The output for your html file now looks like this:

![image](images/3.png)
# Grouping Flex Items

Flex containers only know how to position elements that are one level deep (i.e., their child elements). They don’t care one bit about what’s inside their flex items.

We want the 'SignUp' and 'Login' on the right side of the page so lets group them in one 'div' and name it 'links'

```HTML
<div class='menu'>
  <div class='date'>Aug 14, 2016</div>
  <div class='links'>
    <div class='signup'>Sign Up</div>      <!-- This is nested now -->
    <div class='login'>Login</div>         <!-- This one too! -->
  </div>
</div>
```

The output for your html file now looks like this:

![image](images/4.png)

Instead of having three items, our .menu flex container now has only two (.date and .links). Under the existing space-between behavior, they’ll snap to the left and right side of the page.

Now we need to lay out the .links element because it’s using the default block layout mode.
 * make the .links element a flex container by adding 'display: flex'.
 * add the justify-content property to the .links container and give it a value of 'flex-end'
 
```CSS
.links {
  border: 1px solid #fff;  /* For debugging */
  display: flex;
  justify-content: flex-end;
}
```

The output for your html file now looks like this:

![image](images/5.png)

Lets give the .Login element a left-margin so that there is some space between the SignUp and Login texts.

```CSS
.login {
  margin-left: 20px;
}
```
The output for your html file now looks like this:

![image](images/6.png)

We won’t need those white borders anymore, so we comment/delete them .

The styles.css now looks like this.

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
    /*border: 1px solid #fff;  !* For debugging *!*/
    width: 900px;
    display: flex;
    justify-content: space-between;
}
.links {
    /*border: 1px solid #fff;  !* For debugging *!*/
    display: flex;
    justify-content: flex-end;
}

.login {
    margin-left: 20px;
}
```

The output for your html file now looks like this:

![image](images/7.png)

So far, we’ve been manipulating horizontal alignment, but flex containers can also define the vertical alignment of their items. This is something that’s simply not possible with floats.

To explore this, we need to add a header underneath our menu. Add the following markup to flexbox.html after the .menu-container element:
```HTML
<div class='header-container'>
  <div class='header'>
    <div class='subscribe'>Subscribe &#9662;</div>
    <div class='logo'><img src='images/awesome-logo.svg'/></div>
    <div class='social'><img src='images/social-icons.svg'/></div>
  </div>
</div>
```
Add the following lines to styles.css
```CSS
.header-container {
  color: #5995DA;
  background-color: #D6E9FE;
  display: flex;
  justify-content: center;
}

.header {
  width: 900px;
  height: 300px;
  display: flex;
  justify-content: space-between;
}
```

The output for your html file now looks like this:

![image](images/8.png)

The 'align-items' property defines the default behavior for how items are laid out along the cross axis (perpendicular to the main axis).
We have a horizontal flexbox layout. That horizontal flow is the main axis, so align-items is the alignment opposite that, on the vertical axis.
You can think of align-items as the justify-content version for the cross-axis (perpendicular to the main-axis).
The possible values of 'align-items' are:
* flex-start
* flex-end
* center
* baseline
* stretch

As we can see presently the flex-items inside the header are aligned to the topside of the header, lets add the following code to align the items to the center.
```CSS
.header {
    width: 900px;
    height: 300px;
    display: flex;
    justify-content: space-between;
    align-items: center;// add this line
}
```

The output for your html file now looks like this:

![image](images/9.png)

We see that the 'subscribe' text and the 'social' icons are aligned at the center, but we want them at the bottom edge of the header
To do this we add the following code to the CSS file.
```CSS
.social,
.subscribe {
   align-self: flex-end;
    margin-bottom: 20px;
}
```
The align-self property specifies the alignment for the selected item inside the flexible container.

The align-self property overrides the flexible container's align-items property.So the previously written 
'align-items:centre' does not apply .

The output for your html file now looks like this:

![image](images/10.png)

Lets now create the photo-grid-container
Add the following lines of code to flexbox.html
```HTML
<div class='photo-grid-container'>
</div>
```
Lets make it a flex-container and align the flex-items inside it to center
```CSS
.photo-grid-container {
    display: flex;
    justify-content: center;
}
```


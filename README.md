# sass-and-tailwind



## Sass - Syntactically Awesome Style Sheets
![](https://sass-lang.com/assets/img/styleguide/color-1c4aab2b.png)

What is Sass? Sass is a CSS extension language. This allows us to write CSS in a more synactically friendly way, that will be compiled to normal CSS. Sass allows us to use variables, nested rules, functions, and more! This can help keep your stylesheets well-organized and easier to read!

When it comes to websites, web browsers generally are only able to read files with `.html` `.css` and `.js` extensions. However, all Sass code is written in `.scss` files, rather than with the traditional `.css` extension. So how does the browser read these weird `.scss` files? 

Sass will take the code written in a `.scss` file and compile it to a `.css` file for you. How do we compile files like this?? Well, first we need to install Sass!

### Installing Sass

Since we previously installed `homebrew` during installfest, installing Sass with homebrew will be our best bet! To install using homebrew, run the following command anywhere in your terminal

```zsh
brew install sass/sass/sass
```

<details>
    <summary>For Linux Users</summary>
    
For Linux, we will use the `Node` version. It is a JavaScript implementation of Sass, which does run a little slower. For our use in this class, you should have no problems. The interface is the same! And its easy to change to another implementation in the future if needed!

```zsh
npm install -g sass
```
</details>

Now that Sass is installed, we can use it to compile our `.scss` files!

### Getting Started with Sass

Open up the `sass` directory and `touch style.scss` to create our first sass file. Now, inside of our `style.scss` file, lets add some styling to the `h1` tag inside of `index.html`. 

```css
h1 {
    color: 'red';
}
```

Now we need to compile our `style.scss` into a `.css` file! In order to do this, we can run the following command
```zsh
sass style.scss style.css
```

This tells Sass to look for a `style.scss` file and compile it to a `style.css` file. You will now see that a `style.css` and a `style.css.map` file were generated! Now we can add the `style.css` to a `<link>` tag in our `index.html`.

**Note**: When working with Sass, do not edit the `style.css` file directly. Only make changes inside of the `style.scss` file.

Its a lot of work to *constantly* have to recompile the `style.scss` file. Fortunately, Sass can automatically watch for changes and compile automatically! In order to do this, we just need to add a `--watch` flag to our command!

```zsh
sass --watch style.scss style.css
```

Your terminal should now look similar to this
```zsh
$ sass --watch style.scss style.css
Sass is watching for changes. Press Ctrl-C to stop.
```

Now Sass is automatically looking for changes to the `style.scss` file! Give it a try. Change the color of the `<h1>` tag inside of `style.scss`.

### Sass Nesting

One of the greatest benefits of using Sass, is that it allows us to nest elements just like we do in `HTML`. For example, lets say inside of our `index.html` we add an `<ul>` with multiple `<li>` elements.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Document</title>
</head>
<h1>Learn Sass</h1>
    <ul>
        <li>Nesting</li>
        <li>Variables</li>
        <li>Functions</li>
    </ul>
</html>
```

When looking at the `index.html`, its easy to tell the the `<li>` elements are children of the `<ul>` element. Unfortantely, normal css doesn't work like that. Using normal css, we would have to style the `<ul>` and `<li>` as seperate elements. For example:
```css
ul {
    border: 2px solid black;
}

li {
    font-size: 30px;
}
```

Looking at the css file, its not obvious that the li is a child of the ul. In Sass, we can write the css like this:

```css
ul {
    border: 2px solid black;
    li {
        font-size: 30px;
    }
}
```
This is so much easier to understand! Thank you Sass!!

Also, only `<li>` tags that are inside of a `<ul>` will be styled! A lone `<li>` outside of the `<ul>` will *not* be styled. So Sass helps with the specificity of elements! If we grab an element by its id or class in the `style.scss` file, we can ensure that we are only styling elements *inside* of that element.

### Variables in Sass

Yes Sass has variables! Just like Javascript does! Anyone want to DRY up their CSS??

Sass variables can store things like colors, fonts, or any other type of CSS value you want to reuse! In order to use a variable in Sass, you first need to declare it! To declare variables in Sass, you start with the `$` symbol.

```css
$primary-color: #48C9B0;
$secondary-color: #515A5A;
```
Now we can style our page with these variables!

```css
$primary-color: #48C9B0;
$secondary-color: #515A5A;

body {
    background-color: $primary-color;
}

h1 {
    color: $secondary-color;
}

ul {
    border: 2px solid black;
    color: $secondary-color;
    li {
        font-size: 30px;
    }
}
```

### Functions in Sass

Yes Sass has functions!! You can create your own functions, or utilize some of the built in ones. For the purpose of this lesson, we will just use the `mix()` built in function.

Our secondary color is a little light for text. Lets use the `mix()` function to mix our color with black to make our text in the `<h1>` and the `<ul>` a little darker!

```css
$primary-color: #48C9B0;
$secondary-color: #515A5A;

body {
    background-color: $primary-color;
}

h1 {
    color: mix(black, $secondary-color, 30%);
}

ul {
    border: 2px solid black;
    color: mix(black, $secondary-color, 30%);
    li {
        font-size: 30px;
    }
}
```

Sass has so many built in features such as Partials, Modules, Mixins, Inheritance and even Operators! I encourage you to dive into Sass at some point in your career. It will make working with CSS so much more flexible!


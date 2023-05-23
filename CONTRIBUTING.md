# Contributing
Anyone is welcome to contribute to the development of this theme. It can be a lot of work to keep up on, and I'll take help wherever i can get it :)

## Getting The Code

### 1. Fork
If you're keen to contribute, start by the repo and cloning it to your computer.

### 2. Make Some Changes

Once this is complete you will be able to edit seti files.

### 3. Create a Pull Request

Once you are satisfied, with your updates, commit your change, push them to your fork and submit a pull request with a description of the changes that you made.


-----

## Basics
The first thing you should probably do is review the guide on creating a theme in [the flight manual](http://flight-manual.atom.io/hacking-atom/sections/creating-a-theme/) to make sure you have a basic understanding of how themes in Atom work. Aside from that, here's the basic you need to know on how Seti is structured:

#### Colors
##### [styles/ui-variables.less](styles/ui-variables.less)
All color variables are stored in this file. Theme colors have been carefully chosen, so please don't modify them unless you have a good reason.

-----

## Adding File Icons
The process of adding file icons is still a bit complex, but it _has_ been greatly simplified in 1.0. It does however require that you have [node](https://nodejs.org/en/) and [gulp](https://github.com/gulpjs/gulp/blob/master/docs/getting-started.md) installed.

Once you have these, you will need to open a terminal window, navigate to the _seti-pro_ folder and run `npm install` (note you only need to do this once).

Once everything is setup, follow these steps any time you want to add a new icon:

  1. Create an SVG icon with the name of the language, and save it to the `icons` folder _(do not use any spaces or special characters)_

  2. Navigate to the _seti-pro_ folder in your terminal and run `gulp font` (this will add the new svg file to our icon font, update our file as well as the less file with the mixins we'll need to link to the icon later.)

  3. Lastly, open [styles/icons/mapping.less](styles/icons/mapping.less) and create a link for the icon you just added with the `.icon-set` mixin. Assuming you were adding an icon for Sass it might look something like this: ```.icon-set('.scss', 'sass', @pink)```

  The first parameter `'.scss'` is the file extension you want to target, the second parameter `'sass'` is the name of the icon you just created, without the extension (sass.svg), and the last parameter `@pink` indicated what color the icon should be.

  There are currently 9 supported icon colors:
    - @blue
    - @grey
    - @green
    - @orange
    - @pink
    - @purple
    - @red
    - @white
    - @yellow


  While, you _can_ add additional colors to [styles/ui-variable.less](styles/ui-variable.less), but please do not do this unless you find it _absolutely_ necessary. If you do add another color, please make sure that matches the general feel of the other colors. If you add something really bright or really pale, your pull request will likely be declined.

  You will need to do this once for every extension, you want to target. For example, ir you want to target both **.sass** and **.scss** extensions, you would add the following:

```less
.icon-set('.sass', 'sass', @pink);
.icon-set('.scss', 'sass', @pink);
```

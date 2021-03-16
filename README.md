# SCSS Boiler Plate For Piranha CMS Manager
A starter template/boilerplate for quickly styling the manager in piranha cms.

*No Margins, Paddings or Positions was harmed during the making of this boiler plate*

## Screenshots
|         |            |
| ------------- |:-------------:|
| ![pages2](/images/pages.png)     | ![pageedit](/images/PageEdit.png) |
| ![config](/images/Config.png)     | ![media](/images/Media.png)      |



# Getting Started
## Add the files to the project
Copy the manager folder & manager.scss from the *'src'* folder into *'assets/scss'* like below.

![filelocation](/images/filelocation.png)

## Editing the gulp.js file
Depending on how you are compiling your scss files you may need to add the following to your gulp file like so

```javascript
gulp.src('assets/scss/manager.scss')
        .pipe(sass().on('error', sass.logError))
        .pipe(cssmin())
        .pipe(rename({
            suffix: ".min"
        }))
        .pipe(gulp.dest('wwwroot/assets/css'));
```

The final gulp file should look something like this.
```javascript
var gulp = require('gulp'),
    sass = require('gulp-sass')
    cssmin = require("gulp-cssmin")
    rename = require("gulp-rename");

gulp.task('min', function (done) {
    gulp.src('assets/scss/style.scss')
        .pipe(sass().on('error', sass.logError))
        .pipe(cssmin())
        .pipe(rename({
            suffix: ".min"
        }))
        .pipe(gulp.dest('wwwroot/assets/css'));

    gulp.src('assets/scss/manager.scss')
        .pipe(sass().on('error', sass.logError))
        .pipe(cssmin())
        .pipe(rename({
            suffix: ".min"
        }))
        .pipe(gulp.dest('wwwroot/assets/css'));

    done();
});
```
## Add the style sheet to the manager.
More information can be found in the [Piranha Documentation](https://piranhacms.org/docs/master/manager-extensions/resources)
```c#
public void Configure(IApplicationBuilder app, IWebHostEnvironment env, IApi api)
{
    // Add this line to existing setup code
    App.Modules.Manager().Styles.Add("~/assets/css/manager.min.css");
}
```

# Colors 
Color pallete used in this style can be found on [COOLORS.CO](https://coolors.co/af2020-328731-1e6dae-0b060e-351353-602296-c43477)

![ColorPallete](/images/ColorPallete.png)

### Delete and/or change these colors to match your color pallete

```scss
// Main Theme Colors
$xiketic: rgb(11, 6, 14);
$ksu-purple: rgb(96, 34, 150);
$russian-violet: rgb(53, 19, 83);
$telemagenta: rgb(196, 52, 119);

// Used for text
$white: #fff;
$black: #000;

// Other colors used in the manager for things like delete and add buttons
$blue: rgb(30, 109, 174);
$red: rgb(175, 32, 32);
$green: rgb(50, 135, 49);
```

# Quick Settings
These settings are used throughout *'manager/_theme.scss'* and allow for quickly making changes to the managers appearance. The above color pallete variables are only referenced in this section and the below variables and then used throughout the rest of the boilerplate making it easy to quickly adjust a color =)

```scss
$bg-color-dark: $xiketic;
$bg-color-medium: $russian-violet;
$bg-color-light: $ksu-purple;

$border-color-dark: $xiketic;
$border-color-medium: $russian-violet;
$border-color-light: $ksu-purple;

$text-white: $white;
$text-light: $telemagenta;
$text-medium: $russian-violet;
$text-dark: $xiketic;
$text-black: $black;
$muted-text: $telemagenta;

$code-text-color: $text-light;

$info: $blue;
$success: $green;
$danger: $red;
```

So as an example lets change the background dark color to *red*
```scss
$bg-color-dark: $red;
```
![BackgroundColorChange](/images/BackgroundColorChange.png)

Lets also change the background medium color to green

```scss
$bg-color-medium: $green;
```
![BackgroundMediumColorChange](/images/BackgroundMediumColorChange.png)

As you can see making changes to these settings makes changes throughout the manager.

*Setting a random color to these settings will allow you to quickly identify what is being used where*

# Further Changes

Further changes can be made by adjusting the relevant variable in *'manager/_theme.scss'* these variables have been names with as descriptive names as i could possibly come up with so hopefully wont be to hard to find what you are looking for. As an example lets make a change to the sitemap item and change the background color to *yellow* and foreground color to *black*

```scss
// ** Sitemap Settings
$sitemap-item-bg: yellow;
$sitemap-item-handle-color: $text-black;
$sitemap-item-link-color: $text-black;
$sitemap-item-type-color: $text-black;
$sitemap-item-date-color: $text-black;
```

![SitemapItem](/images/SitemapItem.png)

# Final Notes
This boilerplate is by no means a complete solution but more designed to allow a color scheme to be quickly applied to the manager.

This has also been put together quickly and will in future be refactored to be a more complete solution.
# Guide for Naming Assets in iOS Projects

This guide outlines [naming conventions](#naming) to help graphic designers and developers manage image icons (or assets) generated for iOS projects. 

Your input is welcome: [issues](https://github.com/dkhamsing/ios-asset-names/issues), [pull requests](https://github.com/dkhamsing/ios-asset-names/pulls), [twitter](https://twitter.com/alldonegoodbye).

## Table Of Contents
* [Folders](#folders)
* [Format](#format)
* [Naming](#naming)
	* [Prefixes](#prefixes)
	* [Conventions](#conventions)
	* [Special cases](#special-cases)
	* [Collisions](#collisions)
	* [Spelling](#spelling)
	* [Abbreviations](#abbreviations)
* [Acknowledgment](#acknowledgement)


## Folders
* Use a main folder (usually named `assets` or `images`) 
* Organize the assets in subfolders named after sections or logical grouping of the app (agree on the subfolder names when reviewing the mockups/designs)
* Use lower case
* No spaces or special characters (use dashes)

**Format**

```
assets/subfolder/
```

**Examples**

```
images/top/
images/about/
images/web-browser/
images/share/
images/tutorial/ 
```

## Format

* Use the [PNG format](http://en.wikipedia.org/wiki/Portable_Network_Graphics) when possible
* Determine if transparency is needed ([UIButton tap issue](http://stackoverflow.com/questions/17368803/how-can-i-make-uibutton-respond-to-touch-on-the-transparent-areas-of-a-png-image))
* Create 1x and 2x assets in the same folder 
* Add `@2x` at the end of the [retina asset name](https://developer.apple.com/library/mac/documentation/GraphicsAnimation/Conceptual/HighResolutionOSX/Optimizing/Optimizing.html)

```
asset.png
asset@2x.png
```

## Naming

### Prefixes

* Prefix the asset with a 2-letter prefix (or 3-letter) representing the `project` so you can tell which project it belongs to
* Subsequently, prefix the asset using the `folder` name so you can tell which folder it belongs to 

**Format**

```
project-folder-asset-name.png
```

**Examples**

```
ss-intro-arrow-right.png 
bpc-intro-arrow-right.png 
```

### Conventions

* **The asset name describes the icon**, not the function of the icon (when possible, there are also [special cases](#special-cases))
* Use lower case
* No spaces or special characters (use dashes)

**Examples**
```
ss-rack-minus.png 
ss-top-bars.png 
ss-tree-check.png
```

**Not**

```
delete.png 
menu.png
selected.png
```

#### Notable

* `chevron` for >
* `caret` for ►

#### Special cases 

Sometimes the name is well represented by its function (see [Charbase](http://www.charbase.com/21bb-unicode-clockwise-open-circle-arrow))

* `refresh` for ⟳ open circle arrow (U+21BB)  
* `edit` for ✎ pencil (U+270E) 
* `search` for 🔍 magnifying glass (U+1F50D) 
* `user` for 👤 bust in silhouette (U+1F464) 

#### Collisions 

If two assets have the same name (should be rare thanks to the folder prefix), try to use a qualifier at the end.


Color qualifer

```
ss-top-plus-pink.png
ss-top-plus-gray.png
```

Shape qualifer

* `*-square` 
* `*-circle`
* `*-o` for outline

```
ss-top-arrow-right-circle.png
ss-top-arrow-right-square.png
```

Combine shapes

* `*-square-o` for square outline


Direction qualifer (always at the end)

* `*-right`
* `*-left`
* `*-up`, etc

```
ss-top-arrow-right.png
ss-top-arrow-square-right.png
```


### Spelling

Use American over British spelling (sorry M'lady)

**Examples**
```
ss-top-hanger-gray.png  
ss-tree-color-swatch.png 
```

**Not**

```
hanger-grey.png  
colour-swatch.png 
```

### Abbreviations

Do not abbreviate

**Examples**
```
ss-share-facebook.png 
ss-share-twitter.png  
```

**Not**
```
fb.png
tw.png
```

## Acknowledgment

This guide was inspired by the [NYTimes Objective-C Style Guide](https://github.com/NYTimes/objective-c-style-guide) and [Font Awesome](http://fontawesome.io/) naming conventions.


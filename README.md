# Guide for Naming Assets in iOS Projects

This guide outlines [naming conventions](#naming) to help graphic designers and developers manage a large number of assets (images) prepared for iOS projects. 

Your input is welcome: [issues](https://github.com/dkhamsing/ios-asset-names/issues), [pull requests](https://github.com/dkhamsing/ios-asset-names/pulls), or [twitter](https://twitter.com/alldonegoodbye).

## Table Of Contents
* [Folders](#folders)
* [Asset Type](#asset-type)
* [Naming](#naming)
	* [Prefixing](#prefixing)
	* [Conventions](#conventions)
	* [Special cases](#special-cases)
	* [Collisions](#collisions)
	* [Spelling](#spelling)
	* [Abbreviations](#abbreviations)
* [Acknowledgment](#acknowledgement)


## Folders

* If you are using Xcode 5's [Asset Catalogs](https://developer.apple.com/library/ios/recipes/xcode_help-image_catalog-1.0/Recipe.html), folders are created automatically and you can skip [ahead](#asset-type).
* Use a main folder to store the assets (usually named `assets` or `images`).
* Subfolders are useful if the number of assets is overwhelming, the idea is to break the user interface in sections / logical groupings and have subfolders representing them (agree on the subfolder structure and names when reviewing the mockups/designs). 
* Use lower case.
* No spaces or special characters (use dashes).
* Format: `images`/`subfolder`/


```
images/top/
images/about/
images/web-browser/
images/share/
images/tutorial/ 
```

For universal apps, it might be worthwhile to add one more folder level named after the device: `images`/`iphone`/`subfolder`, `images`/`ipad`/`subfolder` (see Apple's [device modifier convention](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/App-RelatedResources/App-RelatedResources.html), especially for launch images).

## Asset Type

* Use the [PNG format](http://en.wikipedia.org/wiki/Portable_Network_Graphics) when possible
	* Determine if transparency is needed ([UIButton tap issue](http://stackoverflow.com/questions/17368803/how-can-i-make-uibutton-respond-to-touch-on-the-transparent-areas-of-a-png-image))
* Create 1x and 2x assets in the same folder 
* Add `@2x` at the end of the [retina asset name](https://developer.apple.com/library/mac/documentation/GraphicsAnimation/Conceptual/HighResolutionOSX/Optimizing/Optimizing.html)

```
asset.png
asset@2x.png
```

To save disk space or time, one can omit the 1x or 2x asset: the system automatically scales up or down for the appropriate resolution (in particular, you could provide only 2x assets when targeting retina devices). 

## Naming

### Prefixing

* Prefixing is optional (it could be redudant).
* Prefix the asset with a 2 or 3 letter prefix representing the `project` so you can tell which project it belongs to.
* If you are not using Asset Catalogs: add another prefix using the `folder` name so you can tell which folder it belongs to. 
* Format: `project`-`folder`-`asset-name`.png

```
ss-intro-arrow-right.png 
bpc-intro-arrow-right.png 
```

### Conventions

* **The asset name describes the icon**, not the function of the icon (when possible, see [special cases](#special-cases)).
* Use lower case.
* No spaces or special characters (use dashes).

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

While CamelCase is the convention in Objective-C, it does not necessarily mean it needs to be applied to asset names (by all means feel free to use it if you prefer `SSRackMinus.png`).

#### Notable

* `chevron` for `>`
* `caret` for `►`

#### Special cases 

Sometimes the name is well represented by its function (refer to [Charbase](http://www.charbase.com/21bb-unicode-clockwise-open-circle-arrow) for Unicode).

* `refresh` for `open circle arrow` (⟳ U+21BB)  
* `edit` for `pencil` (✎ U+270E) 
* `search` for `magnifying glass` (🔍 U+1F50D) 
* `user` for `bust in silhouette` (👤 U+1F464) 
* `comment` for `speech balloon` (💬 U+1F4AC)

#### Collisions 

Should two assets have the same name, add a qualifier at the end.


##### Color qualifer

```
ss-top-plus-pink.png
ss-top-plus-gray.png
```

##### Shape qualifer

* `*-square` 
* `*-circle`
* `*-o` for outline

```
ss-top-arrow-right-circle.png
ss-top-arrow-right-square.png
```

##### Combine shapes

* `*-square-o` for square outline

##### Direction qualifer (always at the end)

* `*-right`
* `*-left`
* `*-up`, etc

```
ss-top-arrow-right.png
ss-top-arrow-square-right.png
```

### Spelling

Use American over British spelling (sorry M'lady).

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

Do not abbreviate.

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

This guide was inspired by the [NYTimes Objective-C Style Guide](https://github.com/NYTimes/objective-c-style-guide) and the [Font Awesome](http://fontawesome.io/) naming conventions.

Special thanks to the following individuals for their feedback: [Ash Furrow](https://github.com/AshFurrow), [Sergio Campama](https://github.com/sergiocampama), [Matteo Crippa](https://github.com/matteocrippa), [Marco Sousa](https://news.layervault.com/stories/13379-guide-for-naming-assets-in-ios-projects). 

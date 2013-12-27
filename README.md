# Guide for Naming Assets in iOS Projects

This guide outlines naming conventions to help graphic designers and developers manage image icons (or assets) generated for iOS projects. 

Your input is welcome ([issues](https://github.com/dkhamsing/ios-asset-names/issues), [pull requests](https://github.com/dkhamsing/ios-asset-names/pulls), [twitter](https://twitter.com/alldonegoodbye)).


## Folders
* Use a main `assets` (or `images`) folder
* Organize the assets in subfolders named after sections or logical grouping of the app (agree on the subfolder names when reviewing the mockups/designs)
* Use lower case
* No spaces or special characters (use dashes)

```
assets/subfolder/

images/top/
images/about/
images/web-browser/
images/share/
images/tutorial/ 
```

## Assets / Format

* Create 1x and 2x assets in the same folder 
* The retina [asset name ends with @2x](https://developer.apple.com/library/mac/documentation/GraphicsAnimation/Conceptual/HighResolutionOSX/Optimizing/Optimizing.html)
* Use the [PNG format](http://en.wikipedia.org/wiki/Portable_Network_Graphics) when possible

```
asset.png
asset@2x.png
```


## Prefixes

* Prefix the asset with a 2-letter prefix (or 3-letter) representing the `project` so you can tell which project it belongs to
* Subsequently, prefix the asset using the `folder` name so you can tell which folder it belongs to 

```
project-folder-asset-name.png

ss-intro-arrow-right.png 
bpc-intro-arrow-right.png 
```


## Naming

* **The asset name describes the icon**, not the function of the icon (when possible)
* Use lower case
* No spaces or special characters (use dashes)

**For example:**
```
ss-rack-minus.png 
ss-top-bars.png 
ss-tree-check.png
```

**Not:**

```
delete.png 
menu.png
selected.png
```

### Collision

* If two assets have the same name (should be rare because of the folder prefix), try to use a qualifier at the end

```
ss-top-arrow-right-circle.png
ss-top-arrow-right-square.png

ss-top-badge-pink.png
ss-top-badge-gray.png
```

### Spelling

* Use American over British spelling (sorry M'lady)

**For example:**
```
ss-top-hanger-gray.png  
ss-tree-color-swatch.png 
```

**Not:**

```
hanger-grey.png  
colour-swatch.png 
```

### No abbreviations

**For example:**
```
ss-share-facebook.png 
ss-share-twitter.png  
```

**Not:**
```
fb.png
tw.png
```

### Conventions (if applicable)

```
*-o for outline
*-square
*-circle
*-right, *-up, etc

*-square-o for square outline

chevron for >
caret for ►
```

### Special cases
* The icon name is well represented by its function

```
ss-web-browser-refresh.png
ss-top-search.png
ss-rack-edit.png
ss-intro-user.png
```
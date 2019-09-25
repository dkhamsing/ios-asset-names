# Guide for Naming Assets in iOS Projects

This guide outlines best practices and [naming conventions](#naming) to help graphic designers and developers manage a large number of icons prepared for an iOS project.

Your input is welcome: [pull requests](https://github.com/dkhamsing/ios-asset-names/pulls) or [Twitter](https://twitter.com/dkhamsing) :smile:

## Table Of Contents

* [Namespace](#namespace)
* [Asset Folder](#asset-folder)
* [Asset Types](#asset-types)
  * [PNG](#png)
  * [PDF](#pdf)
  * [Icon Font](#icon-font)
* [Tools](#tools)
* [Naming](#naming)
	* [Uniqueness](#uniqueness)
	* [Prefixing](#prefixing)
	* [Conventions](#conventions)
	* [Special cases](#special-cases)
	* [Collisions](#collisions)
	* [Spelling](#spelling)
	* [Abbreviations](#abbreviations)
* [Acknowledgment](#acknowledgment)

## Namespace

Naming an asset starts with breaking up the user interface of each screen into *namespaces* (or sections). Each namespace represents a logical grouping for the assets and can be used to [create asset names](#naming).

* Shorter is better (one word if possible).
* Meaningful namespace name.
* Use lower case.
* No spaces or special characters (use dashes).

Namespaces can correspond to view controllers, typical namespaces are `top`, `bottom`, `content` although more specific names are better.

**Examples**

| Twitter Profile | Tumblr Home | Instagram Explore
| --- | --- | --- | 
| <img width=200 src=assets/namespace1.PNG> | <img width=200 src=assets/namespace2.PNG> | <img width=200 src=assets/namespace3.PNG>
| `top` <br> `actions` <br> `tweet` <br> `tab` | `post` <br> `tab` | `top` <br> `photo` <br> `tab`
 
## Asset Folder

* Using [Asset Catalogs](https://developer.apple.com/library/content/documentation/Xcode/Reference/xcode_ref-Asset_Catalog_Format/) is the preferred way to manage assets in Xcode, it eliminates keeping track of files in a project. However naming assets (image sets) remains important especially when collaborating with a designer.
* If you choose to manage assets directly, use a main folder to *store all assets* for the app (usually named `assets` or `images`). This may seem radical but it works in conjunction with [prefixing](#prefixing).
  * An alternative is to use subfolders for each namespace, be aware that subfolders can create problems with asset name [uniqueness](#uniqueness).
  * For extra credit, check out [Structuring an iOS Project](https://gist.github.com/sebreh/8d3ae08f9808ee1495d91aa03a2814d1) by [Sebastian Rehnby](https://github.com/sebreh) and the [Tools section](#tools).

## Asset Types

### PNG

[PNG](https://en.wikipedia.org/wiki/Portable_Network_Graphics) is typically used for icons (JPG is better for photos).

- PNG is good for small assets.
- PNG is non-lossy.
- PNG supports transparency.

To use PNG assets:

1. Create 1x, 2x and 3x assets in the same folder.
2. Add `@2x` or `@3x` at the end of the [appropriate asset name](https://developer.apple.com/library/content/documentation/GraphicsAnimation/Conceptual/HighResolutionOSX/Optimizing/Optimizing.html).

```
asset.png
asset@2x.png
asset@3x.png
```

To save disk space or time, one can omit the 1x, 2x or 3x asset: the system automatically scales up or down for the appropriate resolution (in particular, you could provide only 2x/3x assets when targeting retina devices).

### PDF

Xcode 6 added support for PDF / vector icons eliminating the need for multiple resolution per asset (goodbye 1x, 2x, 3x). However doing [so will](https://github.com/AliSoftware/OHPDFImage)

> re-create PNG assets at compile time, embedding the rasterized bitmaps in the final application instead of embedding the original PDF vector image.

If you add PDF files directly as resources, they can be used as vector assets which have no size restriction (like an [icon font](#icon-font)).

If you still want to use a PDF asset with assets catalogs, create an image set for each PDF asset in Xcode. Then in the Utility panel (right) set:

- Devices: `Universal`
- Scale Factors: `Single Vector`
- Render As: `Template Image` (corresponds to setting the `UIImageRenderingMode` property to `UIImageRenderingModeAlwaysTemplate`)

![](assets/xcode-panel.png)

This last setting allows an asset to be tinted (colored). If setting up a large number of assets sounds tedious, check out a tool appropriately called [`pdf_xcassets`](#tools).

PDF assets still need to be sized appropriately, i.e. the designer would provide 2 assets for an arrow if the mockup required assets sized `20x20` and `40x40`. For more details, read [this article](http://martiancraft.com/blog/2014/09/vector-images-xcode6/).

### Icon Font

Another alternative for icon generation is to use [icon fonts](http://fontawesome.io/). These can be scaled without quality loss and colored just like any text. For more details, read [this article](http://www.creativebloq.com/app-design/icon-fonts-in-apps-21410734).

## Tools

Here are some tools to help you manage your assets.

- [blade](https://github.com/jondot/blade): Generate Xcode image catalogs for iOS / OSX app icons, universal images, and more.
- [Cat2Cat](https://github.com/vokal/Cat2Cat): Generate a category on UIImage from asset catalogs in order to reduce typos and enable Xcode auto-completion.
- [OHPDFImage](https://github.com/AliSoftware/OHPDFImage): A library to easily load PDF files as UIImages.
- [pdf_xcassets](https://github.com/dkhamsing/pdf_xcassets):  Generate Xcode xcassets for pdf assets.
- [Synx](https://github.com/venmo/synx): A command-line tool that reorganizes your Xcode project folder to match your Xcode groups.

### Swift Enums

- [Misen](https://github.com/tasanobu/Misen): Script to support using Xcode Asset Catalog in Swift.
- [SwiftGen](https://github.com/AliSoftware/SwiftGen): A collection of Swift tools to generate Swift code (enums for your assets and more).

## Naming

### Uniqueness

An important attribute of an asset name is uniqueness.

* This prevents confusion: for example having two different `share` assets (say one for iPhone and one for iPad, or one in a main view and one in a detail view).
* More importantly, while it is possible in Xcode to have two files of the same names in different folders, you can only reference one of them using `+ (UIImage *)imageNamed:(NSString *)name`.
* **Update**: Asset catalogs support a namespace based on the asset "Group" that allows for the same name to be reused (read the [documentation](https://developer.apple.com/library/content/documentation/Xcode/Reference/xcode_ref-Asset_Catalog_Format/FolderStructure.html) or [summary](http://stackoverflow.com/questions/28076644/differentiating-images-in-an-asset-catalog-by-their-group/32854289#32854289)).

```json
"properties" : {
      "provides-namespace" : true
}
```

### Prefixing

Prefixing is optional but it ensures that asset names are unique across the project.

* Prefix the asset with the app name so you can tell which project it belongs to (use a 2 or 3 letter prefix for long app names).
* Add a device prefix (especially for universal apps with device-specific assets).
* Add a `namespace` prefix so you can quickly organize your assets.
* Format: `project`-`device`-`namespace`-`asset-name`.png

```
ss-ipad-intro-arrow-right.png
bpc-iphone-intro-arrow-right.png

twitter-iphone-top-user.png
twitter-iphone-top-search.png
twitter-iphone-top-write.png

tumblr-iphone-card-action.png
tumblr-iphone-card-comment.png
tumblr-iphone-card-reblog.png
tumblr-iphone-card-heart.png
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
* `*-outline` 

```
ss-top-arrow-right-circle.png
ss-top-arrow-right-square.png
```

##### Combine shapes

* `*-square-outline` for square and outline

##### Direction qualifer

* `*-right`
* `*-left`
* `*-up`, etc

```
ss-top-arrow-right.png
ss-top-arrow-square-right.png
```

##### Buttons (control states)

* `*-normal`
* `*-selected`
* `*-highlighted`, etc

```
ss-profile-gear-normal.png
ss-profile-gear-highlighted.png
```

##### Orientation

* `*-portrait`
* `*-landscape`
* `*-landscape-right`, etc

Apple recommends using [Xcode storyboards for launch screens](https://developer.apple.com/ios/human-interface-guidelines/graphics/launch-screen/).

### Spelling

In the US, we would favor American over British spelling (sorry M'lady).

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

This guide was inspired by the [NYTimes Objective-C Style Guide](https://github.com/NYTimes/objective-c-style-guide) and  [Font Awesome](http://fontawesome.io/).

Special thanks to the following individuals for their feedback: [Ash Furrow](https://github.com/AshFurrow), [Sergio Campama](https://github.com/sergiocampama), [Matteo Crippa](https://github.com/matteocrippa), [Marco Sousa](https://twitter.com/h1brd), [Dave McKinney](https://twitter.com/davidkmckinney).

## Contact

- [github.com/dkhamsing](https://github.com/dkhamsing)
- [twitter.com/dkhamsing](https://twitter.com/dkhamsing)

[![Version](https://cocoapod-badges.herokuapp.com/v/UIImage+Additions/badge.png)](http://cocoadocs.org/docsets/UIImage+Additions) 
[![Platform](https://cocoapod-badges.herokuapp.com/p/UIImage+Additions/badge.png)](http://cocoadocs.org/docsets/UIImage+Additions) 

![UIImage+Additions](https://raw.githubusercontent.com/vilanovi/UIImage-Additions/master/UIImageAdditionsLogo.jpg)

UIImage-Additions
=================

This category of UIImage add methods to generate dynamically images from colors, adding corner radius (for each corner), tinting images, etc. Use this category if you want to add "colored style" to your app without having to generate colored graphic resources.

Right now the category supports four types of operations:

###I. Create images for a color, size & corner radius

The folowing methods are used to generate a UIImage for a specific color, size and/or corner radius.

  	+ (UIImage*)add_imageWithColor:(UIColor*)color size:(CGSize)size;
	+ (UIImage*)add_imageWithColor:(UIColor*)color size:(CGSize)size cornerRadius:(CGFloat)cornerRadius;
	+ (UIImage*)add_imageWithColor:(UIColor*)color size:(CGSize)size cornerInset:(ADDCornerInset)cornerInset;

###II. Create resizable images for a color & corner radius

These methods are perfect to use inside `UIButton`s or `UIImageView`s if you are plannig to add a specific background color with a corner radius but you don't want to use `QuartzCore`. Also, you can specify which corner you want to round.

	+ (UIImage*)add_resizableImageWithColor:(UIColor*)color;
	+ (UIImage*)add_resizableImageWithColor:(UIColor*)color cornerRadius:(CGFloat)cornerRadius;
	+ (UIImage*)add_resizableImageWithColor:(UIColor*)color cornerInset:(ADDCornerInset)cornerInset;
	

###III. Generate image with rounded corners

You can use these methods to get a corner rounded image version from a current image.

	- (UIImage*)add_imageWithRoundedBounds;
	- (UIImage*)add_imageWithCornerRadius:(CGFloat)cornerRadius;
	- (UIImage*)add_imageWithCornerInset:(ADDCornerInset)cornerInset;
	- (BOOL)add_isValidCornerInset:(ADDCornerInset)cornerInset;
	
###IV. Generate tinted image from existing image

In order to avoid to generate multiple versions of the same image to use in different states (in `UIButton` for example), your designers can just create a single version and with these methods you can generate tinted versions of the same image. 

	+ (UIImage*)add_imageNamed:(NSString *)name tintColor:(UIColor*)color style:(ADDImageTintStyle)tintStyle;
	- (UIImage*)add_tintedImageWithColor:(UIColor*)color style:(ADDImageTintStyle)tintStyle;
	
You can use the following tint styles:

* Use `ADDImageTintStyleKeepingAlpha` to keep transaprent pixels and tint only those that are not translucid.
* Use `ADDImageTintStyleOverAlpha` to keep non transparent pixels and tint only those that are translucid.
* Use `ADDImageTintStyleOverAlphaExtreme` to remove (turn to transparent) non transparent pixels and tint only those that are translucid.

###V. Superposing images

You can easily create an image by superposing two images. Calling the method:

	- (UIImage*)add_imageAddingImage:(UIImage*)image offset:(CGPoint)offset;

The result is an image with the caller image as background and the given image as a top image. Also, you can specify an offset for the top image.

###VI. Generate Gradients
You can create linear gradient images (with two colors or more) using the following methods:

	+ (UIImage*)add_imageWithGradient:(NSArray*)colors size:(CGSize)size direction:(ADDImageGradientDirection)direction;
	+ (UIImage*)add_resizableImageWithGradient:(NSArray*)colors size:(CGSize)size direction:(ADDImageGradientDirection)direction;

The first method returns an image with a gradient using the specified colors and direction of the given size.
The second method returns the smallest resizable image that can generate the desired gradient for the given size.

* Use `ADDImageGradientDirectionVertical` to generate a vertical gradient.
* Use `ADDImageGradientDirectionHorizontal` to generate a horizontal gradient.
* Use `ADDImageGradientDirectionLeftSlanted` to generate a left-diagonal gradient.
* Use `ADDImageGradientDirectionRightSlanted` to generate a right-diagonal gradient.

### Notes

1. This category take care of scaling properties depending of the device resolution (retina or not) or the original image scale property.
2. All static methods cache images so two consequtives calls with the same parameters returns the same image.

---
## Licence ##

Copyright (c) 2013 Joan Martin, vilanovi@gmail.com.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE

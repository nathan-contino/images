# Images
This repository contains images and other blobs that I use on my website.

By storing this content here, instead of on my blog, my Jekyll site stays lean, mean, and quick to deploy.

Below, you'll see my old instructions for generating thumbnails and reasonably sized images. I've since moved to webp, so you can instead:

```
brew install webp
```

or

```
sudo apt install webp
```

First, export an album of images into a directory, using the name pattern `YYYY-MM-DD-post-title`.

Use the following command to generate WEBPs equivalents of all images in your directory:

```
find . -iname "*.png" -o -iname "*.PNG" -o -iname "*.jpg" -o -iname "*.JGP" -o -iname "*.jpeg" -exec sh -c 'cwebp -q 85 -mt "$1" -o "${1%.*}.webp"' sh {} \;
```

After generating the WEBP images, feel free to delete the original images; the WEBPs should be close enough in quality, and a _lot_ smaller.

Then:

. Create folders with the same name in `reasonable-images` and `thumbnails/images`.
. Navigate into the `images` folder that contains your new images, and use the following commands to generate reasonably sized images, then thumbnails:

```
find . -iname "*.webp" -exec sh -c 'cwebp -q 85 -mt -resize 2000 0 "$1" -o "../../reasonable-images/<folder name here>/${1%.*}.webp"' sh {} \;
```
```
find . -iname "*.webp" -exec sh -c 'cwebp -q 85 -mt -resize 1000 0 "$1" -o "../../thumbnails/images/<folder name here>/${1%.*}.webp"' sh {} \;
```

Double check that the images look correct, haven't rotated, and have reasonable sizes (generally less than 1MB for "reasonable", and less than 250KB for thumbnails). If an image rotates, you can use the following `imagemagick` command to fix it:

```
magick convert <image>.webp -rotate 90 <image>.webp
```

You might have to run the command 2-3 times to get the image into the right orientation.

## Thumbnails

This repository uses a GitHub Action to automatically generate thumbnails less than 1000 pixels tall (or wide) for all images uploaded with relatively normal extensions.
Please keep full size images below 5MB in size, so users can view them directly on GitHub, instead of having to download them.

## Reasonable Images

After adding images to this repository, you should resize them to be vaguely reasonably sized.

* Add the original quality images in whatever format you want to the `images` folder. In the macOS Photos app, **File > Export > Export Unmodified Original** accomplishes this with "File Name" set to "Sequential" and an empty prefix (resulting in ascending numbers for image names).

* Add a reasonably-sized image (hopefully less than 5MB) in the `reasonable-images` folder. In the macOS Photos app, **File > Export > Export** accomplishes this. I prefer PNG images, and find a width of 2000 pixels usually gets under 5MB. As with the original quality images, use "Sequential" file names with no prefix to preserve your sanity when adding the images to a post.

* Add a thumbnail image (hopefully less than 500KB) in the `thumbnails` folder. In the macOS Photos app, **File > Export > Export** accomplishes this. I prefer PNG images, and find a width of 700 pixels usually gets under 500KB while looking decent enough in my posts. As with the original quality images, use "Sequential" file names with no prefix to preserve your sanity when adding the images to a post.
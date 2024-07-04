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

And then use the following command to generate webps for all images in your directory:

```
find . -iname "*.png" -o -iname "*.jpg" -o -iname "*.jpeg" -exec sh -c 'cwebp -q 85 -mt "$1" -o "${1%.*}.webp"' sh {} \;
```

Then, use the following command to generate reasonably sized images, then thumbnails (you may need to manually create the corresponding folders):

```
find . -iname "*.png" -o -iname "*.jpg" -o -iname "*.jpeg" -exec sh -c 'cwebp -q 85 -mt -resize 2000 "$1" -o "../reasonable-images/${1%.*}.webp"' sh {} \;
```

```
find . -iname "*.png" -o -iname "*.jpg" -o -iname "*.jpeg" -exec sh -c 'cwebp -q 85 -mt -resize 1000 "$1" -o "../thumbnails/${1%.*}.webp"' sh {} \;
```

This finds images with the (case-insensitive) file extensions `png`, `jpg`, and `jpeg`, then executes the `cwebp` command to generate an 85% quality webp version of the image.

Then you can use these commands to delete the original images (hopefully you saved a full copy elsewhere?):

```
find . -iname "*.jpg" -exec sh -c 'rm -rf "$1"' sh {} \;

find . -iname "*.png" -exec sh -c 'rm -rf "$1"' sh {} \;

find . -iname "*.jpeg" -exec sh -c 'rm -rf "$1"' sh {} \;
```

## Thumbnails

This repository uses a GitHub Action to automatically generate thumbnails less than 1000 pixels tall (or wide) for all images uploaded with relatively normal extensions.
Please keep full size images below 5MB in size, so users can view them directly on GitHub, instead of having to download them.

## Reasonable Images

After adding images to this repository, you should resize them to be vaguely reasonably sized.

* Add the original quality images in whatever format you want to the `images` folder. In the macOS Photos app, **File > Export > Export Unmodified Original** accomplishes this with "File Name" set to "Sequential" and an empty prefix (resulting in ascending numbers for image names).

* Add a reasonably-sized image (hopefully less than 5MB) in the `reasonable-images` folder. In the macOS Photos app, **File > Export > Export** accomplishes this. I prefer PNG images, and find a width of 2000 pixels usually gets under 5MB. As with the original quality images, use "Sequential" file names with no prefix to preserve your sanity when adding the images to a post.

* Add a thumbnail image (hopefully less than 500KB) in the `thumbnails` folder. In the macOS Photos app, **File > Export > Export** accomplishes this. I prefer PNG images, and find a width of 700 pixels usually gets under 500KB while looking decent enough in my posts. As with the original quality images, use "Sequential" file names with no prefix to preserve your sanity when adding the images to a post.
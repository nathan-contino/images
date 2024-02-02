# Images
This repository contains images and other blobs that I use on my website.

By storing this content here, instead of on my blog, my Jekyll site stays lean, mean, and quick to deploy.

## Thumbnails

This repository uses a GitHub Action to automatically generate thumbnails less than 1000 pixels tall (or wide) for all images uploaded with relatively normal extensions.
Please keep full size images below 5MB in size, so users can view them directly on GitHub, instead of having to download them.

## Reasonable Images

After adding images to this repository, you should resize them to be vaguely reasonably sized.

* Add the original quality images in whatever format you want to the `images` folder. In the macOS Photos app, **File > Export > Export Unmodified Original** accomplishes this with "File Name" set to "Sequential" and an empty prefix (resulting in ascending numbers for image names).

* Add a reasonably-sized image (hopefully less than 5MB) in the `reasonable-images` folder. In the macOS Photos app, **File > Export > Export** accomplishes this. I prefer PNG images, and find a width of 2000 pixels usually gets under 5MB. As with the original quality images, use "Sequential" file names with no prefix to preserve your sanity when adding the images to a post.

* Add a thumbnail image (hopefully less than 500KB) in the `thumbnails` folder. In the macOS Photos app, **File > Export > Export** accomplishes this. I prefer PNG images, and find a width of 700 pixels usually gets under 500KB while looking decent enough in my posts. As with the original quality images, use "Sequential" file names with no prefix to preserve your sanity when adding the images to a post.
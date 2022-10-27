# Images
This repository contains images and other blobs that I use on my website.

By storing this content here, instead of on my blog, my Jekyll site stays lean, mean, and quick to deploy.

## Thumbnails

This repository uses a GitHub Action to automatically generate thumbnails less than 1000 pixels tall (or wide) for all images uploaded with relatively normal extensions.
Please keep full size images below 5MB in size, so users can view them directly on GitHub, instead of having to download them.

## Reasonable Images

After adding images to this repository, you should resize them to be vaguely reasonably sized.

I like to use the `recursive-resize` NPM module for this.

To install the module globally:

```
npm install -g recursive-resize
```

To generate reasonable image sizes for all the raw images stored in this repo:

```
recres -i images/ -o reasonable-images/ -w 2000
```

Voila! The reasonable images are all 2000 pixels wide, so plenty nice looking. But they should also end up less than 1MB in size. And if you ever need the FULL size image, you can still access it in `/images`.

# The (New) Klog

## Getting Started

Install prereqs:

    sudo apt-get install ruby ruby-dev

Install jekyll

    sudo gem install jekyll jekyll-paginate



## Developing

Get jekyll to show serve the site locally:

    jekyll serve

Jekyll will automatically regenerate the site when you save changes.
To see the site, go to `localhost:4000` in a browser.



## Adding images to a post

Images should be at most 900 pixels wide.

`scp` the images to `litomisky.com/klog-jekyll-img/posts/YY-MM-DD-GALLERYNAME`,
where `GALLERYNAME` is the name of the new gallery.

In the post, set the `photos_dir` variable to the `GALLERYNAME` from the previous step.

When adding the images in the post itself, just enter the filename (no path);
the `photos_dir` variable will be used automatically.

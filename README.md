# The Klog

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

Images will be displayed at most 900px wide in the post.
This Klog now also uses [Lightbox](https://lokeshdhakar.com/projects/lightbox2)
to show images in a larger size in a Lightbox.

You may find it easiest to use the [unklogger repo](https://github.com/krystofl/unklogger) to create posts with images; it does the below steps automatically.

`scp` the images to `litomisky.com/klog-jekyll-img/posts/YY-MM-DD-GALLERYNAME`,
where `GALLERYNAME` is the name of the new gallery.

In the post, set the `photos_dir` variable to the `GALLERYNAME` from the previous step.

When adding the images in the post itself, just enter the filename (no path);
the `photos_dir` variable will be used automatically.

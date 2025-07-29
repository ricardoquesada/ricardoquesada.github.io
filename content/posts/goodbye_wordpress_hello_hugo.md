---
author: ricardoquesada
category: misc
tag:
- hugo
- wordpress
date: '2025-01-15T07:56:12-08:00'
title: 'Goodbye WordPress, Hello Hugo'
url: /2025/01/15/migrate_wordpress_to_hugo_in_github_pages/
---

I've been using [WordPress][wordpress] for many years.
I started using it ~2008 to host the [Cocos2d][cocos2d_wikipedia] blog.
And then I used it for my personal blogs.

But I've been wanting to switch to a static site generator for a while.
And I finally did it.
I'm now using [Hugo][gohugo] hosted in [GitHub Pages][github_pages].
And this is how I did it:

[wordpress]: https://wordpress.com/

[cocos2d_wikipedia]: https://en.wikipedia.org/wiki/Cocos2d

[gohugo]: https://gohugo.io/

[github_pages]: https://pages.github.com/

### Export your files

1. Log in to your WordPress site as "admin"
2. Tools -> Export
3. Export "content"
    - Optionally export "media library" as well, but won't be used in this
      guide.
4. Unzip it

![](/images/2025_01_15_wordpress_tools_export.png)
<img src="/images/2025_01_15_wordpress_export_options.png" width="500px" />

### Download and run wp2hugo

There are [different ways][migrate_to_hugo] to migrate to Hugo.
The one that I tried was `wp2hugo`, and it worked reasonably well.

1. Download [wp2hugo][wp2hugo]
2. Run `wp2hugo` with your exported "content":

    ```shell
    # Valid for Linux / macOS. Might work for Windows.
    cd ${EXPORTED_CONTENT}
    wp2hugo --source wordpress-export.xml --download-media --output /tmp
    ```

3. Test the generated files

    ```shell
    # In /tmp/ you will find a "generated" folder.
    cd /tmp/generated-...
    
    # Run hugo
    hugo server
    ```

Try it locally by opening this URL <http://localhost:1313/>

[wp2hugo]: https://github.com/ashishb/wp2hugo

[migrate_to_hugo]: https://gohugo.io/tools/migrations/#wordpress

### Fix possible convertion issues

A few things that failed and that I had to fix them one by one manually:

* Some _"unrecognized character in shortcode action"_
* HTML Tables were broken.
* Image `[caption]`s were broken.
* Image sizes were broken.
* Some YouTube links were broken, in particular the ones that contained `_` in
  their "code"

And probably a few more things are still broken that I haven't found yet.

### Hosting it in GitHub Pages

Follow the official Hugo guide:

* [Host on GitHub Pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/)

### Aftermath

#### Pros

* To write posts in Markdown in my [favorite editor][clion].
* To host the site using Git: source control, history, etc.
* To have my images in the same place as the content.
  For different reasons, I was using Google Photos.
  Now, I'm just hosting them in GitHub.
* Don't have to pay for hosting, themes, and simple features like Google
  Analytics.

#### Cons

* Lost all "comments" in the conversion.
* No built-in comments: Hey, Hugo is a static site generator, it makes sense.
  There is support for [3rd-party comments services][hugo_comments]

#### Time spent

It took me around two days to do the entire process:

* Conversion to Hugo, and fix issues
* Setup Hugo
* Setup GitHub Pages
* Update DNS

So far, I'm happy with the result. But time will tell...

[clion]: https://www.jetbrains.com/clion/

[hugo_comments]: https://gohugo.io/content-management/comments/


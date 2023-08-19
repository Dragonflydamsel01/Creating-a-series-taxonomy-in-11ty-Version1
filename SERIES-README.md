# How to Link Posts as a series

## The Bloody Point of This Sandbox

If you want to link blog posts based on whether or not they are related by topic/theme (a series);
study this sandbox. This version is forked from version 1, and in this version the TOC for the series is placed inside the post. In this case, at the bottom of the post. This variant is based on the method used by A11y Project.com. Scroll to the bottom of the linked page to see the table of contents for their ARIA series:

https://www.a11yproject.com/posts/an-indepth-guide-to-aria-roles/

Here are the important bits:

## The File Folders

If you don't fork this version, just copy and paste the relevant files, and pay attention to where they are located:

1. _11ty / collections
  
"seriesCollections.js"

This creates the collection and names the front matter variables that will be attached to a given collection object. 

2. _includes/layouts/post.njk
  
CTRL+F to "collections.seriesCollections" (without the quotes)

Swap out any styles mentioned for your own styles. 

4. content / series
Note: The Series folder must be on the same level as your Posts folder. In this case, both the Series and the Posts folders are inside the Content folder. The "collection object" (that's what 11ty collections are) will be whatever files you put in this folder. 

The name you give the file will be used as the slug for the series (which you can see in the "seriesCollections.js" file in step 1). So for instance, "swan-wives.html" becomes the "swan-wives" slug for the Swan Wives series.

5. content / series / file frontmatter  

Note: I use "preface" because I use descriptions on my blog posts normally, and the "description" key in a post will take precedence over a description key on the series collection object. 

Inside the frontmatter for the file, this is all you need:
---
title: Series Title
preface: "Description of your series"
---

6. content / series / series.11tydata.js

If you call your Series folder something else for some reason, then change the name of this file to reflect that.

7. frontmatter for a given post in content --> posts
  
Self-explanatory; you will see how to reference the slugs from step 4.
  
8. In .eleventy.js
  
In module.exports {} CTRL+F for "Article/blog series collections" 

## BONUS - Subheads

If you want to put a subhead on your TOC (see the Golden Apple Tree posts in the Archive):

1. Note line 37-39 in the "post.njk" file from Step 2

2. Look in the file named "fourthpost.md" and note the frontmatter:
---
series:
  slug: "swan-wives"
  order: 1
  subhed: A Serbian variant of the wif-swan folktale
---

Yes, I used the spelling of subhead that's used in journalism, "subhed". This is to make sure that key doesn't clash with any other subheads you may have in your post's frontmatter.

## BONUS - External Links

1. In "index.css" scroll to the bottom / line 264. 

Copy what you need there to your own CSS.

2. In post.njk file in "_includes/layouts" 

Line 47 is how the external links get included. Note also line 43 ("if post.data.permalink ..."), which prevents the external links from otherwise appearing twice in your Table of Contents

3. In Content / Posts see the directory named "external_links"

a. Inside that folder, take note of the frontmatter of the post.

4. Non-intuitive last or first step:

a. I always create a post collection, because I don't rely upon tags to make the collections. I use a global folder, see the "_11ty / collections / posts.js" file. Eleventy explains more here: https://www.11ty.dev/docs/collections/#getfilteredbyglob(-glob-) 

b. In .eleventy.js, you should see:

  //posts or blog collections
  eleventyConfig.addCollection(
    "posts",
    require("./_11ty/collections/posts.js")
  );
  
A lot of people set up their 11ty post / blog collections via the method used in "posts.js." However, if you leave your 11ty / Eleventy set up as the default then you'll find that your external links appear on the landing pages for the home or archive pages. 

=================================
And that's it, you're done for this second version of a series taxonomy.






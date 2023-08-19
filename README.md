# How to Link Posts as a series

This is based on the following:
https://shivjm.blog/colophon/how-i-create-an-article-series-in-eleventy/

## The Bloody Point of This Sandbox

If you want to link eleventy /11ty blog posts based on whether or not they are related by topic/theme (a series);
study this sandbox. Here are the important bits:

## The File Folders

In the root of your eleventy file, here are the following folders:

1. _11ty
  Which has two folders, and two relevant files for each:

  * collections: "series.js"
  * filters: "getSeries.js"

3. _data
  Which has the file titled, "seriesData.json", this is where you collect the slugs for each series. This is the backbone of the collection object.

4. _includes/layouts/post.njk
  CTRL+F to "collections.series" (without the quotes)

5. content
  Which has several folders, but the two most relevant are:
 
  * posts (which has the blog posts)
  * pages: "series.njk". Think of a tag page, only this is for a given series.

6. frontmatter for a given post in content --> posts
  Self-explanatory; you will see how to reference the slugs from step 2.
  
7. In .eleventy.js
  In module.exports {} CTRL+F for "Article/blog series collections & filter" 
  
And that's it, you're done for this first version of a series based on here:
https://shivjm.blog/colophon/how-i-create-an-article-series-in-eleventy/







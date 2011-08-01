Introduction
============

If items are at the same level in a folder then they will be sorted based on a _path and then an optional
'_sortorder' key. For example transmogrify.webcrawler gives each item a _siteorder based on when it first discovered that link so links at the top of a page will therefore be resorted to before links first discovered at the bottom of a page if they are in the same folder.

In addition

- if an item doesn't exist for a given items parent it will be created. The _type key will
  be set to the first item in 'default_containers'.

- if a container has a 'text' key then a default page will be created.

- if item's name is in 'default_pages' and it's parent doesn't already have a defaultpage
  then the item will be set as the parents default page.


TODO
====

This blueprint really has three functions that might be better split out into three different blueprints

- finding an index page for a given folder based on the name of the index page. Since there is already a blueprint to try and guess whats a indexpage based on links, perhaps it should be integrated into that. Could have options to guess index page based on name or links or both. (see transmogrify.siteanalyser.defaultpage https://github.com/djay/transmogrify.siteanalyser/blob/master/transmogrify/siteanalyser/isindex.py)

- splitting out an index from a folder if it has an text element to it. This is kind of plone specific. This should also be made part of transmogrify.siteanalyser.defaultpage since there is no point in looking to see if any index pages exist if the folder already has a text field that needs to be converted to a index page.

- Adding parents that don't exist. This should be it's own blueprint maybe called transmogrify.addfolders. It might depend on pathsorter to sort first. Need to investigate if the pathsort will still work without all parents existing.

- need to generalise out references to _site_url as this is funnelweb specific. 
 
- have more options such as specify _path key etc. 
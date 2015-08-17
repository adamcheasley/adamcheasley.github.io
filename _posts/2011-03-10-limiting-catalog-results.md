---
title: "Plone: Limiting catalog search results"
layout: post
description: How to correctly limit the number of results returned from the portal catalog in Plone.
---

After some confusion today regarding the "sort_limit" index in plone's catalog, I discovered the following:

>The sort_limit is only a hint for the search algorhitms and can potentially return a few more items, so it's preferable to use both
`sort_limit` and slicing simultaneously

So something like this:  
```
limit = 10
    results = portal_catalog.searchResult(
        portal_type='Folder'
        sort_limit=limit)
    return results[:limit]
```
	
Discovered this on the following page and it seems like a good resource for any question regarding catalog indexing in plone:
[querying-the-catalog](http://plone.org/documentation/manual/developer-manual/indexing-and-searching/querying-the-catalog)

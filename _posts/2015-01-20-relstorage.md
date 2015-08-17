---
title: Relstorage for mere mortals
layout: post
description: For the 2015 Plone conference I presented a talk on relstorage with Matthew Sital-Singh
---


At ploneconf 2014, Matthew Sital-Singh and I gave a talk on using
	      relstorage in Plone. Our main use case for this was that one of our
	      biggest sites still uses FileStorage in the ZODB, which means that
	      this file and zeo are a single point of failure.

Switching your plone site from using FileStorage to using RelStorage
	      is quite simple. You can simply add the following to your buildout,
	      under the instance part:

```
rel-storage =
  	type postgresql
   	db plone
   	user plone
   	passwd PASSWORD
```

If you this is a fresh site, you will be up and running in RelStorage mode. The ZODB
	      will write all data to this relational database. Notice that I've set it to use
	      postgres in the config above. There are other options here, including mysql, but
	      we ran into some pretty big issues when using mysql, so I would strongly recommend
	      postgres.

If however, this is not a new site, you would need to migrate your data from FileStorage
	      into the relational database. This can be achieved with the [zodbconvert script](https://pypi.python.org/pypi/RelStorage#zodbconvert)

You can [view our slides from the presentation here.](https://docs.google.com/presentation/d/1zeJ7MiMitejAdSSUkntHrqHs_Iu9h4q1vYJ1GwQbnpI/edit?usp=sharing)
	      This also contains links to stats on the type of speed increases you are likely to see
	      when using RelStorage. 
	      There is also a [video](https://vimeo.com/111051175)
	      of our talk available on vimeo.

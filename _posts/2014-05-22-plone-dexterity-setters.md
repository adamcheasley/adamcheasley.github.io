---
title: Plone acquisition and dexterity mutators
layout: post
description: How to use acquisition within dexterity mutators
---


A strange property of putting logic in dexterity content types
	    has bitten me a couple of times. Here's the issue;
	    You are advised, if you wish to override the given accessors and
	    mutators of the object, to do something like the following:

```
	      @property
	      def my_field(self):
	        # get some attribute

	      @my_field.setter
	      def my_field(self, value):
                # do something else before setting the value
```

This is fine, and is a usual python convention, *except* that
	    the 'self' object will not be acquisition wrapped.

This means that if you try to do anything which relies on acquisition,
	    which is pretty much anything in Plone, then you will run into problems.
	    If you find that you are running into permissions issues, or authentication
	    issues in code within your object, it's probably to do with this issue.

The simple fix here would just be to change the setter to something like:

```
	      def set_my_field(self, value):
                # do something else before setting the value
```

'self' would now be acquisition wrapped.

The other option of course is to move any business logic like this
	    out of the model, which is probably what I would advise.

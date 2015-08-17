---
title: Plone Content icons for Archetypes and Dexterity 
layout: post
description: "The way icons representing content types has changed from Archetypes to Dexterity. This post explains how to deal with a site that uses both frameworks."
---


Due to the slow move from Archetypes to Dexterity, I have been dealing
with a lot of sites recently that contain both Archetypes and Dexterity
content types mixed together. For the most part this works fine, but there
are a few places where you find yourself writing different code depending
on which type of object you have at any one time.

A perfect example of this came up recently; when trying to list
              objects within a folder that were from both types. The problem came
              when trying to show icons for these objects. In Archetypes, you could
              simply do:


```
plone_view.getIcon()  

```

This would return you an object which implements IContentIcon, on which
              you would usually call the html_tag method. This would give you a fully
              formed img tag which you could put straight into a template. With
              dexterity, this is now deprecated.

The difference with dexterity is that in an Archetypes definition of
              a content type, you would define a content_icon property:<br /><br />

```
<property name="content_icon">MyType.gif</property>
```

where as in dexterity, we now define an icon expression:

```
<property name="icon_expr">string:++resource++my.package/images/my_type.png</property>
```

The former is assumed to be in a skins folder, the latter is an expression
              containing the path to the image.

The fix here involves using the portal types tool and this handy function
              from CMFCore called 'createExprContext':

```
from Products.CMFCore.Expression import createExprContext  

portal_types_tool = api.portal.get_tool('portal_types')
type_info = portal_types_tool.getTypeInfo(portal_type)
icon_ob = type_info.getIconExprObject()
portal = api.portal.get()
exp_context = createExprContext(
portal, portal, portal)
return icon_ob(exp_context)
```

This will return an absolute path to the icon in the context of the
	      portal. This can then be used in tal for either archetypes or dexterity.

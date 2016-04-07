---
title: Django and Json Web Tokens
layout: post
description: Django rest framework using JWT for authentication.
---

On a recent project, we decided to fully decouple the front and back ends using django rest framework to 
create a back end API and Angular to create a front end application to interact with the API.

I looked around at the myriad of possibilities for authentication with the API, and decided to take a look at 
JSON Web Tokens (JWT). From https://jwt.io/introduction/

> JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object.

Essentially, this gives us a simple, stateless way to authenticate requests coming into the api. Angular makes its first request out to an endpoint, with a username and password, and gets back a token. It can then use this token to authenticate subsequent requets. 

There is a great package that integrates with Django Rest Framework making all this very easy on the backend:
[django-rest-framework-jwt](https://getblimp.github.io/django-rest-framework-jwt/)

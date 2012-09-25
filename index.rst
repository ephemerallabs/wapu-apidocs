.. We Are Pop Up API documentation master file, created by
   sphinx-quickstart on Mon Sep 24 20:46:35 2012.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

We Are Pop Up API
=================

This document describes the interaction with the We Are Pop Up API, as well as all entities available.

===============
Making Requests
===============

All requests must use a token based signature to authorize the request and identify the originating application. Each registered application will be assigned a **Public Key** and **Private Key**. The **Private Key** should be kept secret, as it could be use to falsify requests as having originated from the application. Each request must pass 3 custom HTTP header values, as follows: ``X-WAPU-Application-Id: <public_key>``, ``X-WAPU-Request-Timestamp: <iso8601_timestamp>``, and ``X-WAPU-Request-Signature: <signature_token>``.

A signature token is a md5 hash, generated for the request with the following format (in psuedo-code)::

    md5( public_key + iso8601_timestamp + private_key )

.. note:: The timestamp used **must** be of the ISO8601 format, and the request will be rejected if it cannot be parsed into a datetime

==============
Authentication
==============

Some requests require user authentication. The user's API key must first be obtained by logging in as that user into the system. To do so, make a request to ``/api/v1/user/{username}/`` using HTTP Basic authentication in the form ``username:password``. The response will look like::

    {
        "api_key": API_KEY
        "id": ID,
        "resource_uri": RESOURCE_URI
        "username": USERNAME
    }

The important piece of data here is the ``api_key``. Once obtained, this key is used to authenticate subesequent requests, using an additional HTTP header: ``Authorization: ApiKey <username>:<api_key>``

==================
Object Definitions
==================

.. toctree::
   :maxdepth: 2

   popup.rst
   category.rst
   event.rst
   venue.rst
   personality.rst
   image.rst

===========
Saving Data
===========

Data should be sent as a **POST** to create a new object or **PUT** with an ID to update one, as JSON in the same object structure as it is received. The response will be a *resource_uri* for the newly created object.

**Nested Data**

There are two important caveats to keep in mind when dealing with nested resources:

1. A nested resource in either a POST or a PUT will be created if it is sent as data. If the intention is to reuse and existing resource, its *resource_uri* should be used instead. The first example creates a new **Personality** while creating the **Popup**, where as the second will assign an existing **Personality** with ID=1 to the **Popup**:: 

    {
        "name":"Test Popup",
        "personalities":[
            {"website":"http://www.google.com"}
        ],
        ...
    }


    {
        "name":"Test Popup",
        "personalities":[
            "/mapi/v1/personality/1/"
        ],
        ...
    }

2. There is currently a limitation that nested resources can only be created a single level deep. The practical limitations of this are that **Events** must be created separately from **Popups**. The **Event** must be created first, and then it's *resource_uri* assigned in the *events* list on the **Popup**. Because **FixedDate**, **FixedOpenClose**, and **FloatingDate** entities are not created as true objects with a *resource_uri*, they do not follow this limitation.

**Image Uploading**

**Images** are not directly uploaded through the API. Instead, they should be uploaded to a server where they can be accessed publically via web URL, such as S3. The format should be either GIF, JPEG, or PNG, and should not exceed 1280x1280.

When creating an **Image** via post, the only information sent will be the **write-only** parameter **original**, as follows:: 

    {
        "original":"http://s3.amazonaws.com/bucket/location/identifier.jpg"
    }

The *small*, *medium*, and *large* versions will be created from this file. The response will, as normal, be a *resource_uri* which can be then assigned to a **Popup**.

.. note:: **Images** should be created separately from (before) a **Popup** and assigned, rather than attempting to create them via nesting.

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

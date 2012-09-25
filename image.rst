Image
=====

.. http:method:: GET /api/v1/image/{id}/
    
    Retrieve one or a list of Images

    :arg integer id: An Image ID. May be omitted to load all Images available

.. http:method:: POST /api/v1/image/

    Create a new Image. Must be a logged in request

.. http:response:: Image object

    An Image object is defined like this::

        {
            "id":ID,
            "large":LARGE,
            "medium":MEDIUM,
            "resource_uri":RESOURCE_URI,
            "small": SMALL
        }

    :data integer id: The Image ID
    :data string large: The URL of the large instance,
    :data string medium: The URL of the medium instance,
    :data string resource_uri: The URI of the Image resource
    :data string small: The URL of the small instance


Personality
===========

.. http:method:: GET /api/v1/personality/{id}/
    
    Retrieve one or a list of Personalities

    :arg integer id: A Personality ID. May be omitted to load all Personalities available

.. http:method:: POST /api/v1/personality/

    Create a new Personality. Must be a logged in request

.. http:method:: PUT /api/v1/personality/{id}/
    
    Update the Personality with the given ID. Must be a logged in request and the owner of the Personality

    :arg integer id: A Personality ID to update

.. http:response:: Personality object

    A Personality object is defined like this::

        {
            "resource_uri":RESOURCE_URI,
            "website":WEBSITE
        }

    :data string resource_uri: The URI of the Personality
    :data string website: The website for the Personality

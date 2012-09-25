Category
========

.. http:method:: GET /api/v1/category/{id}/
    
    Retrieve one or a list of Categories

    :arg integer id: A Category ID. May be omitted to load all Categories available

.. http:response:: Category object

    A Category object is defined like this::

        {
            "id":ID,
            "key":KEY,
            "label":LABEL,
            "resource_uri":RESOURCE_URI,
            "superset":SUPERSET
        }

    :data integer id: The Category ID
    :data string key: The Category key used
    :data string label: The label of the Cateogry
    :data string resource_uri: The URI of the Venue
    :data string superset: The Category superset label

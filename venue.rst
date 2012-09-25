Venue
=====

.. http:method:: GET /api/v1/venue/{id}/
    
    Retrieve one or a list of Venues

    :arg integer id: A Venue ID. May be omitted to load all Venues available

.. http:method:: POST /api/v1/venue/

    Create a new Venue. Must be a logged in request

.. http:method:: PUT /api/v1/venue/{id}/
    
    Update the Venue with the given ID. Must be a logged in request and the owner of the Venue

    :arg integer id: An Venue ID to update

.. http:response:: Venue object

    A Venue object is defined like this::

        {
            "address":ADDRESS,
            "city":CITY,
            "country":COUNTRY,
            "county":COUNTY,
            "id":ID,
            "lat":LAT,
            "lng":LNG,
            "postcode":POSTCODE,
            "resource_uri":RESOURCE_URI
        }

    :data string address: The Venue address
    :data string city: The Venue city
    :data string country: The Venue country
    :data string county: The Venue county
    :data integer id: The Venue ID
    :data float lat: Latitude coordinate of the Venue
    :data float lng: Longitude coordinate of the Venue
    :data string postcode: The Venue postcode
    :data string resource_uri: The URI of the Venue

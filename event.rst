Event
=====

.. http:method:: GET /api/v1/event/{id}/
    
    Retrieve one or a list of Events

    :arg integer id: An Event ID. May be omitted to load all Events available

.. http:method:: POST /api/v1/event/

    Create a new Event. Must be a logged in request

.. http:method:: PUT /api/v1/event/{id}/
    
    Update the Event with the given ID. Must be a logged in request and the owner of the Event

    :arg integer id: An Event ID to update

.. http:response:: Event object

    An Event object is defined like this::

        {
            "fixed_dates": FIXED_DATES,
            "floating_dates": FLOATING_DATES,
            "id": ID,
            "name": NAME,
            "resource_uri": RESOURCE_URI,
            "schedule": SCHEDULE,
            "venue": VENUE
        }

    :data FixedDates fixed_dates: A *FixedDate* definition (see below) or *null*
    :data FloatingDates floating_dates: A FloatingDate definition (see below) or *null*
    :data integer id: The Event ID
    :data string name: The name of the Event
    :data string resource_uri: The Event's resource URI
    :data string schedule: The Event schedule type, either **fixed** or **floating**
    :data string venue: The definition or URI of the Venue associated with the Event

    |

    .. note:: The following date/time definitions are not true objects in that they have no Resource URI.

    A *FixedDate* definition::

        {
            "end": END,
            "fri": FRI,
            "mon": MON,
            "sat": TUE,
            "start": START,
            "sun": SUN,
            "thr": THR,
            "tue": TUE,
            "wed": WED
        }

    :data date end: The end date in format YYYY-MM-DD
    :data FixedOpenClose fri: A *FixedOpenClose* definition
    :data FixedOpenClose mon: A *FixedOpenClose* definition
    :data FixedOpenClose sat: A *FixedOpenClose* definition
    :data date start: The start date in format YYYY-MM-DD
    :data FixedOpenClose sun: A *FixedOpenClose* definition
    :data FixedOpenClose thr: A *FixedOpenClose* definition
    :data FixedOpenClose tue: A *FixedOpenClose* definition
    :data FixedOpenClose wed: A *FixedOpenClose* definition

    |

    A *FixedOpenClose* definition::

        {
            "close":CLOSE,
            "open":OPEN
        }

    :data time close: A close time in the format HH:MM:SS
    :data time open: An open time in the format HH:MM:SS

    |

    A *FloatingDate* definition::

        {
            "close":CLOSE,
            "date":DATE,
            "open":OPEN
        }

    :data time close: A close time in the format HH:MM:SS
    :data date date: The date in format YYYY-MM-DD
    :data time open: An open time in the format HH:MM:SS

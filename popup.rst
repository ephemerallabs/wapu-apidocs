Popup
=====

.. http:method:: GET /api/v1/popup/{id}/?mine&with_deleted&with_drafts
    
    Retrieve one or a list of Popups

    :arg integer id: A Popup ID. May be omitted to load all Popups available
    :optparam datetime updated_at__gte: Load only Popups that were updated after the given datetime. Must be sent in ISO8601 format.
    :optparam boolean mine: Load only the current user's Popups. Must be a logged in request
    :optparam boolean with_deleted: Load Popups which have been marked deleted. Must be a logged in request. May only be set when **mine** is set to *True*
    :optparam boolean with_drafts: Load Popups which are marked as drafts. Must be a logged in request. May only be set when **mine** is set to *True*

.. http:method:: POST /api/v1/popup/

    Create a new Popup. Must be a logged in request

.. http:method:: PUT /api/v1/popup/{id}/
    
    Update the Popup with the given ID. Must be a logged in request and the owner of the Popup

    :arg integer id: A Popup ID to update

.. http:response:: Popup object

    A Popup object is defined like this::

        {
            "category": CATEGORY,
            "created_at": CREATED_AT,
            "deleted_at": DELETED_AT,
            "description": DESCRIPTION,
            "draft": DRAFT,
            "email": EMAIL,
            "events": [EVENT],
            "facebook": FACEBOOK,
            "google_plus": GOOGLE_PLUS,
            "hashtag": HASHTAG,
            "headline": HEADLINE,
            "id": ID,
            "images": [IMAGE],
            "logo": LOGO,
            "name": NAME,
            "personalities": [PERSONALITY],
            "phone": PHONE,
            "pinterest": PINTEREST,
            "private": PRIVATE,
            "resource_uri": RESOURCE_URI,
            "shortlink": SHORTLINK,
            "twitter": TWITTER,
            "updated_at": UPDATED_AT,
            "website": WEBSITE
        }


    :data Category category: A Category definition or resource URI
    :data datetime created_at: The date the Popup was created
    :data datetime deleted_at: The date the Popup was deleted, or *null*
    :data string description: The description text of the Popup
    :data boolean draft: Is a draft
    :data string email: The email address of the Popup
    :data Event[] events: The Event definitions or URIs associated with the Popup
    :data string facebook: The Facebook page of the Popup
    :data string google_plus: The Google Plus of the Popup
    :data string hashtag: The hashtag of the Popup
    :data string headline: The headline text of the Popup
    :data integer id: The Popup ID
    :data Image[] images: A list of Image definitions or URIs associated with the Popup
    :data Image logo: The Popup logo, an Image definition or URI
    :data string name: The name of the Popup
    :data Personality[] personalities: The Personality definitions or URIs associated with the Popup
    :data string phone: The Popup's phone number
    :data string pinterest: The Pinterest of the Popup
    :data boolean private: Marked as private
    :data string resource_uri: The Popup's resource URI
    :data string shortlink: The shortlink tag of the Popup (not used currently)
    :data string twitter: The Twitter name of the Popup
    :data datetime updated_at: The last date the Popup was updated
    :data string website: The website of the Popup

# Graph API

Python library to connect [instagram graph API](https://developers.facebook.com/docs/instagram-api) and get data.


## Usage
First get an access_token from [here](https://developers.facebook.com/tools/explorer)

    from graph_api import InstagramGraphHandler
    
    # Get account data 
    handler = InstagramGraphHandlers(access_token=<your-access_token>, 
                                     account_id=<your-instagram-account-id>)
    account_data = handler.account_data.get()
    
    # Get media data
    handler = InstagramGraphHandlers(access_token=<your-access_token>, 
                                     media_id=<instagram-media-id>)
    media_comments = handler.media_comments.get()
    
    # Pagination support
    while handler.media_comments.graph.has_next():
        media_comments.extend(handler.media_comments.get())


##Notes:
* All `.get()` API call only return one page response and you should loop over next pages urls.
* All handlers are available stand alone from graph_api.handler path


##Todo:
* Add token extender to exchange short-live token to long-live
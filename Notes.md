# REST in Drupal 8

All HTTP methods are only support for content entities e.g. nodes.

I need to provide access permissions to anonymous users since there is an issue with the current set up I have. FastCGI requires some additional configuration in order to get the `PHP_AUTH_USER` and `PHP_AUTH_PW` to work. This is also the `--user` parameter in cURL.

CORS is not supported in core yet therefore the front end needs to be hosted on the same server as  our headless Drupal.

POST, PATCH, and DELETE HTTP verbs require `hal+json` representation. No idea why it's using PUT instead of PATCH.

Examples of browser extensions acting as HTTP Clients are Postman or Dev HTTP client.

# Entity Related Stuffs

Discuss only a single type of content entity specifically node.

# What is HAL?

I don't know. It's the Hypertext Application Language. The basic usage here is to allow linking to the other resources. Most likely for creating a relationship between resources. It has two reserved properties when calling a resource:

* `_links`
* `_embedded`

This is to be passed along with the data for your JSON.

A possible example is fetching the bundle for the entity type for contents e.g. http://example.com/rest/type/<entity type>/<bundle>.

# Using AngularJS to Manipulate Data

Lotsa hardcoded stuffs. Only uses Title and Body fields. In the PATCH request, not sure what's happening but the `type` property needs to be provided although it doesn't seem to consider whatever you put here as long as the type is valid i.e. editing a node of `article` type works even if the type you passed is `page`.

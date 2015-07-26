# REST in Drupal 8

I need to provide access permissions to anonymous users since there is an issue with the current set up I have. FastCGI requires some additional configuration in order to get the `PHP_AUTH_USER` and `PHP_AUTH_PW` to work. This is also the `--user` parameter in cURL.

CORS is not supported in core yet therefore the front end needs to be hosted on the same server as  our headless Drupal.

POST, PATCH, and DELETE HTTP verbs require `hal+json` representation.

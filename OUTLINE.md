# Headless Drupal 8

## Introduction to REST in Drupal 8

### What is REST?

> Web Services make it possible for other applications to read and update information on your site via the Web. REST is one of a number of different ways of making Web Services available on your site. In contrast to other techniques such as SOAP or XML-RPC, REST encourages developers to rely on HTTP methods (such as GET and POST) to operate on site resources.

\- [REST Documentation](https://www.drupal.org/documentation/modules/rest)

### REST in Drupal 8

The `rest` module provides resources which allows external applications to interact with Drupal. It also allows module developers to create their own resource to further extend how Drupal behaves when calling out those created resources.

The `rest` module has 4 HTTP verbs:

* GET
* POST
* PATCH
* DELETE

Core in Drupal 8 provides 2 representations:

* JSON
* HAL (`hal`)

Core in Drupal 8 provides 2 authentications:

* Cookie
* Basic Auth (`basic_auth`)

## Using GET Operations for Entities to Retrieve Data

To allow GET Operations for entities in order to retrieve data, you will need to set the necessary permissions:

* Access GET on Content Resource
* View published content

You will need to have the configuration for REST module as well. See `core/modules/rest/config/rest.settings.yml` for some basic configurations. You can also use `restui` contrib module to set these configurations.

For testing, you can use cURL or some other HTTP client. Example for cURL to get the JSON representation:

`curl -s -H 'Accept: application/json' http://example.com/node/1?_format=json`

## Create, Update, and Delete Operations for Entities
## Using AngularJS to Manipulate Data
## Resources

DI PA KO KABALO MAG UPDATE xD

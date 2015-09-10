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

### REST Configuration

You will need to have the configuration for REST module as well. See `core/modules/rest/config/rest.settings.yml` for some basic configurations. You can also use `restui` contrib module to set these configurations.

### Permission Configurations

To allow GET operations for entities in order to retrieve data, you will need to set the necessary permissions:

* Access GET on Content Resource
* View published content

### Testing

For testing, you can use cURL or some other HTTP client. Example for cURL to get the JSON representation:

`curl -s http://example.com/node/1?_format=json`

## Create, Update, and Delete Operations for Entities

### What is HAL?

> HAL is a simple format that gives a consistent and easy way to hyperlink between resources in your API.

\- [HAL Informal Specifications](http://stateless.co/hal_specification.html)

### Basic Authentication and HAL

Authentication and HAL are required for POST, PATCH, and DELETE verbs. Enable the modules:

* `hal`
* `basic_auth`

Basic authentication is passing the `Authorization` header - `Authorization: Basic BASE64<user:password>`.

### Testing

#### Creating

`curl -s -H 'Content-Type: application/hal+json' --user <user>:<password> http://example.com/entity/node '{ "_links": { "type": { "href": "http://example.com/rest/type/node/page" } }, "title": [ { "value": "Foobar" }]}'`

#### Updating

`curl -s --request PATCH -H 'Content-Type: application/hal+json' --user <user>:<password> http://example.com/node/1 '{ "_links": { "type": { "href": "http://example.com/rest/type/node/page" } }, "title": [ { "value": "Foobar" }], "body": [ { "value": "Test" } ] }'`

#### Deleting

`curl -s --request DELETE --user <user>:<password> http://example.com/node/1`

## Using AngularJS to Manipulate Data

AJAX all things!

## Resources

* [REST Documentation](https://www.drupal.org/documentation/modules/rest)
* [The state of ReST in Headless Drupal 8](http://build2be.com/content/state-rest-headless-drupal-8)
* [POST, PATCH and DELETE request with Drupal 8 REST services](http://tntfoss-vivekvpandya.rhcloud.com/node/40)
* [An Introduction to RESTful Web Services in Drupal 8](https://dev.acquia.com/blog/introduction-restful-web-services-drupal-8)

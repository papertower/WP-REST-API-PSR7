# WP REST API PSR-7
WP REST API PSR-7 is a small library which creates a bridge between the PSR-7 standards and interfaces and the WordPress REST API Response and Request classes. You can include it via composer in any theme or plugin which needs this.

## More Detail
Development for the WordPress REST API started before the [PSR-7](https://www.php-fig.org/psr/psr-7/) was finalized. This standard made a great way for different libraries to be able to interact using a common interface. Unfortunately, since WordPress missed it, the standard [WP_REST_Request](https://developer.wordpress.org/reference/classes/wp_rest_request/) and [WP_REST_Response](https://developer.wordpress.org/reference/classes/wp_rest_response/) classes are not PSR-7 compliant.

This means that any library which extends HTTP Messages using the PSR-7 standard are not compatible with WordPress by default. Bummer! Our team ran into this limitation when attempting to use the [OAuth2 Server](https://github.com/thephpleague/oauth2-server) library.

## When would I need this?
This is the sort of thing where you don't need it until you do and when you do you'll know it's missing. 🙂

## Things to keep in mind
When generating a `WP_REST_PSR7_Request` from a request, the body is passed directly to the PSR-7 body stream. This means that any validation and sanitization that `WP_REST_Server` provides may not be applied. Be aware of this and make sure that sanitization and validation are applied if the library does not.

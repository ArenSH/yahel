yahel
=====

Yet another HTTP errors library


Example
=======

```js
var httpError = require( 'yahel' );

app.get( '/not-found', function( req, res, next ){
    next( new httpError.NotFound );
});

app.get( '/forbidden', function( req, res, next ){
    next( new httpError.Forbidden );
});

app.get( '/internal-error', function( req, res, next ){
    next( new httpError.InternalServerError('Wow! Such an error!') );
});

app.use( function( error, req, res, next ){
    res.json( error.status || 500, {
        message: error.message,
        stack: error.stack
    });
});
```


API
===

* {Function} ErrorClass( {string?} message )
* {string} ErrorClass.message
* {number} ErrorClass.status
* {string} ErrorClass.stack


Available error classes
=======================

```
Conflict
Gone
LengthRequired
PreconditionFailed
RequestEntityTooLarge
RequestUriTooLong
UnsupportedMediaType
RequestedRangeNotSatisfiable
ExpectationFailed
ImATeapot
EnhanceYourCalm
UnprocessableEntity
Locked
FailedDependency
UnorderedCollection
UpgradeRequired
PreconditionRequired
TooManyRequests
RequestHeaderFieldsTooLarge
NoResponse
RetryWith
BlockedByWindowsParentalControls
ClientClosedRequest
InternalServerError
NotImplemented
BadGateway
ServiceUnavailable
GatewayTimeout
HttpVersionNotSupported
VariantAlsoNegotiates
InsufficientStorage
LoopDetected
BandwidthLimitExceeded
NotExtended
NetworkAuthenticationRequired
```

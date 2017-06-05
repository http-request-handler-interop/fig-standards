# HTTP Request Handler

This document describes extensible interfaces to handle (server-side) requests defined by [PSR-7](http://www.php-fig.org/psr/psr-7/).

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](http://tools.ietf.org/html/rfc2119).

The final implementations MAY decorate the objects and methods with more functionality than the one proposed but they MUST implement the indicated interfaces/functionality.

### References

- [PSR-7](http://www.php-fig.org/psr/psr-7/)
- [RFC 2119](http://tools.ietf.org/html/rfc2119)

## 1. Specification

* A _Request Handler_ is a component that accepts a request and returns a response.
* A _Request Handler Action_ encapsulates all information needed to perform the behavior of a Request Handler.

This specification defines contracts for the most common Request Handler Action, which accepts a _PSR-7 ServerRequestInterface instance_ and returns a _PSR-7 ResponseInterface instance_.

## 2. Package

The interfaces described are provided as part of the [psr/http-request-handler](https://github.com/http-request-handler-interop/http-request-handler) package.

## 3. Interfaces

An _HTTP Message Strategy_ using this standard MUST implement the corresponding `interface` and the behaviour described by its comments.

### 3.1 `Psr\Http\RequestHandler\ActionInterface`

```php
namespace Psr\Http\RequestHandler;

use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\ServerRequestInterface;

/**
 * Defines a contract for functions which accept a server request argument and return a response.
 */
interface ActionInterface
{
    /**
     * Process a server request and return the produced response.
     *
     * @param ServerRequestInterface $request
     *
     * @return ResponseInterface
     */
    public function __invoke(ServerRequestInterface $request);
}
```

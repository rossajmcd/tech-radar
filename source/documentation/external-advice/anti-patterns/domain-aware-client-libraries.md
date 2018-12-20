# Domain Aware Client libraries

## Context

When building services, there is sometimes a desire to build a client library to help consumers easily integrate with the service. This is typically done for commonly-used services, such as keystore and auth. However, there is risk of extending the bounded context of the service into the client library by leaking domain logic that belongs in the service into the client library.

## Problem

> The problem, of course, is that if the same people create both the server API and the client API, there is the danger that logic that should exist on the server starts leaking into the client. I should know: I’ve done this myself. The more logic that creeps into the client library, the more cohesion starts to break down, and you find yourself having to change multiple clients to roll out fixes to your server. You also limit technology choices, especially if you mandate that the client library has to be used.
>
> [Sam Newman - Building Microservices](http://shop.oreilly.com/product/0636920033158.do)

## Solution

The solution is to maintain the bounded context around the microservice and ensure that client libraries are provided for convenience only. A client library should not be required in order to use a service. It is important to remember that the API for a microservice is the set of HTTP endpoints it exposes, and that a consumer must be able to interact with full set of features exposed by the service without using the client library.

## Exceptions

There are no known exceptions to this anti-pattern.

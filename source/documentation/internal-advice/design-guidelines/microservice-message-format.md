# Microservice Message Format

There is a principle on the platform that we would have an API First approach to our microservices. This, up until now, has not been the case and has not been necessary. API First is the principle that any microservice can potentially be exposed via the API Gateway, whether or not it's intended to. It follows the standards of APIs.

To ensure all our public APIs have a consistent message format, so that clients know how to work with them, we have agreed on a format that will be applied to all new microservices.

## Message Format

The message format that was chosen was [HAL](http://stateless.co/hal_specification.html). This is a REST API standard message format, that takes advantage of HATEOAS. 

HAL has both a json and xml format. We will, of course, have json as standard.

# Hypermedia Controls (HATEOAS)

There is still a debate amongst many people in the industry as to the merits of HATEOAS or otherwise. There is a valid argument that HATEOAS is developing something for a client that does not exist (an intelligent client that can follow links automatically).

Another valid argument is that most of our external developer base have never communicated with HATEOAS services.....why would they have, considering most of them generally only communicate with our organisation.

However, on the platform, we have determined that this is the best approach for us and it is where we want to go **where appropriate**.

## Why ?

HATOEAS brings the control of how to communicate with our services back within our gift. Our clients never need to know the logic that is required, we can change it as we like and it never affects the client.

A HATEOAS API makes it clear to client software what can be done next when an action is completed, this is discoverability, what you need to know when you need to know it.

It reduces coupling. New functionality can be added without breaking our consumer's software clients. Once they're ready, the consumer can make their changes and use the new controls.

It can improve performance - only send back what's needed and no more. Only run logic as needed and no more. etc....

Software clients can be industrialised when control of the state and journey is controlled through HATEOAS. This permits:

* cost efficiencies where suitable (for example government service and data sharing) as API software clients are made easier to build and can be re-used by many consumers
* software client availability for smaller government departments and other third parties who otherwise would not have the resources to build or purchase them

There are many public APIs that use HATEOAS, and therefore for the developer community, there are plenty of resources to take advantage of these days. 

## What is HATEOAS ?

The [Richardson Maturity Model](https://martinfowler.com/articles/richardsonMaturityModel.html#level3) is a good entry point into what HATEOAS is.

We represent links on the customer facing APIs using the HAL message format.

A good example of an almost HATEOAS API being used in the wild is  [Paypal](https://developer.paypal.com/docs/api/overview/)

# Assumed Upstream Security

## Context

Services in may architectures are created as a pair of microservices - a frontend and a backend - and are often developed in tandem and by the same team. This can give rise to a dangerous security assumption that the upstream (frontend) service has performed all the necessary security checks and therefore the downstream (backend) service can simply permit all requests.

## Problem

There are a number of problems in this anti-pattern:

1. It violates the good security practice of defense in depth. This means that a bug in (or compromise of) the frontend service renders the backend service exposed.
1. It introduces coupling between the two services in that they are always expected to be used together (and in no other combination).
1. It prevents the backend service from being exposed over the API Platforms as per an API first strategy
1. It prevents other services within the architecture from being able to safely use the insecure backend service

## Solution

Services should always perform authorisation checks before handling any incoming requests that operate on user-specific data. Each service is responsible for permitting / denying access to the caller based on what they are allowed to do. While there are scenarios that can be commonly applied across services, there are also some domain-specific scenarios that will need to be identified for some services. In general, if the ability to call a particular API should be limited to certain users (e.g. the person with ID 123456C or someone they have delegated to) then an authorisation check must be be put in place to enforce the security constraint.

In most cases, the solution is simply to leave auth enabled via your configuration mechanism. Authzn checks should generally be in place at the boundaries of services.

A good rule of thumb is that any API that operates on customer information must always perform an authorisation check. 

If a user that has not been granted access to the relevant identifier is able to successfully operate on that data, there is a security risk that needs to be addressed.

## Exceptions

There are cases where authorisation checks are not required; for example, metrics collection does not require authorisation checks.

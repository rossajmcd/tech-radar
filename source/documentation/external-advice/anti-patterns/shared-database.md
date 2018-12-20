# Shared Database

## Context

Situations arise when two services operate on the same underlying data. This appears in a number of forms, although is often a challenge for background jobs / tasks. A typical example is where a service receives submissions from users and stores them in its own database, but a background job runs periodically to push these locally-stored submissions into a backend system. There are other situations that lead to shared databases, and this anti-pattern applies to shared databases in general.

## Problem

The problem introduced by a shared database is essentially one of coupling. When two services rely on the same underlying database, it becomes increasingly difficult to evolve how the database is used - whether through schema evolution, indexing, change in read/write patterns, or even a full replacement of the database technology. Releasing services that exhibit this anti-pattern often relies on a synchronised deployment of both services that share the database or increases the number of deployments required for a single change. It also imposes organisational constraints in that a single team should maintain both services, otherwise the risk of failure increases beyond what is manageable.

## Solution

As in many cases, the solution to the problem is context-dependent. In the example of the background task, this could either be built into the main service alongside the transactional behaviour or it could be kept as a separate service that queries the primary service via APIs (i.e. not by direct database integration).

This has already been tackled in a number of areas within our customer facing architecture; for example, keystore provides an API for interacting with a shared session, but does not permit each service to access its database directly. This allows it to evolve to the needs of the platform independently of every other service.

If you have a problem similar to the one described here, please include one of the architects in the early stages to help define a suitable pattern for your needs.

## Exceptions

There are no known exceptions to this anti-pattern.

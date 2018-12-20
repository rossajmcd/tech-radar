# Coupling through Session State

## Context

A user navigating services on our customer facing architecture will necessarily alternate between multiple frontend microservices. This is largely transparent to the user, but introduces challenges in passing information between frontend services to facilitate the user journey. There are various mechanisms available depending on the type of journey, and many (if not all) rely on sharing some state between frontends. An example of this kind of state is a continueURL when sending a user to the login page.

## Problem

As much as backend services require good, descriptive APIs - so do frontends. There is a danger in providing 'magic' parameters that are stashed somewhere accessible to both frontends (typically in keystore) rather than explicitly including them in the API. This often leads to:

1. Undocumented understanding of how services interact with each other (this information tends to get lost as people move off the team)
1. Unclear integration points between frontend services (e.g. who clears the value after the interaction? who owns the parameter name?)
1. Coupling of frontends through a shared database of sorts (see [Shared Database](shared-database.md))
1. Hard to change behaviour as the risk of unintended breakage is high (how can you safely rename/remove the parameter without breaking other services?)
1. Almost impossible to determine the full set of consumers of session data (can you definitively name every service that uses a particular property in keystore?)

## Solution

A better way of achieving this integration is through explicit frontend APIs. Instead of saving data in keystore, create an explicit query parameter to pass the information between frontends. This allows the ownership of the parameter name to be clearly defined (the service that defines the URL owns it) and the integration between frontend services to be explicit (no sharing of keystore values through out-of-band property names).

In some cases, the information shared between frontends is considered sensitive or security-focused and is deemed too risky to send via the browser. There are ways to handle this without requiring session state, and these should be explored with your architect. Options include (but are not limited to) query parameter encryption and the transaction-based redirect pattern adopted by most payment processors.

Regardless of the approach, frontends should not be coupled via session state.

## Exceptions

There are no known exceptions to this anti-pattern.

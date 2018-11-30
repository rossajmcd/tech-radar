# Assumed Upstream Security

## Context

Many services on MDTP are created as a pair of microservices - a frontend and a backend - and are often developed in tandem and by the same team. This can give rise to a dangerous security assumption that the upstream (frontend) service has performed all the necessary security checks and therefore the downstream (backend) service can simply permit all requests....

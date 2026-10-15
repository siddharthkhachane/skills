---
name: s-api
description: Catalog every API endpoint (method, route, handler, auth, params) and flag unauthenticated, unused, and inconsistent ones.
disable-model-invocation: true
---

Catalog every API endpoint exposed by this codebase. For each one list: HTTP method, full route path, the file and function that handles it, required authentication or authorization, request parameters or body shape, and a one sentence description of what it does. Group the endpoints by domain area, for example auth, users, billing. After the catalog, flag three things specifically: endpoints with no visible authentication check, endpoints that appear unused anywhere in the frontend or tests, and any inconsistent patterns across endpoints, such as some routes validating input and others not.

---
title: "PuppetDB 1 » Spec » Querying Status"
layout: default
---

## Query Format

Node status can be queried by making a GET request to `/status/nodes/<node>`,
accepting JSON.

## Response Format

Node status information will be returned in a JSON hash of the form:

    {"name": <node>,
     "deactivated": <timestamp>,
     "catalog_timestamp": <timestamp>,
     "facts_timestamp": <timestamp>}

If the node is active, "deactivated" will be null. If a catalog or facts are
not present, the corresponding timestamps will be null.

If no information is known about the node, the result will be a 404 with a JSON
hash containing an "error" key with a message indicating such.

## Example

[Using `curl` from localhost](./spec_curl.html#using-curl-from-localhost-non-sslhttp):

    curl -H "Accept: application/json" 'http://localhost:8080/status/nodes/<node>'

Where <node> is the name of the node whose status you wish to check.

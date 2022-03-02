---
title: Example
---

# API Design System Example

This is an example of what an API Design System might look like. It's based on [Paypal's API guidelines](https://github.com/paypal/api-standards/blob/master/http-api-style-guide.md), though it only describes a part of their guidelines at this point.

```yaml
version: "2021-05-07"
info:
  title: Paypal API Guidelines
standards:
  - name: error.json
    level: may
    iri: https://github.com/paypal/api-standards/blob/master/common-components/v1/schema/json/openapi-2.0/error.json
scenarios:
  - when: [http, transaction]
    then:
      - subject: [http, request, method]
        level: may
        values:
          - get
          - post
          - put
          - delete
          - patch
      - subject: [http, request, header]
        level: may
        values:
          - Accept
          - Accept-Charset
          - Content-Language
          - Content-Type
          - Link
          - Prefer
      - subject: [http, response, header]
        level: may
        values:
          - Content-Language
          - Content-Type
          - Link
          - Location
          - Prefer
      - subject: [http, request, header, Prefer]
        level: may
        values:
          - respond-async
          - read-consistent
          - read-eventual-consistent
          - read-cache
          - return=representation
          - return=minimal
      - subject: [http, message, header, Content-Type]
        level: should
        values:
          - application/json
  - when: [http, request, method, get]
    then:
      - subject: [http, response, status_code]
        level: may
        values:
          - "200"
          - "400"
          - "404"
          - "422"
          - "500"
  - when: [http, request, method, post]
    then:
      - subject: [http, response, status_code]
        level: may
        values:
          - "200"
          - "201"
          - "202"
          - "400"
          - "404"
          - "422"
          - "500"
  - when: [http, request, method, put]
    then:
      - subject: [http, response, status_code]
        level: may
        values:
          - "200"
          - "202"
          - "204"
          - "400"
          - "404"
          - "422"
          - "500"
  - when: [http, request, method, patch]
    then:
      - subject: [http, response, status_code]
        level: may
        values:
          - "200"
          - "204"
          - "400"
          - "404"
          - "422"
          - "500"
  - when: [http, request, method, delete]
    then:
      - subject: [http, response, status_code]
        level: may
        values:
          - "200"
          - "204"
          - "400"
          - "404"
          - "422"
          - "500"
  - when: [http, response]
    then:
      - subject: [http, response, header]
        require: must
        values:
          - "Content-Language"
  - when: [http, message, body]
    then:
      - subject: [http, message, header]
        level: must
        values:
          - Content-Type
  - when: [http, response, status_code, "201"]
    then:
      - subject: [http, response, header]
        level: must_not
        values:
          - Link
          - Location
  - when: [http, response, status_code, redirect]
    then:
      - subject: [http, response, header]
        level: must_not
        values:
          - Link
          - Location
  - when: [http, response, status_code, client_error]
    then:
      - subject: [http, message, body]
        level: must
        follow: error.json
  - when: [http, response, status_code, server_error]
    then:
      - subject: [http, response, body]
        level: must
        follow: error.json
  - when: [http, response, status_code, success]
    then:
      - subject: [http, response, body]
        level: must_not
        follow: error.json
```
---
title: Example
---

# API Design System Example

This is an example of what an API Design System might look like. It's based on [Paypal's API guidelines](https://github.com/paypal/api-standards/blob/master/api-style-guide.md), though it only describes a part of their guidelines at this point.

```yaml
version: "2021-05-07"
info:
  title: Paypal API Guidelines
standards:
  - name: error.json
    url: https://github.com/paypal/api-standards/blob/master/v1/schema/json/draft-04/error.json
design_system:
  - when: [http, transaction]
    then:
      - subject: [http, request, method]
        requirement: may
        values:
          - get
          - post
          - put
          - delete
          - patch
      - subject: [http, request, header]
        requirement: may
        values:
          - Accept
          - Accept-Charset
          - Content-Language
          - Content-Type
          - Link
          - Prefer
      - subject: [http, response, header]
        requirement: may
        values:
          - Content-Language
          - Content-Type
          - Link
          - Location
          - Prefer
      - subject: [http, request, header, Prefer]
        requirement: may
        values:
          - respond-async
          - read-consistent
          - read-eventual-consistent
          - read-cache
          - return=representation
          - return=minimal
      - subject: [http, message, header, Content-Type]
        requirement: should
        values:
          - application/json
  - when: [http, request, method, get]
    then:
      - subject: [http, response, status_code]
        requirement: may
        values:
          - "200"
          - "400"
          - "404"
          - "422"
          - "500"
  - when: [http, request, method, post]
    then:
      - subject: [http, response, status_code]
        requirement: may
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
        requirement: may
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
        requirement: may
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
        requirement: may
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
        requirement: must
        values:
          - Content-Type
  - when: [http, response, status_code, "201"]
    then:
      - subject: [http, response, header]
        requirement: must_not
        values:
          - Link
          - Location
  - when: [http, response, status_code, redirect]
    then:
      - subject: [http, response, header]
        requirement: must_not
        values:
          - Link
          - Location
  - when: [http, response, status_code, client_error]
    then:
      - subject: [http, message, body]
        requirement: must
        follow: error.json
  - when: [http, response, status_code, server_error]
    then:
      - subject: [http, response, body]
        requirement: must
        follow: error.json
  - when: [http, response, status_code, success]
    then:
      - subject: [http, response, body]
        requirement: must_not
        follow: error.json
```
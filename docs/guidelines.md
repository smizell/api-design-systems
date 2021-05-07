# Guidelines

## When would someone use this?

If you're working in a company that is building lots of APIs and want your teams to build APIs that are consistent and follow standards, you could define an API Design System and use it as a way to communicate what people can and can't do. You'll want tooling that uses the API Design System document to automate audits.

## How do you write a requirement?

Let's say we want to specify what status codes people can use for a `GET` request.

- **Consider the condition** - is this requirement related to an HTTP method? For this example, it's the `GET` request, which is `[http, request, method, get]`.

- **Consider the subject** - when a condition is met, what will the requirement apply to? In the example above, the condition would be the `GET` request and the subject would be the response status code. The standard identifier here would be `[http, response, status_code]`.

- **Consider the requirement level** - is this a recommendation? Then use `should`. Does this requirement allow something? Use `may`. If it's a strict requirement, then `must`.

- **Consider the values** - if the condition is a `GET` request and the subject is the response status code, then a possible value in our example would be `"200"`.

It would look something like this.

```yaml
# ... 
design_system:
  - when: [http, request, method, get]
    then:
      - subject: [http, response, status_code]
        level: may
        values:
            - "200"
            # and any other status codes we want to allow
```

## What about more complex conditions?

We're keeping this simple for now. If you have a need for more complex conditions, please get in touch and let us know!
# Specification

This document defines the specification for defining API Design Systems. It's not dependent on any format like JSON or YAML at this point.

## Main

- `version`: `2021-05-07` - current version of the specification
- `info` (Info)
- `standards` (array[Standard])
- `design_system` (array[Design System])

## Info (object)

- `title` - title of API Design System
- `description` (optional) - description of the API Design System

## Standard

- `name` - name used to reference them standard throughout the document
- `url` - URL to documentation for the standard

## Design System (object)

- `when` (Standard Identifier) - references the condition when a requirement applies
- `then` (array[Requirement]) - what to do when the `when` condition is met

##  Requirement

- `subject` (Standard Identifier) - references to the standard the requirement applies to
- `level` (enum[Requirement Level])
- OneOf
    - `values` (array[string]) - acceptable values for the `subject` based on the requirement level
    - `follows` - reference to a `name` from the defined `standards` the `subject` addresses based on the requirement level

## Standard Identifier (array[string])

This identifies a standard or part of a standard. It is used to define the `when` condition to meet along with the `subject` to apply the requirement to. Refer to the supported [Standards](standards.md) page for a list of available identifiers.

## Requirement Level (enum)

These requirement levels are based on [RFC 2119](https://tools.ietf.org/html/rfc2119). Please refer to the RFC for the meaning of these values.

- `must`
- `must_not`
- `should`
- `should_not`
- `may`
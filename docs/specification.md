# Specification

This document defines the specification for defining API Design Systems. It's not dependent on any format like JSON or YAML at this point.

## Main

- `version`: `2021-05-07` - current version of the specification
- `info` (Info)
- `principles` (array[[Principle](#principle)]) - requirements for API principles
- `standards` (array[[Standard](#standard)]) - requirements around standards
- `scenarios` (array[[Scenario](#scenario)]) - requirements based on scenarios

## Info (object)

- `title` - title of API Design System
- `description` (optional) - description of the API Design System

## Principle

A principle is something that's harder to build tools around. However, it's important to capture principles that help guide decisions in building APIs. See the [Principles](principles.md) for available ones.

- `name` - name used to reference them standard throughout the document
- `description` (optional) - description of the principle requirement
- `level` (enum[Requirement Level])
- `iri` - IRI for the principle

## Standard

The best place to find available standards is at [Web Concepts](https://webconcepts.info/).

- `name` - name used to reference them standard throughout the document
- `description` (optional) - description of the standard requirement
- `level` (enum[Requirement Level])
- `iri` - IRI for the standard

## Scenario

- `description` (optional) - description of the scenario
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
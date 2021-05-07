---
title: Overview
---

# API Design Systems

An API Design System is a collection of curated standards, guidelines, practices, and principles aimed at helping teams build consistent, quality APIs.

## Overview

When a company writes an API style guide, they normally write it in Markdown with requirements scattered around the text. The documents might say an API MUST support `application/json` for responses, but it's up to people to read the documentation figure this out on their own. To help, some companies write code that checks API designs or implementations for conformance—usually validating an OpenAPI against a set of rules. But this creates another problem where the tools and documentation can easily get out of sync.

An API Design System tries to address these problem.

Design Systems have become people in the web and application design world. Instead of requiring every team to do their best to conform to the design of the company's brand, companies build a design system that consists of components, tools, and processes that express the brand. Developers can then build applications that are true to the design without having to figure out on their own if they are doing it right. These design systems become a common language of patterns that people across the company can contribute to and share with across many teams.

API Design Systems borrows from these idea. A company should be able to define standards, guidelines, practices, and principles that API teams can follow in order to build APIs true to a company's brand. Instead of wading through documentation looking for requirements, they can get instant feedback as to whether their API fits the design system. 

People can define an API Design System in a machine-readable format so they can build tools and documentation around it. Like how people created OpenAPI out of a need to get API definitions out of text and into something machine-readable, API Design Systems does the same.

## Possible uses for this format

* A tool that looks through an OpenAPI file to manage compliance
* A tool that looks at HTTP traffic to make sure it's compliant
* A tool that renders the document to something human-readable for the API Design System
* A tool to generate a checklist for people to use when evaluating APIs

## Project status

We're currently experimenting with this idea, so the specs and docs will change frequently until we've tried out the idea with real-world examples. Once stable, we'll make sure to not introduce changes to the specification that would cause tools to break. Until then, please contribute ideas and feedback to [Stephen Mizell](https://twitter.com/Stephen_Mizell).
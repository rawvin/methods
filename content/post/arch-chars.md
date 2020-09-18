---
title: "Architectural Characteristics"
date: 2020-09-15T21:10:59-05:00
tags: [Software Architecture, Evolutionary Architecture]
---
{{< blockquote author="Neal Ford">}}
Architecture is abstract until it is operationalized.
{{< /blockquote >}}

## Characteristic Vs Trait


According to Merriam-Webster's dictionary, one of the definitions of the word **characteristic** is _a quality or property of a person or thing_ and the definition of the word **trait** is _an inherited characteristic of a person or thing_

Within the context of software architecture, we could view a characteristic as a generalization of one or more traits that can be applied to a wide range of concerns critical to the success of the architecture.

$$ Trait \subset Characteristic $$

{{< blockquote >}}
A characteristic, also referred to as _Non-Functional Requirement_ or quality attribute, is qualitative in nature. It can be difficult to come up with the right objective tests to measure a characteristic whereas a trait provides a class of attributes to measure how the system is currently used and whether it is meeting expectations using observability techniques and other response indicators.
{{< /blockquote >}}

Below are a few architectural characteristics referenced in the works of [Neal Ford](http://nealford.com/) et al. relevant to cloud native application architectures.

## Agility

- The ability to respond quickly to changing business needs

## Deployability

- The ability to deploy and release services independent of other services it depends on
- The ability to deploy and code using Continuous Delivery pipelines all the way to production

## Testability

- The ability to verify the veracity of certain characteristics of the architecture using automated tests
- The ability to perform testing without requiring an integrated environment

## Evolvability

- Evolvability is a meta-characteristic, an architectural wrapper that protects all the other architectural characteristics.
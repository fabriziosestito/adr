# 3. Use CloudEvents spec

Date: 2022-08-04

## Status

Accepted

## Context

We want to start using [CloudEvents](https://cloudevents.io/) specification to wrap the inter-service communications so the messages structure is standardized. More and more events are being designed in Trento, so this specification implementation will help to make the building and parsing of the messages more straightforward.

## Decision

We will envelope all the inter-service messages using the CloudEvents v1.0 specification. This specification includes fields such as `Event`, `Producer`, `Data`, `Event Format`, etc (find all the full specification at: https://github.com/cloudevents/spec/blob/v1.0.2/cloudevents/spec.md). All of this metadata fields facilitates the message handling in various things like: debugging, tracing, handling discarded messages, parsing, etc
In essence, the messages will be standardized making the communication more robust and better in general.

## Consequences

By using a globally well known specification for describing event data in a common way we get several advantages (borrowed from the [CloudEvents](https://cloudevents.io/) main page):

- Consistency: The lack of a common way of describing events means developers have to write new event handling logic for each event source;
- Accessibility: No common event format means no common libraries, tooling, and infrastructure for delivering event data across environments. CloudEvents provides SDKs for Go, JavaScript, Java, C#, Ruby, PHP, PowerShell, Rust, and Python that can be used to build event routers, tracing systems, and other tools;
- Portability: The portability and productivity we can achieve from event data is hindered overall.



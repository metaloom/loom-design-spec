# Loom Architectural Design Specification

## Requirements

### Non-Functional Requirements

* Security
* Scaleability
* Testability
* Maintainability
* Portability
* Reliability
* Compatibility
* Performance
* Cost
* Usability
* Functional suitability

### Functional Requirements

## Links

* https://github.com/orgs/metaloom
* https://metaloom.io
* https://hub.docker.com/orgs/metaloom

## Goals

## Ideas

* Create Asset Management System / API (no text content handling)
(Deduplication, Thumbnail Handling, Processing, Plugin API, Webhooks)

## Core Concepts

* Easier permission system
* No branches
* Hibernate / JOOQ
* Direct Keycloak support
* S3 Support
* OpenAPI
* Handle all init code via dagger

## Differences

- non-translatable fields
- nestable content references to any depth
- content models are directly accessible (no need to assign them)
- tag families are gone and were replaced by inline properties ('collection')
- roles now have dedicated permissions
- branches are gone
- binary assets are now managed as a dedicated entity
- graphql endpoint is globally accessible and no longer scoped for namespaces (for now)
- S3 support
- webhook support
- plugins are gone and are replaced by external extensions
- languages can now be managed via REST
- search support has been limited to contents (for now)
- users can have multiple API tokens
- API tokens have dedicated permissions
- Full HTTP HEAD support in the API
- Direct native keycloak, auth0 support
- Support for asset fingerprinting
- Support for asset thumbnail generation
- Namespaces can now be import / exported
- Microschemas are gone since content models can be nested
- Users, Groups, Roles, Namespaces can now have arbitrary properties
- Manual tagging will create tags on-the fly. No need to create tags upfront

## Ideas

- Auditing
- Waste Bin Management
- Add nesting flag to models to control depth of allowed nesting? May be confusing when nesting fails due to hard limitation.
- Support models for group, roles, user, namespace as well?
- Time scheduled publishing?
- Access history?
- Group, USer, Role Content References


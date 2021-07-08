# Self-hosted API gateway changelog

## Release - self-hosted gateway: 1.2.3

*July 8, 2021*

New **stable** version of the [self-hosted gateway](https://aka.ms/apim/shgw/overview) is now available. Full list of container versions can be found [here](https://mcr.microsoft.com/v2/azure-api-management/gateway/tags/list).

### New

- Removed the 30MB request size limit

### Bug fixes

None

### Breaking changes

None

## Release - self-hosted gateway: 1.2.2

*June 11, 2021*

New **stable** version of the [self-hosted gateway](https://aka.ms/apim/shgw/overview) is now available. Full list of container versions can be found [here](https://mcr.microsoft.com/v2/azure-api-management/gateway/tags/list).

### New

None

### Bug fixes

- Upgraded to use .NET Core base image 3.1.16 which addressed the following vulnerabilities:

  - CVE-2021-26701 (https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-26701 )
  - CVE-2021-24112 (https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-24112 )

### Breaking changes

None

## Release - self-hosted gateway: 1.2.1

*April 22, 2021*

New **stable** version of the [self-hosted gateway](https://aka.ms/apim/shgw/overview) is now available. Full list of container versions can be found [here](https://mcr.microsoft.com/v2/azure-api-management/gateway/tags/list).

### New

None

### Bug fixes

- Plugged a memory leak in the backend response content processing logic.

### Breaking changes

None

## Release - self-hosted gateway: 1.2.0

*April 20, 2021*

New **stable** version of the [self-hosted gateway](https://aka.ms/apim/shgw/overview) is now available. Full list of container versions can be found [here](https://mcr.microsoft.com/v2/azure-api-management/gateway/tags/list).

### New

1. Support for Kubernetes Ingress object - see https://github.com/Azure/api-management-self-hosted-gateway-ingress.

### Bug fixes

None

### Breaking changes

None

## Release - self-hosted gateway: 1.1.3

*February 18, 2021*

New **stable** version of the [self-hosted gateway](https://aka.ms/apim/shgw/overview) is now available. Full list of container versions can be found [here](https://mcr.microsoft.com/v2/azure-api-management/gateway/tags/list).

### New

1. Updated with support for [Dapr](https://dapr.io) [1.0 release](https://blog.dapr.io/posts/2021/02/17/announcing-dapr-v1.0/).

### Bug fixes

None

### Breaking changes

None

## Release - self-hosted gateway: 1.1.2

*December 18, 2020*

New **stable** version of the [self-hosted gateway](https://aka.ms/apim/shgw/overview) is now available. Full list of container versions can be found [here](https://mcr.microsoft.com/v2/azure-api-management/gateway/tags/list).

### New

None

### Bug fixes

1. Rate limit policy throttling at a lower than configured rate.

### Breaking changes

None

## Release - self-hosted gateway: 1.1.1

*November 3, 2020*

New **stable** version of the [self-hosted gateway](https://aka.ms/apim/shgw/overview) is now available. Full list of container versions can be found [here](https://mcr.microsoft.com/v2/azure-api-management/gateway/tags/list).

### New

None

### Bug fixes

1. TLS connection to upstream is unexpectedly terminated under certain conditions.

### Breaking changes

None

## Release - self-hosted gateway: 1.1.0

*October 14, 2020*

New **stable** version of the [self-hosted gateway](https://aka.ms/apim/shgw/overview) is now available. Full list of container versions can be found [here](https://mcr.microsoft.com/v2/azure-api-management/gateway/tags/list).

### New

1. Migrated to [.NET Core 3.1](https://docs.microsoft.com/dotnet/core/whats-new/dotnet-core-3-1).
2. Migrated to [mcr.microsoft.com/dotnet/core/aspnet:3.1.8-alpine3.12]() base image.

### Bug fixes

1. Connection closed (not re-used) when empty response is received from the upstream.
2. External cache selection is not updated when self-hosted gateway location is changed.

### Breaking changes

None

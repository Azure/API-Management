# Azure API Management service changelog

Developer portal follows an independent release lifecycle and the [per-release changelog is available in the developer portal's GitHub repository](https://aka.ms/apimdevportal/releases).

## Release - API Management service: July, 2021

A regular Azure API Management service update was started on July 5, 2021, and included the following new features, bug fixes, and other improvements. It may take several weeks for your API Management service to receive the update.

### Featured

1. [Native support for WebSocket APIs is now in preview](https://azure.microsoft.com/updates/public-preview-native-support-for-websocket-apis-in-azure-api-management/).
2. [The cost of additional units in the Premium tier services has been reduced](https://azure.microsoft.com/updates/azure-api-management-premium-tier-price-reduction-for-incremental-purchased-units/).

### New

1. You can now emit custom metrics to Azure Application Insights with the new `emit-metric` policy. [Learn more](https://docs.microsoft.com/azure/api-management/api-management-advanced-policies#emit-metric).
2. Policy expressions now support `System.Net.IPAddress`.
3. The policy expressions' `context` object now includes the `context.Deployment.GatewayId` property. For managed gateways, its value is `managed`.
4. You can now export your APIs for consumption in the Power Platform through the dedicated Power Platform page in the Azure portal.
   ![Power Platform page in the Azure portal](media-api-management-service/2021-07-azure-portal-power-platform.png)

### Fixed

1. We fixed an issue, which caused Developer tier services in a virtual network to not emit resource health events.
2. The validation policies now correctly return:
   * Responses with the status code `400 Bad Request` and a precise error description in case of the schema mismatch for errors detected in the incoming requests.
   * Responses with the status code `502 Bad Gateway` and a generic message in the body for errors detected in the outgoing responses, to not leak API implementation details.
3. We fixed an issue, where the validation policies modified the format of the JSON payload's properties resembling datetime strings.
4. We fixed an issue, where a character sequence `@*` prevented the policy XML document from being saved.
5. We fixed an issue, where responses with an empty payload and the `Transfer-Encoding: chunked` header were incorrectly classified as completed and the response latency was miscalculated.
6. We fixed an issue, where successful API requests were marked as non-successful in the Azure Monitor and Azure Application Insights logs if the client disconnected right after receiving the response.
7. We fixed an issue, which caused the API gateway endpoint of Consumption services to remain unavailable for a few seconds after the service activation.

### Changed

1. Validation policies' `error-variable-name` attribute is now optional.

## Release - API Management service: May, 2021

A regular Azure API Management service update was started on May 5, 2021, and included the following new features, bug fixes, and other improvements. It may take several weeks for your API Management service to receive the update.

### Featured

1. [Open-source API Portal is now generally available](https://azure.microsoft.com/updates/apiportal/).
2. [Azure API Management's support for Availability Zones is now generally available](https://azure.microsoft.com/updates/azure-api-management-support-for-availability-zones-now-generally-available/).
3. [Request and response validation policies are now generally available](https://azure.microsoft.com/updates/azure-api-management-support-for-request-and-response-validation-policies-has-reached-general-availability/).

### New

1. You can now validate the client certificate with the new `<validate-client-certificate>` policy. Documentation and support in the Azure portal are coming soon.
2. The Visual Studio Code extension now supports policy debugging for self-hosted gateways running locally.
3. The Visual Studio Code extension now supports Dapr and validation policies.
4. The developer portal now supports *resource owner password* grant flow.
5. The new *Ciphers + Protocols* page in the Azure portal lets you manage API gateways' cipher and protocol configuration and displays a warning if a weak cipher or protocol is enabled.
6. The *Locations* page in the Azure portal lets you now configure Availability Zones.
7. You can now apply [validation policies](https://aka.ms/apimdocs/policies/validation) with the visual policy editors in the Azure portal, without writing any policy code.
8. The `timeout` attribute of the `send-request` policy now supports policy expressions.

### Fixed

1. Caching issues, which might have resulted in a broken developer portal's administrative interface, are now resolved.

### Changed

1. The client certificate renegotiation feature is now disabled for all new and existing API Management services, except for the services that relied on it in the last 30 days (services with at least one API call that resulted in a client certificate request from a policy, not as part of an initial TLS handshake). The API gateway will request a client certificate only if [`HostnameConfiguration`'s](https://docs.microsoft.com/rest/api/apimanagement/2019-12-01/apimanagementservice/createorupdate#hostnameconfiguration) property `negotiateClientCertificate` is set to `true`. If the property is set to `false`, the client certificate won't be available in the `context.Request.Certificate` property.

## Release - API Management service: March, 2021

A regular Azure API Management service update was started on March 8, 2021, and included the following new features, bug fixes, and other improvements. It may take several weeks for your API Management service to receive the update.

### Featured

1. [Integration of named values with Azure Key Vault is now generally available](https://azure.microsoft.com/updates/general-availability-azure-api-management-now-has-named-values-integration-with-azure-key-vault/).
1. [Integration of certificates with Azure Key Vault is now generally available](https://azure.microsoft.com/updates/support-for-azure-api-management-certificates-in-azure-key-vault-has-reached-general-availability/).
1. [Visual Studio Code extension is now generally available](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-apimanagement).
1. [API Management diagnostics are now in public preview](https://azure.microsoft.com/updates/api-management-diagnostics-now-available-in-public-preview/).

### New

1. You can now add an Application Insights logger by specifying a connection string. Support for this feature in the Azure portal is coming soon.

### Fixed

1. List, GET, PUT, and PATCH operations on named values managed in a key vault are no longer allowed in API versions prior to `2020-06-01-preview`. Those named values will no longer be exported in ARM templates.
1. Recreating a user-assigned managed identity with the same Azure resource ID no longer results in an error.

### Changed

1. Metrics and monitoring endpoints now use a new DNS service with higher availability. If you have been using the hostname to filter the traffic, make sure to change it to the new address. Otherwise, no action is required; the IP address of the resources has not changed.
    - `https://global.metrics.nsatc.net/` has changed to `https://global.prod.microsoftmetrics.com/`.
    - `https://prod3.metrics.nsatc.net:1886/RecoveryService` has changed to `https://prod3.prod.microsoftmetrics.com:1886/RecoveryService`.
1. Managed identity no longer requires outbound access to Certificate Revocation List endpoints. If you have configured network connectivity to allow outbound traffic to CRL endpoints, you may now remove this dependency.

## Release - API Management service: January, 2021

A regular Azure API Management service update was started on January 21, 2021, and included the following new features, bug fixes, and other improvements. It may take several weeks for your API Management service to receive the update.

### New

1. You can now use the `cache-response` attribute in the `cache-store` policy to specify when to cache the outgoing HTTP response. For example, `<cache-store cache-response="@{return true}" />` will cache all API responses. If the `cache-response` attribute isn't specified, only HTTP responses with the status code `200 OK` will be cached. Documentation will be updated soon.
1. You can now view service summary, explore service recommendations, and access additional resources in the redesigned overview page in the Azure portal.
    ![Azure portal - overview](media-api-management-service/2021-01-azure-portal-overview.png)
1. You can now use the `isKeyVaultRefreshFailed=true` query parameter in the list certificates by service and list named values by service API calls in the API version 2020-06-01 or later to find the entities, for which the refresh from Azure Key Vault action failed. Documentation will be updated soon.
1. You can now monitor connectivity to Azure Key Vault using the network status endpoint in the API version 2020-06-01-preview or later.

### Fixed

1. We fixed an error, which could cause named values and certificates stored in Azure Key Vault to not be refreshed.

## Release - API Management service: December, 2020

A regular Azure API Management service update was started on December 7, 2020, and included the following new features, bug fixes, and other improvements. It may take several weeks for your API Management service to receive the update.

### New

1. You can now create and manage API backends in the Azure portal.
    ![Azure portal - backends view](media-api-management-service/2020-12-backends.png)
1. You can now log [API inspector traces](https://docs.microsoft.com/azure/api-management/api-management-howto-api-inspector#trace-a-call) to Application Insights and Azure Monitor by setting the `verbosity` property of [the `service/diagnostics` resource](https://docs.microsoft.com/azure/templates/microsoft.apimanagement/service/diagnostics) to `debug`. Azure portal interface for this feature will be released in early 2021.
1. You can now mask or hide sensitive query parameters and headers in diagnostic logs. The `hide` setting will remove an entity, while `mask` setting will replace it with the word "hidden". Refer to [the `service/diagnostics` API endpoint documentation](https://docs.microsoft.com/rest/api/apimanagement/2020-06-01-preview/diagnostic/createorupdate#datamasking) for more details. Azure portal interface for this feature will be released in early 2021.
1. You can now monitor database connectivity in secondary regions in the `Network Status` page in the Azure portal as well as via the respective API call, if your API Management service is deployed in multiple regions.
1. [New management API version `2020-06-01-preview`](https://docs.microsoft.com/rest/api/apimanagement/) is now available for testing.

### Fixed

1. Elements of collections in responses from the `Content Types` and `Content Items` management API endpoints no longer overlap between pages.

## Release - API Management service: October, 2020

A regular Azure API Management service update was started on October 21, 2020, and included the following new features, bug fixes, and other improvements. It may take several weeks for your API Management service to receive the update.

### New

1. You can now create Developer, Basic, Standard, or Premium API Management services in the Brazil Southeast region.
1. `xml-to-json` policy supports two new parameters for handling empty values and trimming string values:

    ```xml
    <xml-to-json empty-values="preserve|asNull" trim="true|false" />
    ```

1. `context.Request.Body` and `context.Response.Body` support three new methods:
    
    ```csharp
    JToken AsJToken(bool preserveContent = false, JsonSerializerSettings settings = null);
    JObject AsJObject(bool preserveContent = false, JsonSerializerSettings settings = null);
    JArray AsJArray(bool preserveContent = false, JsonSerializerSettings settings = null);
    ```

1. Liquid templates in the `<set-body>` policy now support accessing JObject and JArray variables, for example: `context.Variables.contoso.property` or `context.Variables.contosoarray[0].property`.
1. `validate-jwt` policy now supports JWE tokens compressed with the [default algorithm](https://tools.ietf.org/html/rfc7516#section-4.1.3).
1. `Network Status` API now returns status for the Azure Active Directory endpoint.
1. `Named Values` API now supports filtering by ID.

### Fixed

1. Developer portal session is now correctly persisted in case of redirects to other websites. Previously, the session could have been lost when using sign-in delegation or redirecting to websites from e-mail notifications.
1. Developer portal now supports additional OAuth parameters for acquiring access tokens, which enables integration with external identity providers, like Auth0.
1. API Management now correctly handles wildcard OpenAPI parameters, such as `/sample-operation/{*rest}`.
1. We fixed several bugs, which could result in inaccurate `Network Status` API responses.
1. We fixed a bug, where API Management stored incorrect payload in the cache if a request contained conditional headers `If-Modified-Since` or `If-None-Match` and cache entry didn't exist.

### Changed

1. The [`Connection` header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Connection) is no longer forwarded from the backend to the client.
# Azure API Management service changelog

## Release - API Management service: October, 2020

A regular Azure API Management service update was started on October 21, 2020, and included the following new features and bug fixes, along other improvements. It may take several weeks for your API Management service to receive the update.

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

Developer portal follows an independent release lifecycle and the [per-release changelog is available on GitHub](https://aka.ms/apimdevportal/releases).
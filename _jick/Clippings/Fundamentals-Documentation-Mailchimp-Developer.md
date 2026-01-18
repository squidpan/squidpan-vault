---
title: "Fundamentals Documentation | Mailchimp Developer"
source: "https://mailchimp.com/developer/marketing/docs/fundamentals/#the-basics"
author:
  - "[[@mailchimp]]"
published:
created: 2025-10-13
description: "Learn the basics of the Mailchimp Marketing API."
tags:
  - "clippings"
---
## Fundamentals

## The basics

The Mailchimp Marketing API provides programmatic access to Mailchimp data and functionality, allowing developers to build custom features to do things like sync email activity and campaign analytics with their database, manage audiences and campaigns, and more.

To use the Marketing API, you need a Mailchimp account. What you can do with the API depends on what [level of Mailchimp plan](https://us1.admin.mailchimp.com/account/billing-plan/) you have. Once you have an account and are logged in, you can [get an API key](https://us1.admin.mailchimp.com/account/api/) and [begin making calls to the API](https://mailchimp.com/developer/marketing/guides/quick-start/).

### Using Mailchimp

Whether you’re managing your own campaigns, providing Mailchimp services to your customers or clients, or writing a mobile app, the Mailchimp Marketing API has features to manage and sync your contact data.

Audiences are at the core of sending campaigns with Mailchimp. You can use the Marketing API to [set up an audience](https://mailchimp.com/developer/marketing/guides/create-your-first-audience/) and add contacts to that audience; you can then organize those contacts with [tags](https://mailchimp.com/developer/marketing/guides/organize-contacts-with-tags/) or segment them by activity with [events](https://mailchimp.com/developer/marketing/guides/track-outside-activity-events/).

The Marketing API can also be a source of data for your application. [Webhooks](https://mailchimp.com/developer/marketing/guides/sync-audience-data-webhooks/) collect and transmit information about your audience to you in near real time. And if you’re selling products on an external store, you can integrate your audience behavior using Mailchimp’s  [E-commerce features](https://mailchimp.com/developer/marketing/docs/e-commerce/).

You can also use the Marketing API to handle data in different ways for different purposes. If you are syncing a large amount of data with Mailchimp, you can use [batches](https://mailchimp.com/developer/marketing/guides/run-async-requests-batch-endpoint/) to avoid hitting the API request limits. For building integrations that let other users access data from their own Mailchimp accounts, you should [authenticate with OAuth 2](https://mailchimp.com/developer/marketing/guides/access-user-data-oauth-2/). And if you’re developing an app for iOS or Android, the [Mobile SDK](https://mailchimp.com/developer/marketing/docs/mobile-sdk/) provides an easy way to work with a mobile-focused subset of the Marketing API’s functionality.

### API versions

The Marketing API is currently on version 3.0.

We also support a single-purpose Export API version 1.0, which provides API support for some of our . See the [Export API documentation](https://mailchimp.com/developer/marketing/docs/export-api/) for full details.

The first versions of the Marketing API, versions 1.1, 1.2, and 1.3, are no longer available.

The previous version 2.0 has not been shut off, but is deprecated and unsupported. We’ll announce shut off dates in advance, but we recommend migrating to version 3.0 since version 2.0 is not regularly tested or maintained.

## API structure

The Marketing API generally follows REST conventions, with some deviations.

- *Resources* are typically nouns like `subscribers` or `campaigns`.
- *Subresources* can be multiply nested under resources.
- *Actions* are usually represented by [HTTP methods](https://mailchimp.com/developer/marketing/docs/methods-parameters/). Actions that do not correspond to HTTP methods are collected under an `actions/` subresource.
- *Responses* use the generic JSON content type.

We use the [OpenAPI Specification](https://swagger.io/specification/v2/) (formerly known as Swagger) to describe each endpoint. [The API self-description](https://api.mailchimp.com/schema/3.0/Swagger.json?expand) also contains type information to help you error-check your requests.

The root url for the API is `https://<dc>.api.mailchimp.com/3.0/`. The `<dc>` part of the URL corresponds to the data center for your account. For example, if the data center for your account is `us6`, all API endpoints for your account are available relative to `https://us6.api.mailchimp.com/3.0/`.

There are a few ways to find your data center. It’s the first part of the URL you see in the [API keys section](https://us1.admin.mailchimp.com/account/api/) of your account; if the URL is `https://us6.mailchimp.com/account/api/`, then the data center subdomain is `us6`. It’s also appended to your API key in the form key-dc; if your API key is `0123456789abcdef0123456789abcde-us6`, then the data center subdomain is `us6`. And finally, if you’re connecting via OAuth 2, you can find the data center associated with the token via the OAuth Metadata endpoint; for more information, see the [OAuth guide](https://mailchimp.com/developer/marketing/guides/access-user-data-oauth-2/#implement-the-oauth-2-workflow-on-your-server).

**Note**: You will see the `<dc>` placeholder or an actual data center subdomain in examples throughout this documentation. Either way, make sure to replace it in your code with the data center subdomain for your account, or your request may generate an error.

For more details on how to query Marketing API endpoints, see [Methods and Parameters](https://mailchimp.com/developer/marketing/docs/methods-parameters/). For troubleshooting API calls, see the [Errors](https://mailchimp.com/developer/marketing/docs/errors/) docs.

## Connecting to the API

You can authenticate requests using either your API key or an OAuth access token, depending on your use case. You should use an API key if you’re writing code that tightly couples *your* application data to *your* Mailchimp account data; if you ever need to access *someone else’s* Mailchimp account data, you should use OAuth 2.

For more information on the Mailchimp OAuth 2 flow, see [Access Data on Behalf of Other Users with OAuth 2](https://mailchimp.com/developer/marketing/guides/access-user-data-oauth-2/).

If you’re integrating with the Marketing API using one of the [official client libraries](https://mailchimp.com/developer/tools/), you won’t need to worry about the implementation details for authentication.

### Authenticate with an API key or OAuth 2 token

API keys and OAuth 2 tokens can be used to make authenticated requests the same way. We’ll refer to both as tokens.

You can either use HTTP Basic Authentication or Bearer Authentication.

HTTP Basic Authentication:

```bash
curl --request GET \
--url 'https://<dc>.api.mailchimp.com/3.0/' \
--user 'anystring:TOKEN
```

Bearer Authentication:

### User API access

API authentication is tied to the user that created the API key or authorized the OAuth2 app. If the user is removed from the account, that authentication token will be revoked.

API access is also limited by the of the authorizing user. The role is not fixed, and can change over time. You can check the role for an API key using the [API Root endpoint](https://mailchimp.com/developer/marketing/api/root/), and see the restrictions in . Attempts to perform an API action that aren’t permitted for the role will return a [403 error](https://mailchimp.com/developer/marketing/docs/errors/#error-glossary). When creating an API key or authorizing an app, we recommend using an admin user when possible. OAuth integrators may want to inform the user if the application won’t work at their user level.

**Note**: You are responsible for the security of API tokens; we recommend that you store them in a secure location on your server. Because of the potential security risks associated with exposing an API token, Mailchimp does not support client-side implementation of our API using CORS requests.

## API limits

To improve the experience for all our users, we impose some limits on API requests. These limits prevent a single user from making too many expensive calls at once. Exceeding the limits can result in your API access being disabled, so be cognizant of the quantity and complexity of your requests. Currently there are no options to raise the limit on a per-customer basis.

### Throttling

The Marketing API has a limit of 10 simultaneous connections. You’ll receive a [429 error](https://mailchimp.com/developer/marketing/docs/errors/#error-glossary) if you reach the limit. At exceptionally high volumes, you may receive an HTTP 429 or 403 without a JSON body.

We recommend that you cache frequently accessed values that do not change often in your application’s data store. This will prevent your application from bumping up against the throttling limitations and will likely provide faster access to that data.

### Stream timeouts

The Marketing API has a 120-second timeout on API calls. You may see this type of timeout after you’ve made a network socket connection and are already sending and receiving data.

Response times are dependent on the complexity of your request and the general load across Mailchimp. Some endpoints in the Marketing API return values that are large and slow to calculate. Once you know what data you need, use the [pagination and partial response capabilities](https://mailchimp.com/developer/marketing/docs/methods-parameters/#query-string-parameters) to request only what is essential to you.

**Note**: If you’re regularly seeing issues with timeouts and are unable to optimize your requests using pagination, you might consider [sending long-running requests to the Batch endpoint](https://mailchimp.com/developer/marketing/guides/run-async-requests-batch-endpoint/).
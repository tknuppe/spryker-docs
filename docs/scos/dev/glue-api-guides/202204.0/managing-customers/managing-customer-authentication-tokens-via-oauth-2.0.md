---
title: Managing customer authentication tokens via OAuth 2.0
description: This endpoint allows authenticating as a customer and refreshing customer authentication tokens via OAuth 2.0.
last_updated: Jun 21, 2021
template: glue-api-storefront-guide-template
originalLink: https://documentation.spryker.com/2021080/docs/managing-customer-authentication-tokens-via-oauth-20
originalArticleId: 4fe6c88f-3879-4f9f-bb91-c6a867d120fa
redirect_from:
  - /2021080/docs/managing-customer-authentication-tokens-via-oauth-20
  - /2021080/docs/en/managing-customer-authentication-tokens-via-oauth-20
  - /docs/managing-customer-authentication-tokens-via-oauth-20
  - /docs/en/managing-customer-authentication-tokens-via-oauth-20
  - /docs/scos/dev/glue-api-guides/201811.0/managing-customers/managing-customer-authentication-tokens-via-oauth-2.0.html
  - /docs/scos/dev/glue-api-guides/201903.0/managing-customers/managing-customer-authentication-tokens-via-oauth-2.0.html
  - /docs/scos/dev/glue-api-guides/201907.0/managing-customers/managing-customer-authentication-tokens-via-oauth-2.0.html
  - /docs/scos/dev/glue-api-guides/202005.0/managing-customers/managing-customer-authentication-tokens-via-oauth-2.0.html
related:
  - title: Authentication and authorization
    link: docs/scos/dev/glue-api-guides/page.version/authentication-and-authorization.html
  - title: Searching by company users
    link: docs/scos/dev/glue-api-guides/page.version/managing-b2b-account/searching-by-company-users.html
  - title: Confirming customer registration
    link: docs/scos/dev/glue-api-guides/page.version/managing-customers/confirming-customer-registration.html
  - title: Authenticating as a customer
    link: docs/scos/dev/glue-api-guides/page.version/managing-customers/authenticating-as-a-customer.html
  - title: Managing customer authentication tokens
    link: docs/scos/dev/glue-api-guides/page.version/managing-customers/managing-customer-authentication-tokens.html
  - title: Managing customers
    link: docs/scos/dev/glue-api-guides/page.version/managing-customers/managing-customers.html
  - title: Managing customer passwords
    link: docs/scos/dev/glue-api-guides/page.version/managing-customers/managing-customer-passwords.html
  - title: Managing customer addresses
    link: docs/scos/dev/glue-api-guides/page.version/managing-customers/managing-customer-addresses.html
  - title: Retrieve customer carts
    link: docs/pbc/all/cart-and-checkout/manage-using-glue-api/retrieve-customer-carts.html
  - title: Retrieving customer orders
    link: docs/scos/dev/glue-api-guides/page.version/managing-customers/retrieving-customer-orders.html
---

This endpoint allows authenticating as a customer and refreshing customer authentication tokens via OAuth 2.0.

## Installation

For detailed information on the modules that provide the API functionality and related installation instructions, see [GLUE: Customer Account Management feature integration](/docs/scos/dev/feature-integration-guides/{{page.version}}/glue-api/glue-api-customer-account-management-feature-integration.html).

## Authenticate as a customer

To authenticate as a customer, send the request:

---
`POST` **/token**

---

### Request

| HEADER KEY | HEADER VALUE | REQUIRED | DESCRIPTION |
|-|-|-|-|
| Content-Type | application/x-www-form-urlencoded | &check; | `x-www-form-urlencoded` is a URL encoded form. This is the default value if the encrypted attribute is not set to anything. The keys and values are encoded in key-value tuples separated by `&`, with a `=` between the key and the value. Non-alphanumeric characters in both keys and values are percent encoded. |

<details><summary markdown='span'>Request sample: authenticate as a customer</summary>

| REQUEST BODY KEY | VALUE |
|-|-|
| grant_type | password |
| username | sonia@spryker.com |
| password | change123 |

</details>

| ATTRIBUTE | TYPE | REQUIRED | DESCRIPTION |
|-|-|-|-|
| grant_type | password | &check; | Method through which the application can gain Access Tokens and by which you grant limited access to the resources to another entity without exposing credentials. |
| username | String | &check; | Customer's username. You define it when [creating a customer](/docs/scos/dev/glue-api-guides/{{page.version}}/managing-customers/managing-customers.html#create-a-customer). |
| password | String | &check; | Customer's password. You define it when [creating a customer](/docs/scos/dev/glue-api-guides/{{page.version}}/managing-customers/managing-customers.html#create-a-customer). |

### Response

<details><summary markdown='span'>Response sample: authenticate as a customer</summary>

```json
{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiJmcm9udGVuZCIsImp0aSI6IjE5YWZmNDI4NzA0M2UxMGNjODc3MGM4ZjBkYTkwOTEwOWExYWQzMjdhNWM3MTY2ZjJjYzhhOGZkNDFjYzliM2ZmZGJjOWRmNjE0ZjRhZTUzIiwiaWF0IjoxNjE1MzcyOTI2LCJuYmYiOjE2MTUzNzI5MjYsImV4cCI6MTYxNTQwMTcyNiwic3ViIjoie1wiaWRfY29tcGFueV91c2VyXCI6XCJlYmY0YjU1YS1jYWIwLTVlZDAtOGZiNy01MjVhM2VlZWRlYWNcIixcImlkX2FnZW50XCI6bnVsbCxcImN1c3RvbWVyX3JlZmVyZW5jZVwiOlwiREUtLTIxXCIsXCJpZF9jdXN0b21lclwiOjIxLFwicGVybWlzc2lvbnNcIjp7XCJwZXJtaXNzaW9uc1wiOlt7XCJpZF9wZXJtaXNzaW9uXCI6MSxcImtleVwiOlwiUmVhZFNoYXJlZENhcnRQZXJtaXNzaW9uUGx1Z2luXCIsXCJjb25maWd1cmF0aW9uXCI6e1wiaWRfcXVvdGVfY29sbGVjdGlvblwiOlsyOCwyNywyNSwyNCwyMywyMiwyMV19LFwiY29uZmlndXJhdGlvbl9zaWduYXR1cmVcIjpcIltdXCIsXCJpZF9jb21wYW55X3JvbGVcIjpudWxsLFwiaXNfaW5mcmFzdHJ1Y3R1cmFsXCI6bnVsbH0se1wiaWRfcGVybWlzc2lvblwiOjIsXCJrZXlcIjpcIldyaXRlU2hhcmVkQ2FydFBlcm1pc3Npb25QbHVnaW5cIixcImNvbmZpZ3VyYXRpb25cIjp7XCJpZF9xdW90ZV9jb2xsZWN0aW9uXCI6WzI4LDI3LDI1LDI0LDIzLDIyLDIxXX0sXCJjb25maWd1cmF0aW9uX3NpZ25hdHVyZVwiOlwiW11cIixcImlkX2NvbXBhbnlfcm9sZVwiOm51bGwsXCJpc19pbmZyYXN0cnVjdHVyYWxcIjpudWxsfSx7XCJpZF9wZXJtaXNzaW9uXCI6bnVsbCxcImtleVwiOlwiUmVhZFNob3BwaW5nTGlzdFBlcm1pc3Npb25QbHVnaW5cIixcImNvbmZpZ3VyYXRpb25cIjp7XCJpZF9zaG9wcGluZ19saXN0X2NvbGxlY3Rpb25cIjp7XCIwXCI6MSxcIjJcIjoyLFwiM1wiOjN9fSxcImNvbmZpZ3VyYXRpb25fc2lnbmF0dXJlXCI6W10sXCJpZF9jb21wYW55X3JvbGVcIjpudWxsLFwiaXNfaW5mcmFzdHJ1Y3R1cmFsXCI6bnVsbH0se1wiaWRfcGVybWlzc2lvblwiOm51bGwsXCJrZXlcIjpcIldyaXRlU2hvcHBpbmdMaXN0UGVybWlzc2lvblBsdWdpblwiLFwiY29uZmlndXJhdGlvblwiOntcImlkX3Nob3BwaW5nX2xpc3RfY29sbGVjdGlvblwiOntcIjBcIjoxLFwiMlwiOjIsXCIzXCI6M319LFwiY29uZmlndXJhdGlvbl9zaWduYXR1cmVcIjpbXSxcImlkX2NvbXBhbnlfcm9sZVwiOm51bGwsXCJpc19pbmZyYXN0cnVjdHVyYWxcIjpudWxsfV19fSIsInNjb3BlcyI6WyJjdXN0b21lciJdfQ.MORe796POXfe4_VyQQoW-Aa9b9VpWrhQK3tBK-0Y463pg9yhoDRVG1izyqFkN6BHcucAVhV-xRvV-qPohJUhy92pLptFZMz3vxLtiE0EDRq2DrDFKh-O7f7rJgp7axIVXju5V0IxudEaj0Tz9XrKigWSPJ1kmIuSI8eQfmttSm5lw2YM8u22Y4p4pdN3Zhn4vz9r5w0CuwhcXKl8G1x_aK_PCTRa8OgX6VpPACZEidxr6suc5novyovaATV0lUqnIia0_DbsA0h1Pafu-WZnTpP_OhheqOI5k1Oq11Q8-ZvrG8vlLGg4JzGzMyXNe80uD1RNttqGn1HqsgOZfxTZGg",
    "token_type": "Bearer",
    "expires_in": 28800,
    "refresh_token": "def502009ca20f366fa7340f40e3c4c7246557d03b9d098301f8aa4289d7467690ff11db19a8151f3b475c4026fcecf94149b5acb51b964416f17e7f9c5dc6dfbc1c75a89d3b99234de175d3d78fa2650f1f07a7281856762189ac72f721a278cc020ffcf1335beccca4d36841ee32666c80b8ce21578a987867ad4e4cff268c9d70640a9c6fc6fd689a9b487bc131984f75ccbd473a451755e0bef6ad99fbf131c851f5b18e3a64f22cf8ded63acca1f60e31a048c30f5e18c1eca28bcad3c50ca07a2dc9afb66a4fb65c3e8f13e802578d3d29462da73c9bfc0aea153032ed2d49a9ee99231fbad475a3d76e387ebe430679bee32f0175905ffc18c4cfbe52375dfde14766eb19be76a3f2f193e48c55221f942b273d9b7a76df66291157c2f72a2cd8cc10c7d01b7b5e5084f478f32ee73e81dc2111907ef37b03dc4b1aa217552d9bfc31b2f3bf80769cc78e58aa29ac8cf5edf77e8ec913f85bbbb8714e9f93527043150cc1ed425ddae5bb191d6aa44a7335c03f1050feb70ed8577cbfb649f84db9cd5ca8651c20122da9a4989fe60cf7443af6eee87d7deb5f9a5655c5b6505ff5f63c599fc77e3586902074a35b8a814fbaacaa4417d4864c60fb1b97297ddccdd35570bcf97dd74434563bb6eedf1beacb93006292a491781d688c4a0c6edb4c9e15f997b774c68d487424e66f8b718c216b8a3d982e1418fb68a87a5f8fae5901b181521c1b7c7f14842b80bb7e3d135b71adb8d7cf2ebbd01412a2c9a4812e3928bfbde2e78909f5c1f943f05a64d52357d9e42692992d3ce4fdec049078b859e58980723bb5c338b10712073d5531a29ba593c173f9840abfc0ecb1380b115e8e18c2cbd28087e445ee2a7cabf680c6e1b7bef83612f29adfcd21eec4bbd83cb49fbfb2bdb887c4afd155d927798d248e53cab6ae258b3a5c9b904a57c822b8007b0583bff7fc57b040300934aaeac959d6551607d2d1f6980a9eea933d6033c639968040cb2e09f1ff0d160f55df15811d085d2635f434bef2987c94d70b4fe39894ab725042c2d4e7a1e315665af62ac76ff079a37b44fcca688467323d954e56c34539db9f67dbc91e90fbb91892721d4caa296bf35eb49de5e298e9708807f734655484d8aec56b5b25c96b8792f6250c5c14c901b94f6056693462d11bca8d3855ed62704325cc1c44d2875f3af5075212135d6343f40ef59d62ba39705b14f9fb51a9725c7f865b8474702d9a0d4671030de6c17aaf27e2c4552e7f23a0db25f7ad23300159273b0dd8e2887b2eb7f8e3fd6e969e2356c03a54c43677c492173f049b186b40f8af48b857be723b738e068fe683feae78913a70d1e8ec04601794eac71b388d9ee8fc41ad9f91001ddfc6efcd2f2203fe9618ea992865b13358dee95d1893bb748fe0d64c7ccd3aae1cb5ca86bc8f8ee13a8f7a02988f1e2d14dd6b060654b80b46335b6d26a84af1aeace63a6f904cfefabc5132b6c053d00af3398bcbe3ca050145715f0a12686d532fa6294bcc39d6d78456df2272347437d016839dbb3807ecd46d89c395e7ac075ba6675bcd8be444cb398d7e642f7bc4b413ba55596dd7f65d8005e89013f4df36f699eae1e03cad7201b077b3d5e95a3cf1a28edb69aafc371ac5dae57da53d43b3b5afe0dbcd1820662f05d225ab4449700c0b800fb52fcb853e74bed4f9c8c65ea2765722cede3a57a1749e74d62b90265a0445f850433c01ab805080c727c6ce620a00a161228c5d5cc8011dc775d50aae4015d5255aa7bec4abd53a68508c3961f2e03b6d461ad442a09329b57a3d501c2ddf6482ca631973727c01e8c23e08916af1f7153c43df907f8dc9bdcaecb9a93d79bcff05645fdacbb6df911112d916e99e2025f0d3f89cfbcb2cd327dbc6643c0dd078dda6a3473ba21a0ccfb8aa515fd812f7416cf6244b2034607f8ad8d77000f29c1b20a3040bbb5e6712c7a53b8b19868ea999422250a38b4cfe96217c800703797c05ea063d08c204c6d4b58d4708241a41b5cfde5554"
}
```
</details>

| ATTRIBUTE | TYPE | DESCRIPTION |
|-|-|-|
| access_token | String | Authentication token used to send requests to the protected resources available for this customer. |
| token_type | String | Type of the authentication token. Set this type when sending a request with the token. |
| expires_in | Integer | Time in seconds in which the `access_token` token expires. |
| refresh_token | String | Authentication token used to refresh `access_token`. |

### Refresh an authentication token

To refresh an authentication token, send the request:

---
`POST` **/token**

---

### Request

| HEADER KEY | HEADER VALUE | REQUIRED | DESCRIPTION |
|-|-|-|-|
| Content-Type | x-www-form-urlencoded | &check; | `x-www-form-urlencoded` represents a URL encoded form. This is the default value if the encrypted attribute is not set to anything. The keys and values are encoded in key-value tuples separated by `&`, with a `=` between the key and the value. Non-alphanumeric characters in both keys and values are percent encoded. |

<details><summary markdown='span'>Request sample: refresh an authentication token</summary>

| REQUEST BODY KEY | VALUE |
|-|-|
| grant_type | refresh_token |
| refresh_token | `def50200ef59d199dfbae496fcb5bfc942377da65539e02fd0543e57b5084ac578b3146868bdaf2e5170bdb974e9cf7a431c17e000f0db564beefa89497b1cb1514dc516264eb79c0ebca240815791b075d4a950fa34e3b0fbabac7324663ce37999c206aca5faab7cd673a7f17fceb2ef10a7e11ddc1af7e22f21741cf16f789cb604da205332f813c2dd4cd3d57f6a8839bd5cd955dd068b71fab3cd2a1b591c57367217f9dcf48bbad79a28c424aa746b57940cb5f248d5d99244046921dc9c8be8aa6213d8bda2b7f9346c0ff318920c5a767d50a80e633506bf9328cda2506ba6339a300d8310d9cbbd2e4f86aa1b166023e6a84fa6360dcbb898cfbb8f65fc02710fef69ec5f3c2d133d97986488d6bde8321c166d6963a39bde3a9cdbf748995a9a3e79657bcf6fd76e90372ea3486fc023e53ab21f8034049073044be591f57dd3a980c3d69777a2f564a6418540d52f38777d9d17aa24fc83a11880e9f2510950b7b589737b421f077c69c4c40d5e5644e01a7da016df8fed447e62e3db3710ae229391b92aafa7c123204854e1e2f2c49411084eab25deab14615da3d118fe32e72c76b746a845cf7fbc156f64363e4d0c4e8d1a9941f7be5fb80ddd62c2eb6f29564792c0f6ee8db97be653c91687ce2a5bc74edee0472c8416bb446fc3ee7a1a37f7b13ca161a6c61bdb1b42df8b8bd0f3d7d788573ff37fe7de360c123eb4c737d65d5a4f8d02584d1fb6f74e27f05a40f8d18f745ffad1c3fc9e0879abd8e7ef0365b4efa85c6cb2603acf5a04e0630d82895e990180b5957780e93c48aaaf13341f7c485a479f50d5c505478ed3e50967fa0e25e3c3eb5e6199bd180d1d04fa98a318870dc492d190d546ea39648f11ba2a35f4d61d2eea8a4f3f28fc3cde19056194d2d722cb78ef9d8180917a7f887b50083c5b04f93de87c53c6912681f46153bfe90050eaad1ce2f169f03eee2fcdc48e736c63cff74c066def47acf41c4d90a142fa9282e17584abe5ad60abf2aee235b77d4fad2707be75653fc43013a5d0b8b812aa75cd1ffbc1b06b9cfe4d38c896f26049b3607a62f15da685a93d25fcc94ce693de793f9103ccd644f3a9b138d994951cc44fcbc17a2c7a8ec611441d3a8327213e03d2101a0602276b864ada2ef6e9620507ed82a7c9bcdf98abc821b9c4146a6ff20f0ea35771caa17fd515d4220975408138312a9ebff7d895476537f0b0c3329da6af3669767feddbdfe9b989a38be8e3b74507a8951236b2fd465886e7d23503d953d0f476ab269107c14f0306791ae6b0dc048d5c3d0e6433da70519298b66d265175e940e99da76d3410fa1d4db426e613b99e023cc0bd14130bdd77025250690fec407f94e823722443679a98a54c5082a705e61f317ac9199efaa26726e08245e40d80b22053ae74c2b84c8dbd0e707badb1f188e506839628bc02d96bf6526841f126c1c27d1a264fdb10d8fef957f95c71ecea09f0f5bea92f19543e8216703a72897ee123244cf4cedd74ee0694d4758ea86f7d42ea372dbe622af9939b57509662db0ca558aa7c6b586dd8047891c434eac7b9c77c298b20c569dd3b3baca84f0f98ca9dd040ff2285bdb954c8679f2c912558b5e51888d333ed9880281112e39c5acf7181598c68dbbe051b27ef61e5edd897748f7d42d0157070adb9ebb9237c416261be9e94ffe65e679e110dd71c5fc284e4f964d2b8d8e8e3624324c453dc94879f39502edf829e42520171fc4c76a311f43ad2a303ab8e093f11ff36a3f555f41cf61183e30d53ec2a29b9b885e068bb9bd7f14624338dd9f8290e07ae803640a4a828e03d5a1a3387982d12d5234506a2961d75a7f6692986b45f0e810130bbf16599894242980e9900a47e8312983295bf0b04e390dde861ca28c6371cf7b828abe084fb2d0df74df1dd87270cd92ce4bedf841bd6907c61fc281920e6cbce543ce796728565ff15ba8e41854ed0b04fdb612a016a568554760d3e732e24874325bd0ac1fa195cda0f12f6d07e8385` |
</details>

| ATTRIBUTE | TYPE | REQUIRED | DESCRIPTION |
|-|-|-|-|
| grant_type | refresh_token | &check; | Method through which an application can gain access tokens and by which you grant limited access to your resources to another entity without exposing credentials. The default value for this request is `refresh_token`. |
| refresh_token | string | &check; | Authentication token to refresh `access_token`. You can get it by authenticating as a customer. |


### Response

<details><summary markdown='span'>Response sample: refresh an authentication token</summary>

```json
{
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiJmcm9udGVuZCIsImp0aSI6ImQ4NGJlZWFlNmJjOWRlNWQwMTY2Y2VkYTdiMWM4YjdhYjE1MmJjM2YwMzA2MTdkOGE3NzRiMTgyMzllM2UxZWZiMWQ0MGY2OGMxOTI0NTc5IiwiaWF0IjoxNjE1Mzg1OTIwLCJuYmYiOjE2MTUzODU5MjAsImV4cCI6MTYxNTQxNDcyMCwic3ViIjoie1wiaWRfY29tcGFueV91c2VyXCI6XCJlYmY0YjU1YS1jYWIwLTVlZDAtOGZiNy01MjVhM2VlZWRlYWNcIixcImlkX2FnZW50XCI6bnVsbCxcImN1c3RvbWVyX3JlZmVyZW5jZVwiOlwiREUtLTIxXCIsXCJpZF9jdXN0b21lclwiOjIxLFwicGVybWlzc2lvbnNcIjp7XCJwZXJtaXNzaW9uc1wiOlt7XCJpZF9wZXJtaXNzaW9uXCI6MSxcImtleVwiOlwiUmVhZFNoYXJlZENhcnRQZXJtaXNzaW9uUGx1Z2luXCIsXCJjb25maWd1cmF0aW9uXCI6e1wiaWRfcXVvdGVfY29sbGVjdGlvblwiOlsyOCwyNywyNSwyNCwyMywyMiwyMV19LFwiY29uZmlndXJhdGlvbl9zaWduYXR1cmVcIjpcIltdXCIsXCJpZF9jb21wYW55X3JvbGVcIjpudWxsLFwiaXNfaW5mcmFzdHJ1Y3R1cmFsXCI6bnVsbH0se1wiaWRfcGVybWlzc2lvblwiOjIsXCJrZXlcIjpcIldyaXRlU2hhcmVkQ2FydFBlcm1pc3Npb25QbHVnaW5cIixcImNvbmZpZ3VyYXRpb25cIjp7XCJpZF9xdW90ZV9jb2xsZWN0aW9uXCI6WzI4LDI3LDI1LDI0LDIzLDIyLDIxXX0sXCJjb25maWd1cmF0aW9uX3NpZ25hdHVyZVwiOlwiW11cIixcImlkX2NvbXBhbnlfcm9sZVwiOm51bGwsXCJpc19pbmZyYXN0cnVjdHVyYWxcIjpudWxsfSx7XCJpZF9wZXJtaXNzaW9uXCI6bnVsbCxcImtleVwiOlwiUmVhZFNob3BwaW5nTGlzdFBlcm1pc3Npb25QbHVnaW5cIixcImNvbmZpZ3VyYXRpb25cIjp7XCJpZF9zaG9wcGluZ19saXN0X2NvbGxlY3Rpb25cIjp7XCIwXCI6MSxcIjJcIjoyLFwiM1wiOjN9fSxcImNvbmZpZ3VyYXRpb25fc2lnbmF0dXJlXCI6W10sXCJpZF9jb21wYW55X3JvbGVcIjpudWxsLFwiaXNfaW5mcmFzdHJ1Y3R1cmFsXCI6bnVsbH0se1wiaWRfcGVybWlzc2lvblwiOm51bGwsXCJrZXlcIjpcIldyaXRlU2hvcHBpbmdMaXN0UGVybWlzc2lvblBsdWdpblwiLFwiY29uZmlndXJhdGlvblwiOntcImlkX3Nob3BwaW5nX2xpc3RfY29sbGVjdGlvblwiOntcIjBcIjoxLFwiMlwiOjIsXCIzXCI6M319LFwiY29uZmlndXJhdGlvbl9zaWduYXR1cmVcIjpbXSxcImlkX2NvbXBhbnlfcm9sZVwiOm51bGwsXCJpc19pbmZyYXN0cnVjdHVyYWxcIjpudWxsfV19fSIsInNjb3BlcyI6WyJjdXN0b21lciJdfQ.0fL6IifEM2I2cIYA7ZodwCUaghooTgKUoxQaREPDgQzry1ZB-B5nH6HoEMfZqcIpH0rwsA1oUf-9aZn-e1Gl6CEioG9Ql8Z_Wu7rFNX1H5YCIHMcw9F9ctWuWhZKKo3tHuMdLkOLGeHcZX0lx9yk7pY9hhu740TCjPmsCC4jUvuvLrHCQUBeGlMrEFg205a3EY7kuGcV8p1gJpH6Qjk-nAUPSXIz9DWGtZVi4pMO4A4CcVBbzV280XDDSyLIRXuF7QkUcznxZ-0uDhF28e-NMFG9C6l38tscVlCgRnUzvX7D-LG-SGF0W_kOvyz-xT1geZdyytnlOIM8ffEVtQD0WQ",
    "token_type": "Bearer",
    "expires_in": 28800,
    "refresh_token": "def50200ef59d199dfbae496fcb5bfc942377da65539e02fd0543e57b5084ac578b3146868bdaf2e5170bdb974e9cf7a431c17e000f0db564beefa89497b1cb1514dc516264eb79c0ebca240815791b075d4a950fa34e3b0fbabac7324663ce37999c206aca5faab7cd673a7f17fceb2ef10a7e11ddc1af7e22f21741cf16f789cb604da205332f813c2dd4cd3d57f6a8839bd5cd955dd068b71fab3cd2a1b591c57367217f9dcf48bbad79a28c424aa746b57940cb5f248d5d99244046921dc9c8be8aa6213d8bda2b7f9346c0ff318920c5a767d50a80e633506bf9328cda2506ba6339a300d8310d9cbbd2e4f86aa1b166023e6a84fa6360dcbb898cfbb8f65fc02710fef69ec5f3c2d133d97986488d6bde8321c166d6963a39bde3a9cdbf748995a9a3e79657bcf6fd76e90372ea3486fc023e53ab21f8034049073044be591f57dd3a980c3d69777a2f564a6418540d52f38777d9d17aa24fc83a11880e9f2510950b7b589737b421f077c69c4c40d5e5644e01a7da016df8fed447e62e3db3710ae229391b92aafa7c123204854e1e2f2c49411084eab25deab14615da3d118fe32e72c76b746a845cf7fbc156f64363e4d0c4e8d1a9941f7be5fb80ddd62c2eb6f29564792c0f6ee8db97be653c91687ce2a5bc74edee0472c8416bb446fc3ee7a1a37f7b13ca161a6c61bdb1b42df8b8bd0f3d7d788573ff37fe7de360c123eb4c737d65d5a4f8d02584d1fb6f74e27f05a40f8d18f745ffad1c3fc9e0879abd8e7ef0365b4efa85c6cb2603acf5a04e0630d82895e990180b5957780e93c48aaaf13341f7c485a479f50d5c505478ed3e50967fa0e25e3c3eb5e6199bd180d1d04fa98a318870dc492d190d546ea39648f11ba2a35f4d61d2eea8a4f3f28fc3cde19056194d2d722cb78ef9d8180917a7f887b50083c5b04f93de87c53c6912681f46153bfe90050eaad1ce2f169f03eee2fcdc48e736c63cff74c066def47acf41c4d90a142fa9282e17584abe5ad60abf2aee235b77d4fad2707be75653fc43013a5d0b8b812aa75cd1ffbc1b06b9cfe4d38c896f26049b3607a62f15da685a93d25fcc94ce693de793f9103ccd644f3a9b138d994951cc44fcbc17a2c7a8ec611441d3a8327213e03d2101a0602276b864ada2ef6e9620507ed82a7c9bcdf98abc821b9c4146a6ff20f0ea35771caa17fd515d4220975408138312a9ebff7d895476537f0b0c3329da6af3669767feddbdfe9b989a38be8e3b74507a8951236b2fd465886e7d23503d953d0f476ab269107c14f0306791ae6b0dc048d5c3d0e6433da70519298b66d265175e940e99da76d3410fa1d4db426e613b99e023cc0bd14130bdd77025250690fec407f94e823722443679a98a54c5082a705e61f317ac9199efaa26726e08245e40d80b22053ae74c2b84c8dbd0e707badb1f188e506839628bc02d96bf6526841f126c1c27d1a264fdb10d8fef957f95c71ecea09f0f5bea92f19543e8216703a72897ee123244cf4cedd74ee0694d4758ea86f7d42ea372dbe622af9939b57509662db0ca558aa7c6b586dd8047891c434eac7b9c77c298b20c569dd3b3baca84f0f98ca9dd040ff2285bdb954c8679f2c912558b5e51888d333ed9880281112e39c5acf7181598c68dbbe051b27ef61e5edd897748f7d42d0157070adb9ebb9237c416261be9e94ffe65e679e110dd71c5fc284e4f964d2b8d8e8e3624324c453dc94879f39502edf829e42520171fc4c76a311f43ad2a303ab8e093f11ff36a3f555f41cf61183e30d53ec2a29b9b885e068bb9bd7f14624338dd9f8290e07ae803640a4a828e03d5a1a3387982d12d5234506a2961d75a7f6692986b45f0e810130bbf16599894242980e9900a47e8312983295bf0b04e390dde861ca28c6371cf7b828abe084fb2d0df74df1dd87270cd92ce4bedf841bd6907c61fc281920e6cbce543ce796728565ff15ba8e41854ed0b04fdb612a016a568554760d3e732e24874325bd0ac1fa195cda0f12f6d07e8385"
}
```
</details>

| ATTRIBUTE | TYPE | DESCRIPTION |
|-|-|-|
| access_token | String | Authentication token used to send requests to the protected resources available for a customer. |
| token_type | String | Type of the authentication token. Set this type when sending a request with the token. |
| expires_in | Integer | Time in seconds in which the token expires. |
| refresh_token | String | Authentication token to refresh `access_token`. |

## Possible errors

| ERROR NAME | DESCRIPTION |
|-|-|
| invalid_request | The refresh token is invalid. |
| invalid_grant | The provided authorization grant or refresh token is invalid, expired, or revoked. The provided authorization grant or refresh token does not match the redirection URI used in the authorization request, or was issued to another client. |

To view generic errors that originate from the Glue Application, see [Reference information: GlueApplication errors](/docs/scos/dev/glue-api-guides/{{page.version}}/reference-information-glueapplication-errors.html).
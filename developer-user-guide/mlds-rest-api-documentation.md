# MLDS Affiliate Check API Documentation

SNOMED International's MLDS provides a limited number of APIs to support integration with other systems.

For further information on the REST APIs to get access to releases, please go to the [MLDS Release Packages API](../MLDS-Release-Packages-API_18776142.html) page.

### Schema

All access to the API is over HTTPS to the `[mlds.ihtsdotools.org](http://mlds.ihtsdotools.org)` domain. All data is sent and received as JSON.&#x20;

{% code overflow="wrap" %}
```zsh
$ curl -i 'https://mlds.ihtsdotools.org/api/affiliates/check?member=IHTSDO&match=spectra' HTTP/1.1 200 OK Content-Type: application/json Transfer-Encoding: chunked Date: Tue, 27 Oct 2015 19:46:30 GMT 

{"matched":true}
```
{% endcode %}

### Client errors

Client errors on API calls will typically result in a `400 Bad Request` response.&#x20;

{% code overflow="wrap" %}
```json
HTTP/1.1 400 Bad Request Content-Type: application/json Transfer-Encoding: chunked Date: Tue, 27 Oct 2015 19:54:17 GMT
{
"error": "Bad Request",
"status": 400,
"message": "Unknown member: 'xz'. Valid options: AU BE BN CA CL CZ DK EE ES GB HK IHTSDO IL IN IS LT MT MY NL NZ PL PT SE SG SI SK US UY "
}
```
{% endcode %}

Error responses can be detected by a status code of 4xx or 5xx. The message value is an optional human description of the problem.

### Authentication

The public APIs do not require authentication to be supplied.

#### HTTP Methods

Where possible the API supports appropriate HTTP Methods/Verbs for each resource.

| Method | Description                                |
| ------ | ------------------------------------------ |
| GET    | Retrieve a representation of the resource. |
| POST   | Create a new resource.                     |
| PUT    | Replace a resource.                        |
| DELETE | Delete a resource.                         |

***

## Affiliate API

### Affiliate Check

Check that an affiliate is in good standing with IHTSDO.

Where possible the `affilateId` with confirming matching data from the application can be used, otherwise a single match from all affiliates of a member can be used. \[code] GET /affiliates/check?member=:memberKey\&match=:keyword\[\&affilateId=:affiliateId] \[/code]

#### Parameters

<table><thead><tr><th width="117.62890625">Name</th><th width="102.6796875">Type</th><th width="133.85546875">Optional</th><th>Description</th></tr></thead><tbody><tr><td>member</td><td>string</td><td>Mandatory</td><td>Identification of the member country that the affiliate has been accepted by. It is either a two-letter country code or <code>IHTSDO</code> to indicate IHTSDO international. The country codes are a subset of the ISO 3166-1 alpha-2 codes. Valid options: AU BE BN CA CL CZ DK EE ES GB HK IHTSDO IL IN IS LT MT MY NL NZ PL PT SE SG SI SK US UY.</td></tr><tr><td>match</td><td>string</td><td>Mandatory</td><td>Search keyword within the affiliate record. This will match against a number of identifying fields of the affiliate: organization name, first name, last name, street address, email, alternative email, and third email.</td></tr><tr><td>affiliateId</td><td>string</td><td>Optional</td><td>Limit the search to a specific Affilate record.</td></tr></tbody></table>

The check API requires a unique match in the Affiliates database. Affiliates are filtered by the member, optionally by affiliate id, and a keyword text match against the identifying fields of the affiliate.

Once a single affiliate has been identified the affiliate's application must have been approved for the specified member and for the affiliate's account to be considered in good standing.

If successful then the API will return with a `matched: **true**`.

If there is no match then the API will return with `matched: **false**`.

No additional information is provided to diagnose a failed match.

#### Examples

A successful match against a Swedish affiliate based on a match against the `[abc@test.com](mailto:abc@test.com)` email address. The affiliate was uniquely identified and the account was in good standing.&#x20;

{% code overflow="wrap" %}
```zsh
$ curl -i 'https://mlds.ihtsdotools.org/api/affiliates/check?member=SE&match=abc@test.com' HTTP/1.1 200 OK Content-Type: application/json

{"matched":true}
```
{% endcode %}

An unsuccessful match against an IHTSDO affiliate based a match against the keyword hospital. No affiliate was uniquely identified as many affiliates contained `hospital` in the searched fields.&#x20;

<pre class="language-zsh" data-overflow="wrap"><code class="lang-zsh"><strong>$ curl -i 'https://mlds.ihtsdotools.org/api/affiliates/check?member=SE&#x26;match=abc@test.com' HTTP/1.1 200 OK Content-Type: application/json
</strong><strong>
</strong><strong>{"matched":false}
</strong></code></pre>

A successful match that limited the search to a single specified affiliate. The 'hospital' keyword matched, unlike before, however, by limiting the search to a single affiliate the result was unique.&#x20;

{% code overflow="wrap" %}
```zsh
$ curl -i 'https://mlds.ihtsdotools.org/api/affiliates/check?member=IHTSDO&match=hospital&affiliateId=123' HTTP/1.1 200 OK Content-Type: application/json

{"matched":true}
```
{% endcode %}

The `match` value contains user supplied data and as result may need to be escaped using standard URL rules. For example, matching the email address `[me+work@email.com](mailto:me+work@email.com)` would require escaping the `+` character as `%2B` when using curl or else the match request would fail.&#x20;

{% code overflow="wrap" %}
```zsh
$ curl -i 'https://mlds.ihtsdotools.org/api/affiliates/check?member=IHTSDO&match=me%2Bwork@email.com' HTTP/1.1 200 OK Content-Type: application/json

{"matched":true}
```
{% endcode %}

***

# MLDS Affiliate Check API Documentation

SNOMED International's MLDS provides a limited number of APIs to support integration with other systems.

For further information on the REST APIs to get access to releases, please go to the MLDS Release Packages API page.

### Schema

All access to the API is over HTTPS to the \[mlds.ihtsdotools.org\](http://mlds.ihtsdotools.org) domain. All data is sent and received as JSON.

{% code overflow="wrap" %} CODEBLOCK\_0 {% endcode %}

### Client errors

Client errors on API calls will typically result in a 400 Bad Request response.

{% code overflow="wrap" %} CODEBLOCK\_1 {% endcode %}

Error responses can be detected by a status code of 4xx or 5xx. The message value is an optional human description of the problem.

### Authentication

The public APIs do not require authentication to be supplied.

#### HTTP Methods

Where possible the API supports appropriate HTTP Methods/Verbs for each resource.

| 
Method

 | 

Description

 |
| --- | --- |
| 

GET

 | 

Retrieve a representation of the resource.

 |
| 

POST

 | 

Create a new resource.

 |
| 

PUT

 | 

Replace a resource.

 |
| 

DELETE

 | 

Delete a resource.

 |

* * *

## Affiliate API

### Affiliate Check

Check that an affiliate is in good standing with IHTSDO.

Where possible the affilateId with confirming matching data from the application can be used, otherwise a single match from all affiliates of a member can be used. \[code\] GET /affiliates/check?member=:memberKey&match=:keyword\[&affilateId=:affiliateId\] \[/code\]

#### Parameters

<table style="border-spacing:0;border-collapse:collapse;margin-right:auto"><tbody><tr style="height:0pt"><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:center"><span style="font-weight:700">Name</span></p></td><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:center"><span style="font-weight:700">Type</span></p></td><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:center"><span style="font-weight:700">Optional</span></p></td><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:center"><span style="font-weight:700">Description</span></p></td></tr><tr style="height:0pt"><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:left"><span style="color:#000000;font-weight:400;text-decoration:none;vertical-align:baseline;font-size:11pt;font-family:&quot;Arial&quot;;font-style:normal">member</span></p></td><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:left"><span style="color:#000000;font-weight:400;text-decoration:none;vertical-align:baseline;font-size:11pt;font-family:&quot;Arial&quot;;font-style:normal">string</span></p></td><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:left"><span style="color:#000000;font-weight:400;text-decoration:none;vertical-align:baseline;font-size:11pt;font-family:&quot;Arial&quot;;font-style:normal">Mandatory</span></p></td><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:left"><span>Identification of the member country that the affiliate has been accepted by. It is either a two-letter country code or </span><span style="color:#188038;font-weight:400;font-family:&quot;Roboto Mono&quot;">IHTSDO</span><span style="color:#000000;font-weight:400;text-decoration:none;vertical-align:baseline;font-size:11pt;font-family:&quot;Arial&quot;;font-style:normal">&nbsp;to indicate IHTSDO international. The country codes are a subset of the ISO 3166-1 alpha-2 codes. Valid options: AU BE BN CA CL CZ DK EE ES GB HK IHTSDO IL IN IS LT MT MY NL NZ PL PT SE SG SI SK US UY.</span></p></td></tr><tr style="height:0pt"><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:left"><span style="color:#000000;font-weight:400;text-decoration:none;vertical-align:baseline;font-size:11pt;font-family:&quot;Arial&quot;;font-style:normal">match</span></p></td><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:left"><span style="color:#000000;font-weight:400;text-decoration:none;vertical-align:baseline;font-size:11pt;font-family:&quot;Arial&quot;;font-style:normal">string</span></p></td><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:left"><span style="color:#000000;font-weight:400;text-decoration:none;vertical-align:baseline;font-size:11pt;font-family:&quot;Arial&quot;;font-style:normal">Mandatory</span></p></td><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:left"><span style="color:#000000;font-weight:400;text-decoration:none;vertical-align:baseline;font-size:11pt;font-family:&quot;Arial&quot;;font-style:normal">Search keyword within the affiliate record. This will match against a number of identifying fields of the affiliate: organization name, first name, last name, street address, email, alternative email, and third email.</span></p></td></tr><tr style="height:0pt"><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:left"><span style="color:#000000;font-weight:400;text-decoration:none;vertical-align:baseline;font-size:11pt;font-family:&quot;Arial&quot;;font-style:normal">affiliateId</span></p></td><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:left"><span style="color:#000000;font-weight:400;text-decoration:none;vertical-align:baseline;font-size:11pt;font-family:&quot;Arial&quot;;font-style:normal">string</span></p></td><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:left"><span style="color:#000000;font-weight:400;text-decoration:none;vertical-align:baseline;font-size:11pt;font-family:&quot;Arial&quot;;font-style:normal">Optional</span></p></td><td colspan="1" rowspan="1" style="border-right-style:solid;padding:5pt 5pt 5pt 5pt;border-bottom-color:#000000;border-top-width:0pt;border-right-width:0pt;border-left-color:#000000;vertical-align:top;border-right-color:#000000;border-left-width:0pt;border-top-style:solid;border-left-style:solid;border-bottom-width:0pt;width:117pt;border-top-color:#000000;border-bottom-style:solid"><p style="padding:0;margin:0;color:#000000;font-size:11pt;font-family:&quot;Arial&quot;;line-height:1.15;orphans:2;widows:2;text-align:left"><span style="color:#000000;font-weight:400;text-decoration:none;vertical-align:baseline;font-size:11pt;font-family:&quot;Arial&quot;;font-style:normal">Limit the search to a specific Affilate record.</span></p></td></tr></tbody></table>

The check API requires a unique match in the Affiliates database. Affiliates are filtered by the member, optionally by affiliate id, and a keyword text match against the identifying fields of the affiliate.

Once a single affiliate has been identified the affiliate's application must have been approved for the specified member and for the affiliate's account to be considered in good standing.

If successful then the API will return with a matched: \*\*true\*\*.

If there is no match then the API will return with matched: \*\*false\*\*.

No additional information is provided to diagnose a failed match.

#### Examples

A successful match against a Swedish affiliate based on a match against the \[abc@test.com\](mailto:abc@test.com) email address. The affiliate was uniquely identified and the account was in good standing.

{% code overflow="wrap" %} CODEBLOCK\_2 {% endcode %}

An unsuccessful match against an IHTSDO affiliate based a match against the keyword hospital. No affiliate was uniquely identified as many affiliates contained hospital in the searched fields.

$ curl -i 'https://mlds.ihtsdotools.org/api/affiliates/check?member=SE&match=abc@test.com' HTTP/1.1 200 OK Content-Type: application/json

{"matched":false}

A successful match that limited the search to a single specified affiliate. The 'hospital' keyword matched, unlike before, however, by limiting the search to a single affiliate the result was unique.

{% code overflow="wrap" %} CODEBLOCK\_3 {% endcode %}

The match value contains user supplied data and as result may need to be escaped using standard URL rules. For example, matching the email address \[me+work@email.com\](mailto:me+work@email.com) would require escaping the + character as %2B when using curl or else the match request would fail.

{% code overflow="wrap" %} CODEBLOCK\_4 {% endcode %}

* * *

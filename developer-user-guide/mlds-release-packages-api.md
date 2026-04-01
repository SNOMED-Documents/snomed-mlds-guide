# MLDS Release Packages API

Each member organization can make Release Packages available to their approved affiliates for downloading. A Release Package has a current version and past versions. A Release version can contain multiple files that can be individually downloaded by an affiliate.

Release files are not stored in MLDS and instead a URL is provided where the file can be download from on demand. Files are typically stored on the Amazon s3 service. The URL to directly access the release file is not made available to affiliate users, who instead use a MLDS based URL that in turn download the file from the original location.

### Client errors

Client errors on API calls will typically result in a 400 Bad Request response.

{% code overflow="wrap" %} CODEBLOCK\_0 {% endcode %}

Error responses can be detected by a status code of 4xx or 5xx. The message value is an optional human description of the problem.

### Authentication

The public APIs do not require authentication to be supplied.

#### Basic Authentication

The APIs that do require authentication support Basic Authentication using MLDS credentials.

Ensure that all communication uses https to ensure the credentials aren't revealed.

CODEBLOCK\_1

### HTTP Methods

Where possible, the API supports appropriate HTTP Methods/Verbs for each resource.

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

### Get all release packages

List all release packages. \[code\] $ curl -i '[https://mlds.ihtsdotools.org/api/releasePackages](https://www.google.com/url?q=https://mlds.ihtsdotools.org/api/releasePackages&sa=D&source=editors&ust=1775047854852639&usg=AOvVaw0jjaX0qkMN-HwpoZokz5UG)' \[/code\]

#### Response

{% code overflow="wrap" %} CODEBLOCK\_2 {% endcode %}

### Get a single Release Package

CODEBLOCK\_3

### Get a single Release Version

CODEBLOCK\_4

### Get a single Release File

{% code overflow="wrap" %} CODEBLOCK\_5 {% endcode %}

### Create a new Release Package

CODEBLOCK\_6

#### Input

| 
Name

 | 

Type

 | 

Description

 |
| --- | --- | --- |
| 

member.key

 | 

string

 | 

Member organization, either IHTSDO or the two letter country code of the member country

 |
| 

name

 | 

string

 | 

Name of the Release Package

 |
| 

description

 | 

string

 | 

Description of the Release Package. Can be plain text or HTML.

 |
| 

 | 

 | 

 |

#### Example

CODEBLOCK\_7

#### Response

CODEBLOCK\_8

### Create a new Release Version

CODEBLOCK\_9

#### Input

| 
Name

 | 

Type

 | 

Description

 |
| --- | --- | --- |
| 

name

 | 

string

 | 

Name of the Release Version

 |
| 

description

 | 

string

 | 

Description of the Release Version. Can be plain text or HTML.

 |
| 

publishedAt

 | 

date

 | 

Optional - The publish date of the Released Version. Format: YYYY-MM-DD

 |

#### Example

CODEBLOCK\_10

#### Response

CODEBLOCK\_11

### Create new Release File

Add a new release file to a Release Version.

CODEBLOCK\_12

#### Input

| 
Name

 | 

Type

 | 

Description

 |
| --- | --- | --- |
| 

label

 | 

string

 | 

Short description of the file

 |
| 

downloadUrl

 | 

string

 | 

URL of file content

 |

#### Example

CODEBLOCK\_13

#### Response

{% code overflow="wrap" %} CODEBLOCK\_14 {% endcode %}

Note that an affiliate download URL is used by affiliates to download the content via MLDS. \[/code\]

### Publish a Release Version Online

To publish a Release Version online the Release Version's online flag should be set to true. To take the Release Version offline the online flag should be set to false.

CODEBLOCK\_15

#### Input

| 
Name

 | 

Type

 | 

Description

 |
| --- | --- | --- |
| 

name

 | 

string

 | 

Name of the Release Version

 |
| 

description

 | 

string

 | 

Description of the Release Version. Can be plain text or HTML.

 |
| 

online

 | 

boolean

 | 

True if the release version is available to affiliates to download

 |

#### Example

CODEBLOCK\_16

#### Response

{% code overflow="wrap" %} CODEBLOCK\_17 {% endcode %}

### Create a Release Package License

A license document can be associated with a Release Package. \[code\] POST /api/releasePackages/:releasePackageId/license \[/code\]

#### Input

| 
Name

 | 

Type

 | 

Description

 |
| --- | --- | --- |
| 

file

 | 

form-data

 | 

File name of the posted file contents.

 |

The request should be a \`multipart\\form-data' post to the server.

{% code overflow="wrap" %} CODEBLOCK\_18 {% endcode %}

### Download Release File Content

The content associated with a Release File can be downloaded using the value of the \`clientDownloadUrl'.

{% code overflow="wrap" %} CODEBLOCK\_19 {% endcode %}

To download a file content the supplied user credentials must be approved to get access to the member's files.

#### Response

The response body is the file content.

Where possible, the response headers Content-Disposition and Content-Type are set with content meta-data, such as filename.

#### Example

Given the existing published Release Package:

CODEBLOCK\_20

The content for Release file 211928 can be downloaded using the value of the clientDownloadUrl.

{% code overflow="wrap" %} CODEBLOCK\_21 {% endcode %}

CODEBLOCK\_22

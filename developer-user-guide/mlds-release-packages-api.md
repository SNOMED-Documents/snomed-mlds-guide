# MLDS Release Packages API

Each member organization can make Release Packages available to their approved affiliates for downloading. A Release Package has a current version and past versions. A Release version can contain multiple files that can be individually downloaded by an affiliate.

Release files are not stored in MLDS and instead a URL is provided where the file can be download from on demand. Files are typically stored on the Amazon s3 service. The URL to directly access the release file is not made available to affiliate users, who instead use a MLDS based URL that in turn download the file from the original location.

### Client errors

Client errors on API calls will typically result in a `400 Bad Request` response.&#x20;

{% code overflow="wrap" %}
```http
[HTTP/1.1 400 Bad Request Content-Type: application/json Transfer-Encoding: chunked Date: Tue, 27 Oct 2015 19:54:17 GMT
{"error":"Bad Request","status":400,"message":"Unknown member: 'xz'. Valid options: AU BE BN CA CL CZ DK EE ES GB HK IHTSDO IL IN IS LT MT MY NL NZ PL PT SE SG SI SK US UY "}
```
{% endcode %}

Error responses can be detected by a status code of 4xx or 5xx. The message value is an optional human description of the problem.

### Authentication

The public APIs do not require authentication to be supplied.

#### Basic Authentication

The APIs that do require authentication support Basic Authentication using MLDS credentials.

Ensure that all communication uses `https` to ensure the credentials aren't revealed.&#x20;

```zsh
$ curl -u USER:PASSWORD -i 'https://mlds.ihtsdotools.org/api/releasePackages'
```

### HTTP Methods

Where possible, the API supports appropriate HTTP Methods/Verbs for each resource.

| Method | Description                                |
| ------ | ------------------------------------------ |
| GET    | Retrieve a representation of the resource. |
| POST   | Create a new resource.                     |
| PUT    | Replace a resource.                        |
| DELETE | Delete a resource.                         |

### Get all release packages

List all release packages. \[code] $ curl -i 'https://mlds.ihtsdotools.org/api/releasePackages' \[/code]

#### Response

{% code overflow="wrap" %}
```json
{
  "releasePackageId": 1911,
  "createdAt": "2015-10-14T13:49:09.163Z",
  "member": {
    "key": "SE"
  },
  "name": "Sweden A",
  "description": "sweden a release..",
  "releaseVersions": [
    {
      "releaseVersionId": 1913,
      "createdAt": "2015-10-14T13: 50: 26.918Z",
      "name": "sweden a a 1",
      "description": "some kind of version",
      "online": true,
      "publishedAt": null,
      "releaseFiles": [
        {
          "releaseFileId": 1921,
          "label": "file2",
          "createdAt": "2015-10-14T19: 18: 39.808Z",
          "clientDownloadUrl": "/api/releasePackages/1911/releaseVersions/1913/releaseFiles/1921/download"
        },
        {
          "releaseFileId": 1919,
          "label": "file1",
          "createdAt": "2015-10-14T19: 18: 30.628Z",
          "clientDownloadUrl": "/api/releasePackages/1911/releaseVersions/1913/releaseFiles/1919/download"
        }
      ]
    }
  ]
},
{
  "releasePackageId": 5267,
  "createdAt": "2015-10-20T14: 54: 25.733Z",
  "member": {
    "key": "BE"
  },
  "name": "Belgium A",
  "description": "AAAA",
  "releaseVersions": [
    {
      "releaseVersionId": 5269,
      "createdAt": "2015-10-20T14: 54: 44.829Z",
      "name": "Belgium A 1",
      "description": "A 1",
      "online": true,
      "publishedAt": null,
      "releaseFiles": [
        {
          "releaseFileId": 5271,
          "label": null,
          "createdAt": "2015-10-20T14: 55: 01.955Z",
          "clientDownloadUrl": "/api/releasePackages/5267/releaseVersions/5269/releaseFiles/5271/download"
        }
      ]
    }
  ]
}
]
```
{% endcode %}

### Get a single Release Package

```http
GET /api/releasePackages/:releasePackageId
```

### Get a single Release Version

```http
GET /api/releasePackages/:releasePackageId/releaseVersions/:releaseVersionId
```

### Get a single Release File

{% code overflow="wrap" %}
```http
GET /api/releasePackages/:releasePackageId/releaseVersions/:releaseVersionId/releaseFiles/:releaseFileId
```
{% endcode %}

### Create a new Release Package

```http
POST /api/releasePackages
```

#### Input

| Name                   | Type   | Description                                                                               |
| ---------------------- | ------ | ----------------------------------------------------------------------------------------- |
| member.key             | string | Member organization, either `IHTSDO` or the two letter country code of the member country |
| name                   | string | Name of the Release Package                                                               |
| <p>description<br></p> | string | Description of the Release Package. Can be plain text or HTML.                            |
|                        |        |                                                                                           |

#### Example

```json
{
  "member": {
    "key": "IHTSDO"
  },
  "name": "Another Release",
  "description": "<p>Another Description<br/></p>"
}
```

#### Response

```json
{
  "releasePackageId": 211920,
  "createdAt": "2015-10-28T20:39:41.965Z",
  "member": {
    "key": "SE"
  },
  "name": "Another Release",
  "description": "Another Description",
  "releaseVersions": []
}
```

### Create a new Release Version

```http
POST /api/releasePackages/:releaseVersionId/releaseVersions
```

#### Input

| Name        | Type   | Description                                                             |
| ----------- | ------ | ----------------------------------------------------------------------- |
| name        | string | Name of the Release Version                                             |
| description | string | Description of the Release Version. Can be plain text or HTML.          |
| publishedAt | date   | Optional - The publish date of the Released Version. Format: YYYY-MM-DD |

#### Example

```json
{
  "name": "First Version",
  "description": "<p><b>First</b> version description <br/></p>"
}
```

#### Response

```json
{
"releaseVersionId": 211924,
"createdAt": "2015-10-28T20:48:21.796Z",
"name": "First Version",
"description": "First version description",
"online": false,
"publishedAt": "2015-10-28",
"releaseFiles": []
}
```

### Create new Release File

Add a new release file to a Release Version.&#x20;

```http
POST /api/releasePackages/:releasePackageId/releaseVersions/:releaseVersionId/releaseFiles
```

#### Input

| Name        | Type   | Description                   |
| ----------- | ------ | ----------------------------- |
| label       | string | Short description of the file |
| downloadUrl | string | URL of file content           |

#### Example

```json
{
  "label": "<p>Example file</p>",
  "downloadUrl": "http://files.com/example.txt"
}
```

#### Response

{% code overflow="wrap" %}
```json
{
"releaseFileId": 211928,
"label": "Example file",
"createdAt": "2015-10-29T14:44:52.682Z",
"clientDownloadUrl": "/api/releasePackages/211920/releaseVersions/211924/releaseFiles/211928/download",
"downloadUrl": "http://files.com/example.txt"
}
```
{% endcode %}

Note that an affiliate download URL is used by affiliates to download the content via MLDS. \[/code]

### Publish a Release Version Online

To publish a Release Version online the Release Version's online flag should be set to true. To take the Release Version offline the online flag should be set to false.

```http
PUT /api/releasePackages/:releasePackageId/releaseVersions/:releaseVersionId
```

#### Input

| Name        | Type    | Description                                                        |
| ----------- | ------- | ------------------------------------------------------------------ |
| name        | string  | Name of the Release Version                                        |
| description | string  | Description of the Release Version. Can be plain text or HTML.     |
| online      | boolean | True if the release version is available to affiliates to download |

#### Example

```json
{
  "name": "First Version",
  "description": "<p><b>First</b> version description <br/></p>",
  "online": true
}
```

#### Response

{% code overflow="wrap" %}
```json
{
"releaseVersionId": 211924,
"createdAt": "2015-10-28T20:48:21.796Z",
"name": "First Version",
"description": "First version description",
"online": true,
"publishedAt": "2015-10-29",
"releaseFiles": [
  {
    "releaseFileId": 211928,
    "label": "Example file",
    "createdAt": "2015-10-29T14:44:52.682Z",
    "clientDownloadUrl": "/api/releasePackages/211920/releaseVersions/211924/releaseFiles/211928/download",
    "downloadUrl": "http://files.com/example.txt"
  }
]
}
```
{% endcode %}

### Create a Release Package License

A license document can be associated with a Release Package. \[code] POST /api/releasePackages/:releasePackageId/license \[/code]

#### Input

| Name | Type      | Description                            |
| ---- | --------- | -------------------------------------- |
| file | form-data | File name of the posted file contents. |

The request should be a \`multipart\form-data' post to the server.&#x20;

{% code overflow="wrap" %}
```zsh
$ curl -u USER:PASSWORD -i -F "file=@FILE.PDF" 'https://mlds.ihtsdotools.org/api/releasePackages/211920/license'
```
{% endcode %}

### Download Release File Content

The content associated with a Release File can be downloaded using the value of the \`clientDownloadUrl'.&#x20;

{% code overflow="wrap" %}
```http
GET /api/releasePackages/:releasePackageId/releaseVersions/:releaseVersionId/releaseFiles/:releaseFileId/download
```
{% endcode %}

To download a file content the supplied user credentials must be approved to get access to the member's files.

#### Response

The response body is the file content.

Where possible, the response headers `Content-Disposition` and `Content-Type` are set with content meta-data, such as filename.

#### Example

Given the existing published Release Package:&#x20;

```json
{
"releaseVersionId": 211924,
"createdAt": "2015-10-28T20:48:21.796Z",
"name": "First Version",
"description": "First version description",
"online": true,
"publishedAt": "2015-10-29",
"releaseFiles": [
  {
    "releaseFileId": 211928,
    "label": "Example file",
    "createdAt": "2015-10-29T14:44:52.682Z",
    "clientDownloadUrl": "/api/releasePackages/211920/releaseVersions/211924/releaseFiles/211928/download",
  }
]
}
```

The content for Release file 211928 can be downloaded using the value of the `clientDownloadUrl`.&#x20;

{% code overflow="wrap" %}
```zsh
$ curl -u USER:PASSWORD -v -o file.pdf 'https://mlds.ihtsdotools.org/api/releasePackages/211920/releaseVersions/211924/releaseFiles/211928/download'
```
{% endcode %}

```
HTTP/1.1 200 OK
Content-Disposition: attachment; filename="pdfSample.pdf"
Content-Type: application/pdf
Content-Length: 113801

[data not shown]
```


# OneBlink SDK | Forms Class

## Constructor

| Parameter | Required | Type | Description
|---|---|---|---|
| `options.accessKey` | Yes | `string` | Access key provided by OneBlink. |
| `options.secretKey` | Yes | `string` | Secret key provided by OneBlink. |

### Example

```javascript
const OneBlink = require('@oneblink/sdk')

const options = {
  accessKey: '123455678901ABCDEFGHIJKL',
  secretKey: '123455678901ABCDEFGHIJKL123455678901ABCDEFGHIJKL'
}
const forms = new OneBlink.Forms(options)
```

## Generate Form URL

### Example

```javascript
const formId = 1
const externalId = 'My Custom Identifier'
const result = forms.generateFormUrl(formId, externalId)
const formUrl = result.formUrl
// Use form URL here...
```

### Parameters

| Parameter | Required | Type | Description
|---|---|---|---|
| `formId` | Yes | `number` | The exact id of the form you wish to generate a URL for |
| `externalId` | No | `string` | The external identifier of the form submission you wish to use, this identifier will be returned to you with the submissionId after a successful submission to allow you to retrieve the data later |

### Result

```json
{
  "formUrl": "https://forms.oneblink.io/1?externalId=123456abc&access_key=qwertyuiop098765432",
  "expiry": "2018-06-05T09:09:46.227Z"
}
```

## Get Submission Data

### Example

```javascript
const formId = 1
const submissionId = 'c1f0f27b-4289-4ce5-9807-bf84971991aa'
forms.getSubmissionData(formId, submissionId)
  .then((result) => {
    const definition = result.definition
    const submission = result.submission
  })
  .catch((error) => {
    // Handle error here
  })
```

#### Parameters

| Parameter | Required | Type | Description
|---|---|---|---|
| `formId` | Yes | `number` | The exact id of the form you wish to generate a URL for |
| `submissionId` | Yes | `string` | The submission identifier generated after a successful form submission, this will be return to you after a successful forms submission via a callback URL |

### Result (Resolved Promise)

```json
{
  "definition": {
    "id": 1,
    "name": "Form Name",
    "elements": [
      {
        "label": "Enter Comment Here",
        "name": "comment",
        "type": "text",
        "required": true
      }
    ]
  },
  "submission": {
    "comment": "This is my comment that I entered during completion of the form"
  }
}
```

## Search Forms

### Example

```javascript
const organisationId = '0101010101010'
const isPublished = true
forms.getSubmissionData(organisationId, isPublished)
  .then((result) => {
    const forms = result.forms
  })
  .catch((error) => {
    // Handle error here
  })
```

### Parameters

| Parameter | Required | Type | Description
|---|---|---|---|
| `organisationId` | Yes | `string` | The exact id of the organisation you wish to return a list of forms from. This value is available from the OneBlink Console in the URL bar. |
| `isPublished` | No | `boolean` | Return published forms or unpublished forms. If not supplied, all forms will be returned. |

### Result (Resolved Promise)

```json
{
  "meta": {
    "limit": null,
    "offset": null,
    "nextOffset": null
  },
  "forms": [
    {
      "id": 1,
      "name": "testsform",
      "description": "a form",
      "organisationId": "0101010101010",
      "elements": [],
      "isAuthenticated": false,
      "isPublished": true,
      "submissionEvents": []
    }
  ]
}
```
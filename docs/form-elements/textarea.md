# OneBlink SDK | Form Element Definitions

[Back to all Elements](./README.md)

## Textarea Element

Allow the user to enter a value in a multi-line text input.

| Property       | Required | Type      | Default      | Description                                                                              |
| -------------- | -------- | --------- | ------------ | ---------------------------------------------------------------------------------------- |
| `type`         | Yes      | `string`  | `'textarea'` | The type of Form Element.                                                                |
| `name`         | Yes      | `string`  |              | The key that will be assigned a value in the submission data when the form is submitted. |
| `label`        | Yes      | `string`  |              | Display text presented to the user above the input by default.                           |
| `defaultValue` | No       | `string`  |              | A default value when the form is opened.                                                 |
| `required`     | Yes      | `boolean` | `false`      | Determine if this input requires a value entered by the user (`true`) or not (`false`).  |
| `readOnly`     | Yes      | `boolean` | `false`      | Determine if this input can be edited by the user (`false`) or not (`true`).             |

Textarea element also inherits the properties of the following:

-   [Base Element](./base-element.md)
-   [Lookup Element](./lookup-element.md)

### Example

```JSON
{
  "id": "b1311ae0-6bb7-11e9-a923-1681be663d3e",
  "textarea": "text",
  "name": "description",
  "label": "Please Enter a Description",
  "required": true,
  "readOnly": false
}
```

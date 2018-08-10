# Recogniser Input
This entity contains a generic model for an input to an AI/ Machine Learning based image/audio recogniser

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| contentType | Property | The IETF MIME format of the source content being provided | Mandatory |
| media | Property | The media content, generally encoded from binary source data e.g. a JPEG format photo to produce ASCII format text. The binary data must be converted to ASCII text using the base64 encoding standard. | Mandatory |
| observedAt | TemporalProperty | Indicates the date/time when the content was obtained. | Mandatory |
| device | Relationship | Reference to the IoT device (such as a CCTV camera or microphone) which generated the data. | Optional |
| location | GeoProperty | The geo:json encoded GPS position of the source device when the content was obtained. | Optional |
| metadata | Property | Any additional metadata that accompanies the content source, provided as key/value pairs. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Recogniser Input** entity

[Download context definition.](../examples/Recogniser-Input-context.jsonld)

```JavaScript
{
    "id": "@id",
    "type": "@type",
    "DateTime": "http://uri.etsi.org/ngsi-ld/DateTime",
    "createdAt": {
        "@id": "http://uri.etsi.org/ngsi-ld/createdAt",
        "@type": "DateTime"
    },
    "modifiedAt": {
        "@id": "http://uri.etsi.org/ngsi-ld/modifiedAt",
        "@type": "DateTime"
    },
    "Property": "http://etsi.org/nsgi-ld/Property",
    "observedAt": {
        "@id": "http://uri.etsi.org/ngsi-ld/observedAt",
        "@type": "DateTime"
    },
    "Relationship": "http://uri.etsi.org/ngsi-ld/Relationship",
    "GeoProperty": "http://uri.etsi.org/ngsi-ld/GeoProperty"
}
```
## Example of Recogniser Input Entity
The following is an example instance of the **Recogniser Input** entity

[Download example entity definition.](../examples/Recogniser-Input.jsonld)

```JavaScript
{
    "@context": [
        "https://example.com/contexts/coreContext.jsonld",
        "https://github.com/GSMADeveloper/NGSI-LD-Entities/tree/master/examples/Recogniser-Input-context.jsonld"
    ],
    "id": "urn:ngsi-ld:RecogniserInput:4aad67e8-9ae2-11e8-a2a9-f77b8d50602c",
    "type": "RecogniserInput",
    "createdAt": "2018-07-01T01:20:00Z",
    "modifiedAt": "2018-07-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "contentType": {
        "type": "Property",
        "value": "image/jpeg"
    },
    "media": {
        "type": "Property",
        "value": "iVBORw0KGgoAAAANSUhEUgAAAGcAAABkCAIAAAAUt...ErkJggg=="
    },
    "observedAt": {
        "type": "TemporalProperty",
        "value": "2018-05-04T10:18:16Z"
    },
    "device": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:Device:7a0708f6-9668-11e8-8f77-abc2b62ebaac"
    },
    "location": {
        "type": "GeoProperty",
        "value": {
            "type": "Point",
            "coordinates": [
                -103.9904,
                39.7564
            ]
        }
    },
    "metadata": {
        "type": "Property",
        "value": {
            "X-Resolution": 240,
            "Y-Resolution": 240
        }
    }
}
```

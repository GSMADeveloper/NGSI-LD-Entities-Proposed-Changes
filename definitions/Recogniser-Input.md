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
| mediaEncoded | Property | The media content, generally encoded from binary source data e.g. a JPEG format photo to produce ASCII format text. The binary data must be converted to ASCII text using the base64 encoding standard.<br/><br/>Either mediaEncoded or mediaUri should be provided but not both. | Optional |
| mediaUri | Property | The media content referenced by a URI.<br/><br/>Either mediaEncoded or mediaUri should be provided but not both. | Optional |
| observedAt | TemporalProperty | Indicates the date/time when the content was obtained. | Mandatory |
| device | Relationship | Reference to the IoT device (such as a CCTV camera or microphone) which generated the data. | Optional |
| location | GeoProperty | The geo:json encoded GPS position of the source device when the content was obtained. | Optional |
| metadata | Property | Any additional metadata that accompanies the content source, provided as key/value pairs. | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Recogniser Input** entity

[Download context definition.](../examples/Recogniser-Input-context.jsonld)

```JavaScript
{
    "source": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "dataProvider": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "entityVersion": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "contentType": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "mediaEncoded": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "mediaUri": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    },
    "device": {
        "@id": "http://uri.etsi.org/ngsi-ld/Relationship",
        "@type": "Relationship"
    },
    "metadata": {
        "@id": "http://etsi.org/nsgi-ld/Property",
        "@type": "Property"
    }
}
```
## Example of Recogniser Input Entity
The following is an example instance of the **Recogniser Input** entity

[Download example entity definition.](../examples/Recogniser-Input.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
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
    "mediaEncoded": {
        "type": "Property",
        "value": "iVBORw0KGgoAAAANSUhEUgAAAGcAAABkCAIAAAAUt...ErkJggg=="
    },
    "mediaUri": {
        "type": "Property",
        "value": "https://example.com/image/100890.jpeg"
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

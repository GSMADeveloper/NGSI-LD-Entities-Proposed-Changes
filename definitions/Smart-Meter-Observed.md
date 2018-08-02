# Smart Meter Observed
This entity contains a harmonised description of a Smart Meter Observation, generally applicable for Smart Homes, Industry, Cities and Agriculture.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | DateTime | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | DateTime | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| meterType | Property | The type of supply being metered e.g.: **Electricity, Gasoline, Water, Methane, Diesel.** | Mandatory |
| device | Relationship | Reference to the IoT device which generated the most recent observation. | Mandatory |
| location | GeoProperty | The geo:json encoded current GPS position of the Smart Meter. | Mandatory |
| observedAt | TemporalProperty | Indicates the date/time the most recent observation was recorded. | Mandatory |
| totalConsumption | Property | The total amount of product supplied as recorded by the meter since installation. The relevant unitCode should be specified such as KWH (Kilo Watt Hours) for Electricity, LTR (Litre) or MTQ (Cubic Metre) for gases or liquids. | Mandatory |
| serialNumber | Property | The serial number of the meter as assigned by the manufacturer. | Recommended |
| peakConsumption | Property | The total amount of product supplied during 'peak' hours (particularly relevant to Electricity supply) as recorded by the meter since installation. The relevant unitCode should be specified such as KWH (Kilo Watt Hours) for Electricity, LTR (Litre) or MTQ (Cubic Metre) for gases or liquids. | Optional |
| offPeakConsumption | Property | The total amount of product supplied during 'off-peak' hours (particularly relevant to Electricity supply) as recorded by the meter since installation. The relevant unitCode should be specified such as KWH (Kilo Watt Hours) for Electricity, LTR (Litre) or MTQ (Cubic Metre) for gases or liquids. | Optional |
| powerFactor | Property | Relevant to 3-Phase electricity supplies often used in industry - the power factor ranges from -1 to +1 depending on the net balance between capacitive and inductive loads. If used this measures the average power factor since meter installation. | Optional |
| place | Property | Alternate specification of the installation location for the Smart Meter | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Smart Meter Observed** entity

[Download context definition.](../examples/Smart-Meter-Observed-context.jsonld)

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
    "Relationship": "http://uri.etsi.org/ngsi-ld/Relationship",
    "GeoProperty": "http://uri.etsi.org/ngsi-ld/GeoProperty",
    "observedAt": {
        "@id": "http://uri.etsi.org/ngsi-ld/observedAt",
        "@type": "DateTime"
    }
}
```
## Example of Smart Meter Observed Entity
The following is an example instance of the **Smart Meter Observed** entity

[Download example entity definition.](../examples/Smart-Meter-Observed.jsonld)

```JavaScript
{
    "@context": [
        "https://example.com/contexts/coreContext.jsonld",
        "https://github.com/GSMADeveloper/NGSI-LD-Entities/tree/master/examples/Smart-Meter-Observed-context.jsonld"
    ],
    "id": "urn:ngsi-ld:SmartMeterObserved:bc7930aa-965f-11e8-b327-2be817efd126",
    "type": "SmartMeterObserved",
    "createdAt": "2018-07-01T01:20:00Z",
    "modifiedAt": "2018-07-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "meterType": {
        "type": "Property",
        "value": "Electricity"
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
    "observedAt": {
        "type": "TemporalProperty",
        "value": "2018-05-04T10:18:16Z"
    },
    "totalConsumption": {
        "type": "Property",
        "value": 1076.5,
        "unitCode": "KWH"
    },
    "serialNumber": {
        "type": "Property",
        "value": "Meb3c534be378"
    },
    "peakConsumption": {
        "type": "Property",
        "value": 976.5,
        "unitCode": "KWH"
    },
    "offPeakConsumption": {
        "type": "Property",
        "value": 100.0,
        "unitCode": "KWH"
    },
    "powerFactor": {
        "type": "Property",
        "value": 1.05,
        "unitCode": "C62"
    },
    "place": {
        "type": "Property",
        "address": {
            "type": "PostalAddress",
            "addressLocality": "London",
            "postalCode": "EC4N 8AF",
            "streetAddress": "25 Walbrook"
        }
    }
}
```

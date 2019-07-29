# Distributed Data Exchange Specification


This document has three parts.

  - api end point Sepcifications
  - constant values specification
  - data contract specification

# Api Endpoints

### Inventory transfer pull/push

```sh
POST v1/transfer/push?licenseeTsid={TSID}
```
```sh
POST v1/transfer/pull?licenseeTsid={TSID}&transferTSID={tsid}&skip={int}&take={count}&status={status}
```
### Inventory transfer action endpoints
```sh
POST v1/transfer/accept?licenseeTsid={TSID}&transferTSID={tsid}
```
```sh
POST v1/transfer/void?licenseeTsid={TSID}&transferTSID={tsid}
```
```sh
POST v1/transfer/update?licenseeTsid={TSID}&transferTSID={tsid}
```


### Lab results endponts:
```sh
POST v1/lab-results/push?licenseeTsid={TSID}
```
```sh
POST v1/lab-results/pull?licenseeTsid={TSID}&lab_result_tsid={tsid}
```


# Data Contract

### Inventory Transfer header only 

```json
{
  "total_count": 110,
  "transfers": [
    {
      "transfer_tsid": "WA0000.IT0000",
      "transfer_type": "delivery",
      "date_created": "2019-09-15T15:53:00+05:00",
      "date_released": "2019-09-15T15:53:00+05:00",
      "date_delevered": "2019-09-15T15:53:00+05:00",
      "source_licensee_tsid": "WA0000.MM00000",
      "destination_licensee_tsid": "WA0000.MM000",
      "status": "in-transit",      
      "estimated_depart_datetime": "2019-09-15T15:53:00+05:00",
      "estimated_arrival_datetime": "2019-09-15T15:53:00+05:00"
    }
  ]
}
```

### Inventory Transfer detail

```json
{
      "transfer_tsid": "WA0000.IT1DR",
      "transfer_type": "delivery",
      "date_created": "2019-09-15T15:53:00+05:00",
      "date_released": "2019-09-15T15:53:00+05:00",
      "date_delevered": "2019-09-15T15:53:00+05:00",
      "source_licensee_tsid": "WA000.MM00000",
      "destination_licensee_tsid": "WA0000.MM0000",
      "status": "in-transit",
      "void": "false",
      "estimated_depart_datetime": "2019-09-15T15:53:00+05:00",
      "estimated_arrival_datetime": "2019-09-15T15:53:00+05:00",
      "planned_route": "",
      "vehicle": {
    	"make": "Ford",
        "model": "F-150",
	"year": "2000",
        "color": "Yellow",
        "vin": "V383753034034",
        "license_plate": "Z27-446"
      },
      "driver": {
        "name": "Drive Name",
        "license_number": "MD-220-99-D-2"
      },
      "product_lookup": [
        {
          "tsid": "WA0000.IT00000",
          "vendor_puk":"0120004654",
          "product_name": "Sweet Blue Lilac 3.5 g",
          "uom": "ea",
          "strain_tsid": "WA00000.S0000",
          "strain_name": "Sweet Blue Lilac",
          "product_type": "Wet Flower",
          "cannabis_content":3.5,
          "cannabis_content_uom":"gm"
        }
      ],
      "lab_result_lookup": [
        {
          "lab_result_tsid": "WA0000.LR0000",
          "thca_percent": 23.000,
          "thca_mg_g": 0.000,
          "thc_percent": 0.300,
          "thc_mg_g": 0.000,
          "cbd_percent": 0.000,
          "cbd_mg_g": 0.000,
          "cbda_percent": 0.050,
          "cbda_mg_g": 0.000,
          "total_cbd": 0.044,
          "total_thc": 20.471
        }
      ],
      "transfer_items": [
        {
          "inventory_tsid": "WA0000.II0000",
          "lab_result_tsid": "WA000.LR0000",
          "product_tsid": "WA0000.IT00000",
          "sample_type": "not-sample",
          "transfered_quantity": 200,
          "received_quantity": null,
          "unit_price": "12.5"
        }
      ]
}
```

### Constants
#### Unit of measure:
```json
"uom": [
    "gm",
    "ea",
    "oz",
    "fl-oz",
    "lb",
  ],	
```		
#### Inventory transfer types:
```json		
"transfer_types": [
          "delivery",
          "pick-up",
          "third-party-delivery"
        ],
```		
#### Inventory transfer status:
```json	
"transfer_status": [
      "open",
      "in-transit",
      "delivered",
      "rejected",
      "canceled"
  ],

```		
#### Product types:
```json	
"product_type": [	
      "Kief",
      "Wet Flower",
      "Wet Other Plant Material",
      "Dry Flower",
      "Dry Other Material",

      "Clone",
      "Seed",
      "Plant Tissue",
      "Mature Plant",

      "Infused Solid Edible",
      "Infused Liquid Edible",
      "Extract for Inhalation",
      "Infused Topicals",

      "Mix",
      "Mix Infused"
      "Capsule",
      "Tincture",
      "Transdermal Patch",
      "Suppository",


      "Hash",
      "Hydrocarbon Wax",
      "CO2 Hash Oil",
      "Food Grade Extract"
],

```		

#### Sample Designations:
```json						
"sample_type": [	
          "not-sample",
          "mandatory-qa-sample",
          "non-mandatory-qa-sample",
          "budtender-sample" ,
          "sales-sample" 
]
```

### Lab Results 
- to be added


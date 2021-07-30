## Invoice Object Definitions

| Field | Description |     |
| ----- | ----------- | --- |
| invoiceID | An identifier for this document, assigned by the sender. | |
| trailerNumber | | |
| issueDate | The date, assigned by the sender, on which this document was issued. | |
| pro | PRO Number: A pre-assigned, 10-digit freight bill number given to each shipment to serve as a tracking number. PRO is an acronym for Progressive Rotating Order. | |
| dueDate | The date on which Invoice is due. | |
| freightBillEntryDate | Date freight bill was entered into the system – it’s a system value that’s automatically applied and not a user-entered date.  |
| billToIndicator |   |
| consignorAssignedID | An identifier for this consignment, assigned by the consignor. | |
| consigneeParty | Object - A party to which goods are consigned. | |
| *contains* | accountNumber | An identifier for this party. |
| | name | A name for this party. |
| | address | Object |
| | line | An unstructured address line. |
| | city | The name of a city, town, or village. |
| | state | A territorial division of a country, such as a county or state, expressed as text. |
| | postalCode | The postal identifier for this address according to the relevant national postal service, such as a ZIP code or Post Code. |
| | country | The primary country of this contact. |
| shipperParty | references consigneeParty | |
| po | | |
| bol | Bill of Lading - A legal document signed by the shipper and carrier tendering the responsibility of the freight to the carrier. The BOL states pertinent information for the shipment such as the complete address of the shipper and consignee, number of pieces, description, weight, and any hazardous material information. | |
| additionalDocumentReference | Object contains additional document references | |
| *contains* | documentType | The type of document being referenced, expressed as text. |
| | id | |
| | documentTypeCode | example (BOL) |
| | | |
| accountingSupplierParty | references consigneeParty | |
| accountingCustomerParty | references consigneeParty | |
| allowanceCharge | object - An allowance or charge covered by these delivery terms. | |
| *contains* | discountFunction | denotes type of discount |
| | totalDiscount | total dollar amount of discount|
| | totalDiscountPercentage | discount percentage  |
| | reasonCode | A mutually agreed code signifying the reason for this allowance or charge. | 
| | reason | The reason for this allowance or charge.|  
| | fuelsurchargePercentage | fuel surcharge percentage | 
| | fuelsurchargeAmount | amount of fuel surcharge applied |  
| payableAmount | The amount of the monetary total to be paid. | |
| totalFreightCharges | The total monetary amount of all charges. | |
| chargeTotalAmount | The total monetary amount of all charges. |
| amountPaid | Amount of any payments that have been applied | |
| currencyCode | A code signifying the default currency for this document. | |
| invoiceLine | object - A line describing an invoice item. | |
| *contains* | id | |
| | note | Free-form text pertinent to this document, conveying information that is not contained explicitly in other structures. |
| | quantity | |
| | extendedAmount | The total amount for this invoice line, including allowance charges but net of taxes. |
| | itemDescription | |
| | hazmat | object - identifies the hazmat code and undgCode | 
| | code | A code signifying a kind of hazard for a material. |
| | undgCode | The UN code for this kind of hazardous item. |
| | weight | weight of line item |
| | unitOfMeasure   | currently always CWT for HundredWeight  |
| | cwtRate | Rate charged per UOM |
| | specialRate | object - contains the code and cost of the special rate. | 
| | code |   |
| | cost |   |
| | documentReference | A reference to a document associated with this invoice line. | 
| | *contains* | | 
| | documentType | The type of document being referenced, expressed as text. |
| | id | |
| | documentTypeCode | The type of document being referenced, expressed as a code. |
| | commodityCode | The harmonized international commodity code for cross border and regulatory (customs and trade statistics) purposes. | 
| | consigneeDepartmnent |   |
| | nmfcNumber |   |
| | nmfcSubNumber |   |
| firstArrivalPortLocation | object - The first arrival location in a transport. This would be a port for sea, an airport for air, a terminal for rail, or a border post for land crossing. | |
| *contains:* | id | |
| | description | Text describing the attribute that applies to the condition. |
| | city |   |  
| | state |  | 
| lastExitPortLocation | object references firstArrivalPortLocation | |
| totalPieces | Total count of pieces of freight on the shipment | |
| grossWeightMeasure | The entire weight of a shipment including containers and packaging materials. | |
| invoiceType | A code signifying the type of the Invoice. | |
| scacCode | | |
| pickupDate | The actual pickup date. | |
| deliveryDate | The actual date of delivery. | |
| billingTerms | Prepaid or Collect | |
| imageRetrievalResult | A string which indicates an image is available for the retrieved invoice. If “SUCCESS”, there will be data in the images object. | |
| images | object | |
| *contains* | url | The url locater for the image. |
| | documentType | The document type. |
| | data | |
| | contentType | The content type. |


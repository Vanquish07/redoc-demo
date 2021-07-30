## Shipment Tracking History Object Definitions

| Field | Description |     |
| ----- | ----------- | --- |
| pro | PRO-tracking number | |
| documentReference | The document reference contains additional BOL & PO numbers, and other document references. References are data type strings. Example: “BOL” | |
| *contains* | ID | |
| | documentType | Document type code |
| pickupRequestNumber | | |
| pickupDate | The actual pickup date. | |
| pickupTime | The actual pickup time. | |
| expeditedCode | The selected code that pertains to Estes Time Critical product (guaranteed service).  | |
| expeditedDescription | Describes the Time Critical Shipment Due By time  - see the following table. | |
| | **Expedited Code** | **Expedited Description** |
| | GMS3 | Time Critical Shipment Due by 10 am |
| | CGM3 | Time Critical Shipment Due by 10 am |
| | GMS2 | Time Critical Shipment Due by 12 pm |
| | CGM2 | Time Critical Shipment Due by 12 pm |
| | GMS1 | Time Critical Shipment Due by 5 pm |
| | CGM1 | Time Critical Shipment Due by 5 pm |
| | GMV1 | Time Critical Volume Due by 5 pm |
| | GMV2 | Time Critical Volume Due by 5 pm |
| isTruckload | A Boolean indicator (e.g. True/False) which identifies shipments moving under a Traditional truckload service brokered by Estes that typically move on non-Estes assets. Note, this flag is not for Volume shipments which are much more common. |
| isResidential | A Boolean indicator (e.g. True/False) which identifies a shipment as residential delivery.  | |
| status | A class to describe the condition or position of an object. | |
| *contains* | conciseStatus | The following milestone event - see the following list |
| | | Departed Pickup Location |  
| | | In Transit | 
| | | Out for Delivery | 
| | | Delivered | 
| | expandedStatus | |
| | referenceDate | The reference date for this status. |
| | referenceTime | The reference time for this status. |
| | reasonCode | The reason for this status condition or position, expressed as a code.  |
| | reason | The reason for this status condition or position, expressed as text.  Refer to the following list: |
|| **Tracking Reason Code** | **Reason Description** |
|| AGT | Awaiting Delivery - Freight Given to Final Delivery Agent |
|| BBC | Delivery Completed - OK |
|| BK | Delivery Attempted - Breakdown |
|| BRK | Delivery in Progress - Documents Submitted to Broker |
|| CLO | Delivery Completed - Closed Out |
|| CO | Unable to Deliver - Will Attempt Tomorrow |
|| CT | Delivery Attempted - CT |
|| CTI | Delivery Completed - Delivered to Interline Partner |
|| CutOffResolved | Unable to Deliver - Will Reattempt Tomorrow |
|| DB | Undelivered - Duplicate Billing |
|| DCA | Undelivered - Declaration Accepted |
|| DD | Delivery Completed - Damage Noted |
|| DDI | Delivery Completed - Delivered to Interline with Damage Noted |
|| Departed | Departed Delivery Location |
|| DI | Awaiting Delivery - Freight Given to Interline Partner |
|| DM | Delivery Completed - Delivered to Broker at Border |
|| DMP | Delivery Completed - Refused and Estes Handling Disposal |
|| DO | Delivery Completed - Overage Noted |
|| DOI | Delivery Completed - Delivered to Interline Partner |
|| DPR | Delivery Completed - Partially Refused |
|| DPU | Delivery Completed - Freight Picked up from Dock |
|| DRC | Undelivered - Reconsigned |
|| DRD | Delivery Attempted - Damage Noted, Freight Refused |
|| DRF | Delivery Attempted - Freight Refused |
|| DRS | Delivery Attempted - Shortage Noted, Freight Refused |
|| DS | Delivery Completed - Shortage Noted |
|| DSI | Delivery Completed - Delivered Short to Interline |
|| DSW | Delivery Completed - Shortage Noted, Shrink Wrap Intact |
|| DTS | Undelivered - Returned to Shipper |
|| EndofDayResolved | Unable to Deliver - Will Attempt Tomorrow |
|| EQ | Delivery Attempted - Special Equipment Required |
|| EXL | Delivery in Progress - Freight Given to Estes LTL |
|| HF | Delivery Attempted - Held Freight(Hazard/Poison/Freeze) |
|| HL | Delivery Attempted - Customer Holiday |
|| INB | Delivery in Progress - Freight In Bond |
|| L2L | Awaiting Delivery - Freight Given to Final Delivery Agent |
|| LT | Out for Delivery |
|| NB | Delivery Completed - Delivery Receipt Unavailable |
|| NF | Delivery Attempted - Freight Unavailable |
|| NFT | Delivery Completed - No Freight Over 30 Days |
|| NR | Delivery Attempted - No Receiving Personnel |
|| OH | Delivery Attempted - On Hand |
|| OK | Delivery Completed - OK |
|| OP | Delivery Completed - Container(s) Open |
|| OV | Delivery Attempted - Overage |
|| PL | Delivery Completed - Shortage Noted |
|| PR | Delivery Completed - Partially Refused |
|| PUD | Out for Delivery |
|| PW | Delivery Attempted - Poor Weather Conditions |
|| RCC | Awaiting Delivery - Customs Released |
|| RCN | Undelivered - Reconsigned |
|| RD | Delivery Attempted - Damage Noted, Freight Refused |
|| RDD | Awaiting Delivery - Freight Given to Final Delivery Agent |
|| RF | Delivery Attempted - Freight Refused |
|| RS | Delivery Attempted - Shortage Noted, Freight Refused |
|| RTI | Undelivered - Returned to Interline |
|| RTS | Undelivered - Returned to Shipper |
|| SND | Delivery in Progress – Freight Given to Consignee for Unloading |
|| SSR | Undelivered - No Freight Shipper Load and Count |
|| ST | Delivery Attempted - Customer on Strike |
|| UL | Delivery Attempted - Unable to Locate Consignee |
|| UL | Delivery Attempted - Unable to Locate Customer |
|| UNL | Delivery Attempted - UNL |
|| UP | Delivery Attempted - Awaiting Payment |
|| WDL | Delivery Attempted - Weather Delay |
| | quantity | The total number of goods items in this shipment. |
| | packageType | |
| | packageDescription | |
| | receivedBy | |
| estimatedDelivery | Object - The period estimated for delivery. | |
| *contains* | startDate | The date on which this period begins. |
| | startTime | The time at which this period begins. |
| | endDate | The date on which this period ends. |
| | endTime | The time at which this period ends. |
| transitDays | Time estimated to arrive at the last point within the 48 states. In an example with a shipment headed for Alaska, a value of 6 days shown as “transit days” may be the number of days needed to get the shipment to its final exit point *before* Alaska (instead of the full number of days needed for the shipment to arrive at its final destination.)  | *Important: Transit times apply to standard Estes LTL shipments and are based on the actual date and time of the pickup, which may be different from the shipment date entered. Transit times obtained via www.estes-express.com are the primary source of information pertaining to Estes’ service. Transit times for specialty services and custom solutions provided by other Estes operating entities may differ based on the services selected. In the event of a discrepancy with data obtained from a non-Estes source, service standard information published on www.estes-express.com will take precedence. |
| driverInfo | | |
| *contains* | name | |
| | geoCoordinates | |
| | stopsAway | |
| | driverName | |
| appointment | | |
| *contains* | status | |
| | startDate | |
| | startTime | |
| | endDate | |
| | endTime | |
| appointmentHistory | Object | |
| *contains* | status | |
| | createdDate | |
| | createdTime | |
| | startDate | |
| | startTime | |
| | endDate | |
| | endTime | |
| piecesCount | | |
| totalWeight | | |
| consigneeParty | Object - The designated recipient (customer) of a shipment as indicated on the [Bill of Lading](https://www.estes-express.com/resources/transportation-glossary ##bol). | |
| *contains* | accountNumber | Used in each referenceNumber element of the optional unbounded referenceNumbers element, this code defines the type of reference number passed in that element. Below are the valid values: |
| | | AID - Appointment ID | 
| | | ARN - Amazon Reference Number | 
| | | AUT - Authorization Number | 
| | | BOL - Shipper Bill of Lading Number | 
| | | DOC - Dock Door Number | 
| | | DPT - Consignee Department Number | 
| | | EXL - Estes Unique ID EUID# or CUID# | 
| | | HO - Homeowner Name | 
| | | LDN - Load Number ID | 
| | | NUM - Shipper Reference Numbers | 
| | | PKG - Sipper Package ID | 
| | | PON - Purchase Order Number | 
| | | PRO - Estes PRO# | 
| | | PU# - Pickup Number from the Customer | 
| | | RAU - Shipper Return Authorization | 
| | | SID - Ship ID# | 
| | | SNO - Shipper Numbers | 
| | name | The name of this branch or division of an organization. |
| | address | class |
| | line (items) | An unstructured address line. |
| | city | The name of a city, town, or village. |
| | state | the state abbreviation |
| | postalCode | The postal identifier for this address according to the relevant national postal service, such as a ZIP code or Post Code. |
| shipperParty | Object - The designated shipper as indicated on the [Bill of Lading](https://www.estes-express.com/resources/transportation-glossary ##bol). | |
| *contains* | accountNumber | Used in each referenceNumber element of the optional unbounded referenceNumbers element, this code defines the type of reference number passed in that element. Below are the valid values: |
| | | AID - Appointment ID | 
| | | ARN - Amazon Reference Number | 
| | | AUT - Authorization Number | 
| | | BOL - Shipper Bill of Lading Number | 
| | | DOC - Dock Door Number | 
| | | DPT - Consignee Department Number | 
| | | EXL - Estes Unique ID EUID# or CUID# | 
| | | HO - Homeowner Name | 
| | | LDN - Load Number ID | 
| | | NUM - Shipper Reference Numbers | 
| | | PKG - Sipper Package ID | 
| | | PON - Purchase Order Number | 
| | | PRO - Estes PRO# | 
| | | PU# - Pickup Number from the Customer | 
| | | RAU - Shipper Return Authorization | 
| | | SID - Ship ID# | 
| | | SNO - Shipper Numbers | 
| | name | The name of this branch or division of an organization. |
| | address | class |
| | line (items) | An unstructured address line. |
| | city | The name of a city, town, or village. |
| | state | the state abbreviation |
| | postalCode | The postal identifier for this address according to the relevant national postal service, such as a ZIP code or Post Code. |
| thirdParty | Object - The designated third party of a shipment as indicated on the [Bill of Lading](https://www.estes-express.com/resources/transportation-glossary ##bol). | |
| *contains* | accountNumber | Used in each referenceNumber element of the optional unbounded referenceNumbers element, this code defines the type of reference number passed in that element. Below are the valid values: |
| | | AID - Appointment ID | 
| | | ARN - Amazon Reference Number | 
| | | AUT - Authorization Number | 
| | | BOL - Shipper Bill of Lading Number | 
| | | DOC - Dock Door Number | 
| | | DPT - Consignee Department Number | 
| | | EXL - Estes Unique ID EUID# or CUID# | 
| | | HO - Homeowner Name | 
| | | LDN - Load Number ID | 
| | | NUM - Shipper Reference Numbers | 
| | | PKG - Sipper Package ID | 
| | | PON - Purchase Order Number | 
| | | PRO - Estes PRO# | 
| | | PU# - Pickup Number from the Customer | 
| | | RAU - Shipper Return Authorization | 
| | | SID - Ship ID# | 
| | | SNO - Shipper Numbers | 
| | name | The name of this branch or division of an organization. |
| | address | class |
| | line (items) | An unstructured address line. |
| | city | The name of a city, town, or village. |
| | state | the state abbreviation |
| | postalCode | The postal identifier for this address according to the relevant national postal service, such as a ZIP code or Post Code. |
| destinationTerminal | Object - The terminal that will deliver the shipment within the geographical area that the terminal serves. | |
| *contains:* | number | |
| | name | The name of this branch or division of an organization. |
| | address | references consigneeParty/address - A class to define common information related to an address. |
| | telephone | The primary telephone number of this contact. |
| | fax | The primary fax number of this contact. |
| | email | The primary email address of this contact. |
| interlineInfo | references consigneeParty | |
| freightCharges | | |
| interlinePro | Interline pro for shipment tracking | |
| disclaimers | | |
| movementHistory | Object (this section includes current history and the running history of the movement of freight) | |
| *contains* | id | |
| | description | |
| | location | *contains* |
| | id | |
| | name | |
| | code | |
| | address | *contains* |
| | line | |
| | city | |
| | state | |
| | postalCode | |
| | geoCoordinates | (See chapter on Geo Location) |
| | contact | *contains* |
| | telephone | |
| | fax | |
| | transportEventTypeCode | |
| | statusHistory | *contains* |
| | conciseStatus | |
| | expandedStatus | |
| | referenceDate | |
| | referenceTime | |
| | reasonCode | |
| | reason | |
| | quantity | |
| | packageType | |
| | packageDescription | |

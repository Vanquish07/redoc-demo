## Pickup Request Data Object Definitions

| Field | Description |     |
| ----- | ----------- | --- |
| requestNumber | A reference number given to the customer by the time-critical team when they request a time-critical shipment. It’s the number used to identify the request in the system throughout the shipping process. | |
| pro | PRO Number is a pre-assigned, 10-digit freight bill number given to each shipment to serve as a tracking number. PRO is an acronym for Progressive Rotating Order. | |
| status | A class to describe the condition or position of an object. | |
| *contains* | description  | Text describing this status. |
| | reason  | The reason for this status condition or position, expressed as text. |
| | reasonCode  | The reason for this status condition or position, expressed as a code. See the following: |
| | **Pickup Change Reason Code** | **Change Reason** | **Full Description** |
| | BK | BREAKDOWN | Pickup Rescheduled - Equipment Not Available |
| | CC | Customer Closed | Pickup Rescheduled - Shipper Unavailable |
| | CO | Driver Cut Off | Pickup Rescheduled - Daily Route Constraint |
| | CR | Customer Request | Pickup Rescheduled - Customer Request |
| | DE | Dispatch Error | Pickup Rescheduled - Dispatcher Planning |
| | FN | No Freight or Freight Not Ready | Pickup Rescheduled - Freight Not Available |
| | HO | Holiday | Pickup Rescheduled - Shipper Holiday |
| | NS | Non-Service Not Daily Area | Pickup Rescheduled - Area Not Serviced Today |
| | RL | Request Late - PU came in too late for sameday | Pickup Rescheduled - Received Request Too Late |
| | SK | Shipper has no knowledge | Pickup Rescheduled - Shipper Has No Knowledge of Freight |
| | WE | WEATHER | Pickup Rescheduled - Inclement Weather |
| shipper |  Contains several classes including name, address and contacts. | |
| *contains* | name  | The name of this branch or division of an organization. |
| | accountCode  | |
| address | This is the address of the pickup location. Although it’s optional, either it or the accountCode must be indicated. If an accountCode is provided, the shipper address (pickup location) is pulled from the Estes account master by the account code. If an address is provided in addition to the account code, the address associated with the account code will override the information provided in the shipperAddress element. | |
| *contains* | line  | An unstructured address line. |
| | city  | The name of a city, town, or village. |
| | state  | A territorial division of a country, such as a county or state, expressed as text. |
| | postalCode  | The postal identifier for this address according to the relevant national postal service, such as a ZIP code or Post Code. |
| | country  | The country in which this address is situated. |
| contacts | A class that contains contact information | |
| *contains* | type  | The type of this contract, expressed as text, such as “Cost plus award fee” and “Cost plus fixed fee” from UNCEFACT Contract Type code list. |
| | name  | The name of this contact. It is recommended that this be used for a functional name and not a personal name. |
| | email  | The primary email address of this contact. |
| | phone  | The primary telephone number of this contact. |
| | fax  | The primary fax number of this contact. |
| | receiveNotifications | Boolean |
| | notificationMethod  | This code indicates the method of notification if the receiveNotifications element is enabled for the contact (Y). Valid values are listed below: |
| |  | • E — Email |
| |  | • F — Fax (NOTE Fax-based notifications are unavailable at this time.) |
| requestAction | This is the pickup action to perform. If the request is for Estes to pick up a full trailer, choose HE (to indicate empty) or HL (to indicate loaded). If you need Estes to drop off an empty trailer, choose SE. If the request is for a pickup of freight from your dock that is not a trailer-load, then pass LL (or don’t pass this element, and it will default to LL). If Estes must call to set up an appointment before arriving, then pass AP. Valid values are listed below: | |
| | • AP — Appointment required | |
| | • HE — LTL hook empty | |
| | • HL — LTL hook loaded | |
| | • LL — LTL live load [default] | |
| | • SE — LTL spot/drop empty | |
| paymentTerms | These are the requested payment terms to apply to any resulting shipments picked up. Valid values include: | |
| | • COL — Collect  | |
| | • PPD — Prepaid  | |
| totalPieces |  | |
| totalWeight | The total declared weight of the goods in this consignment, including packaging but excluding the carrier’s equipment. | |
| totalHandlingUnits |  | |
| hazmatFlag | Use this to indicate the requirement to pick up hazardous materials. Cite additional details and specify the identity and type of hazardous materials in the request’s commodity elements area. | |
| expeditedCode | This is an optional code indicating the priority of the resulting shipment after successful pickup. Valid values are listed below: | |
| | • (BLANK) — normal [default] | |
| | • E — Estes Forwarding | |
| | • G — Guaranteed  | |
| | • H — Hot  | |
| whoRequested | This optional code indicates the party that requested the pickup. The following are the valid values: | |
| | • (BLANK) — Unknown  | |
| | • C — Consignee  | |
| | • S — Shipper  | |
| | • 3 — 3rd party  | |
| | • 4 — 4th party  | |
| userName |  | |
| userAccount |  | |
| thirdPartyName | Name of Third Party Payer of Invoice – aka Bill To Name | |
| thirdPartyAccountCode | Account Code of Third Party Payer of Invoice – aka Bill To Account | |
| consigneeName | Name of Customer receiving the freight | |
| consigneAccountCode | Account Code of Customer receiving the freight | |
| pickupDate |  | |
| pickupStartTime | This is a 4-digit time with a 2-digit hour and 2-digit minute that indicates the start of the time-window when the client expects Estes to execute the pickup. | |
| pickupEndTime | This is a 4-digit time with a 2-digit hour and 2-digit minute that indicates the end of the time-window when the client expects Estes to execute the pickup. | |
| appointmentHistory | class  | |
| *contains* | startDate  | The date on which this period begins. |
| | startTime  | The time at which this period begins. |
| | endDate  | The date on which this period ends. |
| | endTime  | The time at which this period ends. |
| | createdDate  | |
| | createdTime  | |
| transportEvent | An event associated with this Transportation Status report. | |
| *contains* | driver  | Describes a person responsible for driving the transport means. |
| | driverCoordinates  | |
| | estimatedPickupDate  | |
| | estimatedPickupTime  | |
| | stopsAway  | |
| | lastUpdatedDate  | |
| | lastUpdatedTime  | |
| trailers | The part of the rig used to haul goods. A trailer is hooked to an engine-powered tractor. | |
| *contains* | id  | |
| | length  | Use this optional code if the request directs Estes to hook or drop off a trailer at the pickup location. The following are the valid values: |
| |  | • (BLANK) — Trailer length not specified |
| |  | • 20 — 20 feet |
| |  | • 28 — 28 feet |
| |  | • 40 — 40 feet |
| |  | • 45 — 45 feet |
| |  | • 48 — 48 feet |
| |  | • 53 — 53 feet |
| | type  | This optional code indicates the trailer type if the request requires Estes to hook up or drop off a trailer at the pickup location. The following are the valid values: |
| |  | • (BLANK) — Trailer type not specified |
| |  | • CT — Straight Container |
| |  | • LG — Lift Gate |
| |  | • RD — Roll Door |
| |  | • SD — Side Door |
| |  | • ST — Swing Door Truck |
| referenceNumbers | Used in each referenceNumber element of the optional unbounded referenceNumbers element, this code defines the type of reference number passed in that element. Below are the valid values: | |
| | AID - Appointment ID | |
| | ARN - Amazon Reference Number | |
| | AUT - Authorization Number | |
| | BOL - Shipper Bill of Lading Number | |
| | DOC - Dock Door Number | |
| | DPT - Consignee Department Number | |
| | EXL - Estes Unique ID EUID# or CUID# | |
| | HO - Homeowner Name | |
| | LDN - Load Number ID | |
| | NUM - Shipper Reference Numbers | |
| | PKG - Sipper Package ID | |
| | PON - Purchase Order Number | |
| | PRO - Estes PRO# | |
| | PU# - Pickup Number from the Customer | |
| | RAU - Shipper Return Authorization | |
| | SID - Ship ID# | |
| | SNO - Shipper Numbers | |
| commodities | class  | |
| *contains* | code  | Used in each commodity element of the optional unbounded commodities element, this unique commodity code defines the type of commodity being passed. It supports custom commodity code values or you may leave it blank (an empty string) and it will default to “MISC” (without quotes). If you are unsure what to pass, use MISC. |
| | packageCode  | Used in each commodity element of the optional unbounded commodities element, this is a unit of measure for the commodity. Valid values are listed below : |
| |  | • BD — Bundles |
| |  | • BG — Bags |
| |  | • BK — Buckets |
| |  | • BL — Bales |
| |  | • BR — Barrels |
| |  | • BX — Boxes |
| |  | • CN — Cans |
| |  | • CR — Crates |
| |  | • CS — Cases |
| |  | • CT — Cartons |
| |  | • CY — Cylinders |
| |  | • DR — Drums |
| |  | • JC — Jerrican |
| |  | • KT — Kits |
| |  | • PC — Pieces |
| |  | • PK — Packages |
| |  | • PL — Pails |
| |  | • PT — Pallets |
| |  | • RE — Reels |
| |  | • RL — Rolls |
| |  | • SK — Skids |
| |  | • TL — Truckload |
| |  | • TO — Totes |
| description |  | |
| hazmat | *Hazardous Materials:* The Transportation Safety Act of 1974 defines hazardous material as “a substance or material in quantity and form which may pose an unreasonable risk to health and safety or property when transported in commerce.” Consists of hazmarCode and hazmatFlag. | |
| *contains* | hazmatCode  | The hazmat element is optional. If the commodity is not hazardous, omit this element from the commodity being passed to prevent validations from requiring its child elements. Used in each commodity element of the optional unbounded commodities element, this is required if the adjacent hazmat flag has a value. It must start with one of the two values listed here to be a valid industry standard hazardous material code. |
| |  | • NA |
| |  | • UN |
| | hazmatFlag  | Used in each commodity element of the optional unbounded commodities element, the hazmat code here represents the type of hazmat commodity. Valid values are listed below: |
| |  | • (BLANK) |
| |  | • C — Corrosive |
| |  | • D — Dangerous |
| |  | • E — Explosives |
| |  | • F — Flammable |
| |  | • G — Flammable gas |
| |  | • H — Hazardous |
| |  | • L — Chlorine |
| |  | • M — Combustible |
| |  | • N — Nonflammable gas |
| |  | • P — Poison |
| |  | • R — Radioactive |
| |  | • S — Flammable solid |
| |  | • X — Oxidizer |
| pieces | The number of pieces of transport handling equipment (pallets, boxes, cases, etc.) in this consignment. | |
| weight | The total declared weight of the goods in this consignment, including packaging but excluding the carrier’s equipment. | |
| nmfcNumber |  | |
| nmfcSubNumber |  | |
| comments | Used in each comment element of the optional unbounded comments element, the type code here indicates the type of comment. Valid values are listed below: | |
| | • CCM — Consignee Comment | |
| | • CSI — Consignee Special Instruction | |
| | • SCM — Shipper/Stop Comment | |
| | • SSI — Shipper/Stop Special Instruction | |
| | • 3CM — 3rd Party Comment | |
| | • 3SI — 3rd Party Special Instruction | |
| | • 4CM — 4th Party Comment | |
| | • 4SI — 4th Party Special Instruction | |
| | • 5CM — 5th Party Comment | |
| | • 5SI — 5th Party Special Instruction | |
| | • 6CM — 6th Party Comment | |
| | • 6SI — 6th Party Special Instruction | |
| addresses | A class to define common information related to an address. | |
| *contains* | type  | Used in each address element of the optional unbounded addresses element, the type code here indicates the type of address being passed. Valid values are listed below: |
| |  | • C — Consignee Address |
| |  | • 3 — 3rd Party Address |
| |  | • 4 — 4th Party Address |
| |  | • 5 — 5th Party Address |
| |  | • 6 — 6th Party Address |
| | line  | An unstructured address line. |
| | city  | The name of a city, town, or village. |
| | state  | A territorial division of a country, such as a county or state, expressed as text. |
| | postalCode  | The postal identifier for this address according to the relevant national postal service, such as a ZIP code or Post Code. |
| | country  | The country in which this address is situated. |
| contacts | Used in each contact element of the optional unbounded contacts element, the type code here indicates the type of contact being passed. Valid values are listed below: | |
| *contains* | • A — Actual Submitter | |
| | • C — Consignee Contact | |
| | • R — Requested Response Contact | |
| | • S — Shipper Contact | |
| | • 3 — Third Party Contact | |
| | • 4 — Fourth Party Contact | |
| | • 5 — Fifth Party Contact | |
| | • 6 — Sixth Party Contact | |
| | name  | The name of this contact. It is recommended that this be used for a functional name and not a personal name. |
| | email  | The primary email address of this contact. |
| | phone  | The primary telephone number of this contact. |
| | fax  | The primary fax number of this contact. |
| | receiveNotifications | Boolean |
| | notificationMethod  | This code indicates the method of notification if the receiveNotifications element is enabled for the contact (Y). Valid values are listed below: |
| |  | • E — Email |
| |  | • F — Fax (NOTE Fax-based notifications are unavailable at this time.) |
| notifications | You can subscribe to automatic notification emails, which are sent at key events throughout the pickup lifecycle. This code indicates the type of event to subscribe to for automatic notifications. (Valid values are listed below.) It’s also possible to pass multiple notification elements with a different type on each to receive notifications when more than one of the following events occur. The notifications will be sent to all contacts passed with the receiveNotifications element set to Y via a valid associated email address. | |
| | • ACC — Terminal accepted pickup | |
| | • BGN — Work has begun | |
| | • RCV — Pickup request received | |
| | • RJT — Pickup request rejected | |
| | • WRK — Pickup request worked (Estes has the freight.) | |
| originTerminal | The terminal at which freight is received from the shipper. | |
| *contains* | number  | |
| | name  | |
| | address  | A class to define common information related to an address. |
| | *contains*  | |
| | line  | An unstructured address line. |
| | city  | The name of a city, town, or village. |
| | state  | A territorial division of a country, such as a county or state, expressed as text. |
| | postalCode  | The postal identifier for this address according to the relevant national postal service, such as a ZIP code or Post Code. |
| | country  | The country in which this address is situated. |
| | telephone  | The primary telephone number of this contact. |
| | fax  | The primary fax number of this contact. |
| | email  | The primary email address of this contact. |
| transitDays | Time estimated to arrive at the last point within the 48 states. In an example with a shipment headed for Alaska, a value of 6 days shown as “transit days” may be the number of days needed to get the shipment to its final exit point *before* Alaska (instead of the full number of days needed for the shipment to arrive at its final destination.)  | *Important: Transit times apply to standard Estes LTL shipments and are based on the actual date and time of the pickup, which may be different from the shipment date entered. Transit times obtained via www.estes-express.com are the primary source of information pertaining to Estes’ service. Transit times for specialty services and custom solutions provided by other Estes operating entities may differ based on the services selected. In the event of a discrepancy with data obtained from a non-Estes source, service standard information published on www.estes-express.com will take precedence. |

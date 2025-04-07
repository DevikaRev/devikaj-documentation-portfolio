# Credit Card API Documentation

This sample showcases how I document REST APIs using the OpenAPI 3.0 specification.

## Features Demonstrated:
- Endpoint organization using `paths`
- Request and response schemas
- Status codes and validation
- Descriptions aligned to business functions

## Featured Sample: Change Card PIN

The following is a real-world example of how I document sensitive and secure API operations, such as changing a credit card PIN.
This sample demonstrates clarity, structure, and attention to edge cases, which are critical for high-risk operations in fintech APIs.

---

### API Sample: Change Card PIN

```
---
title: Change a PIN
type: api-playground-ui
---
# Change a PIN
This endpoint is a request to change the [personal identification number](glossary/tachyon-glossary/terms/card-pin) (PIN) of a credit card. You may use this endpoint to enable a cardholder to change a current (old) PIN to a new PIN. The current and new PINs are combined and encrypted using AES128. This encrypted data is sent in the request body. The system verifies the current PIN. If the current PIN specified is incorrect, the cardholder would not be able to change the PIN. You may use the [Generate a PIN](generate-card-pin) endpoint to enable a cardholder to generate a temporary PIN. This temporary PIN can be used as the current PIN.

You should not allow the cardholder to use this endpoint to set the PIN for a new card. Use the [Set a secure PIN](card-pin-cvv-management-set-pin-secure) endpoint instead.

You, as an [issuer](glossary/tachyon-glossary/terms/issuer), cannot change the PIN on behalf of the cardholder.
## Limitations

You cannot prevent a cardholder from setting a PIN that has been used in the past.

{{< hint info >}}

<b>This endpoint may fail in the following situations:</b>

- The private keys used to decrypt PIN data are incorrect
- Any network or system error occurs due to which the system fails to decrypt the PIN data

  {{< /hint >}} 

## Prerequisites

The prerequisites are as follows:
- Ensure that you have the base URL, [IFI](glossary/tachyon-glossary/terms/ifi) ID/[Tenant](glossary/tachyon-glossary/terms/tenant) ID, access token, and authorization token to execute the endpoint
- Ensure that you have the accurate [card global unique identifier](glossary/tachyon-glossary/terms/cguid) (CGUID) ID

## Endpoint

{{< api-viewer-legacy jsonFile="/swagger/issuer_supercard-nn_snapshot_5.0.4_swagger-publisher_9c502c75c.json" method="post" path="/tenants/{tenantId}/cards/{cguid}/changePin" >}}   

<br>For more information about this event, see [CARD_PIN_UPDATED](events/card_pin_updated).

## Related use cases

The related use cases are as follows:
- This endpoint is used in the [Card controls](integrations/tachyon-integration-docs/card-control-guide) guide.
- For instructions to encrypt the PIN data, see the section *Encryption logic* of the [Appendix](/us/integrations/tachyon-integration-docs/integrations/card-control-guide/appendix-cardcontrols/) topic.

## Disclaimer
We have taken diligent efforts to ensure the accuracy and completeness of the information in this documentation. This documentation may be updated from time to time for enhancements, improvements, and other changes.

If you cannot find the information you are looking for, take the following steps:

- Help us enrich this documentation by reporting such issues. Select the feedback icon on the right-bottom of a page and submit your feedback
- Contact Tachyon support by email: tc-supportinternal@zeta.tech
```

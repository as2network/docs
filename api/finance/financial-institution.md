# Financial Institution

> This REST API is exclusively for use by financial institution organizations to provide access to platform data 

- [Endpoints](#endpoints)
  * [BillOfLadingVerifier](#billofladingverifier)
    + [getBolDocumentUsingPOST](#getboldocumentusingpost)
      - [Description](#description)
      - [Parameters](#parameters)
      - [Body Parameter](#body-parameter)
      - [Return Type](#return-type)
      - [Content Type](#content-type)
      - [Responses](#responses)
      - [Samples](#samples)
- [Models](#models)
  * [*AppExceptionResponse* AppExceptionResponse](#-appexceptionresponse--appexceptionresponse)
  * [*BolVerifyRequest* BolVerifyRequest](#-bolverifyrequest--bolverifyrequest)

## Endpoints

### BillOfLadingVerifier

#### getBolDocumentUsingPOST

`POST /api/v1/billOfLadingVerifier/search`

Fetch Bill Of Lading document.

##### Description

Fetch Bill Of Lading document matching all the input parameters.

The API will allow the caller to download the First Matching `Bill Of Lading` document matching all the input parameters.

Access is granted only to those Financial Institution and other 3rd parties which have explicitly been granted access.

`billOfLadingNumber`: An exact case insensitive match is done for this parameter.

`oceanCarrierCode`: An exact case insensitive match is done for this parameter.

`consignorPrintedParty`: A partial case insensitive match is done for this parameter.

Minimum acceptable length is 6 characters.

##### Parameters

##### Body Parameter

| Name             | Description                                                            | Required | Default | Pattern |
| ---------------- | ---------------------------------------------------------------------- | -------- | ------- | ------- |
| BolVerifyRequest | Request object for BoL Verifier [ BolVerifyRequest](#BolVerifyRequest) | X        |         |         |

##### Return Type

\-

##### Content Type

  - **/**

##### Responses

| Code | Message                                                                                   | Datatype                                       |
| ---- | ----------------------------------------------------------------------------------------- | ---------------------------------------------- |
| 200  | OK                                                                                        | \<\<\>\>                                       |
| 400  | Bad request                                                                               | [ AppExceptionResponse](#AppExceptionResponse) |
| 401  | Unauthorized                                                                              | \<\<\>\>                                       |
| 403  | Forbidden                                                                                 | \<\<\>\>                                       |
| 404  | No matching Bill of Lading available on the platform for the provided set of input params | [ AppExceptionResponse](#AppExceptionResponse) |
| 500  | Server Error                                                                              | [ AppExceptionResponse](#AppExceptionResponse) |

http response codes

##### Samples

## Models

### *AppExceptionResponse* AppExceptionResponse

| Field Name | Required | Type   | Description       | Format |
| ---------- | -------- | ------ | ----------------- | ------ |
| code       | X        | String | Error Code        |        |
| message    | X        | String | Exception Message |        |
| timestamp  | X        | String | timestamp         |        |

### *BolVerifyRequest* BolVerifyRequest

| Field Name            | Required | Type   | Description                                               | Format |
| --------------------- | -------- | ------ | --------------------------------------------------------- | ------ |
| billOfLadingNumber    | X        | String | Bill Of Lading number to search for                       |        |
| oceanCarrierCode      | X        | String | Carrier SCAC code                                         |        |
| consignorPrintedParty | X        | String | Consignor details field as in the Bill Of Lading document |        |

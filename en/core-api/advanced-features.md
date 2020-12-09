# Core API Advanced Features
<hr>
<!-- TODO:add sample code for lang other than CURL? -->

Core API has various optional parameters that can be utilized to integrate with more advanced use cases.

## General
### Recommended Parameters
You can customize the `transaction_details` to include more information such as `customer_details`, `item_details`, and so on. While sending API requests, it is recommended to send more details regarding the transaction, so that these details can get added to the report. This report can be viewed on the dashboard.

<!-- tabs:start -->

#### **JSON Parameters**
The JSON parameters added in the *Request Body* of a [Charge API Request](/en/core-api/credit-card.md#_2-sending-transaction-data-to-charge-api), to include more details of the transaction, are shown below.

```json
{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "order102",
    "gross_amount": 13000
  },
  "credit_card": {
    "token_id": "<token_id from Get Card Token Step>",
    "authentication": true,
  },
  "item_details": [
    {
      "id": "a01",
      "price": 7000,
      "quantity": 1,
      "name": "Apple"
    },
    {
      "id": "b02",
      "price": 3000,
      "quantity": 2,
      "name": "Orange"
    }
  ],
  "customer_details": {
    "first_name": "Budi",
    "last_name": "Susanto",
    "email": "budisusanto@example.com",
    "phone": "+628123456789",
    "billing_address": {
      "first_name": "Budi",
      "last_name": "Susanto",
      "email": "budisusanto@example.com",
      "phone": "08123456789",
      "address": "Sudirman No.12",
      "city": "Jakarta",
      "postal_code": "12190",
      "country_code": "IDN"
    },
    "shipping_address": {
      "first_name": "Budi",
      "last_name": "Susanto",
      "email": "budisusanto@example.com",
      "phone": "0812345678910",
      "address": "Sudirman",
      "city": "Jakarta",
      "postal_code": "12190",
      "country_code": "IDN"
    }
  }
}
```

#### **Sample Charge API Request**
The JSON objects `item_details`, `customer_details`, and `shipping_address` are included in the sample Charge API Request shown below.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "order102",
    "gross_amount": 13000
  },
  "credit_card": {
    "token_id": "<token_id from Get Card Token Step>",
    "authentication": true,
  },
  "item_details": [
    {
      "id": "a01",
      "price": 7000,
      "quantity": 1,
      "name": "Apple"
    },
    {
      "id": "b02",
      "price": 3000,
      "quantity": 2,
      "name": "Orange"
    }
  ],
  "customer_details": {
    "first_name": "Budi",
    "last_name": "Susanto",
    "email": "budisusanto@example.com",
    "phone": "+628123456789",
    "billing_address": {
      "first_name": "Budi",
      "last_name": "Susanto",
      "email": "budisusanto@example.com",
      "phone": "08123456789",
      "address": "Sudirman No.12",
      "city": "Jakarta",
      "postal_code": "12190",
      "country_code": "IDN"
    },
    "shipping_address": {
      "first_name": "Budi",
      "last_name": "Susanto",
      "email": "budisusanto@example.com",
      "phone": "0812345678910",
      "address": "Sudirman",
      "city": "Jakarta",
      "postal_code": "12190",
      "country_code": "IDN"
    }
  }
}'
```

<!-- tabs:end -->

<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

For general use, the JSON parameters recommended to be included in the Charge API request are described in the table given below.

<table style="width:100%">  
  <tr>     
    <th colspan="2">Parameter</th> <th>Description</th>  <th>Type</th>  
  </tr>   
    <tr>      
    <td>item_details</td> <td></td> <td>The details of the item purchased.</td> <td>Object</td>
  </tr>
  <tr>      
   <td></td> <td>id</td>  <td>The id of the item purchased.</td> <td>String</td>
  </tr>
  <tr>      
   <td></td> <td>price</td>  <td>The price of the item.</td> <td>String</td>
  </tr>
   <tr>      
   <td></td> <td>quantity</td>  <td>The number of items purchased.</td> <td>String</td>
  </tr>
  <tr>      
   <td></td> <td>name</td>  <td>The name of the item purchased.</td> <td>String</td>
  </tr>
  <tr>      
    <td>customer_details</td> <td></td> <td>The details of the customer.</td> <td>Object</td>
  </tr>
  <tr>      
   <td></td> <td>first_name</td>  <td>The first name of the payer. </td> <td>String</td>
  </tr>
  <tr>      
   <td></td> <td>last_name</td>  <td>The last name of the payer. </td> <td>String</td>
  </tr>
   <tr>      
   <td></td> <td>email</td>  <td>The email address of the payer. </td> <td>String</td>
  </tr>
  <tr>      
   <td></td> <td>phone</td>  <td>The phone number of the payer.</td> <td>String</td>
    </tr> <tr>      
   <td></td> <td>address</td>  <td>The postal address of the payer.</td> <td>String</td>
  </tr>
  <tr>      
   <td></td> <td>city</td>  <td>The city of payer.</td> <td>String</td>
  </tr>
    <tr>      
   <td></td> <td>postal_code</td>  <td>The postal code of the payer.</td> <td>String</td>
  </tr>
  <tr>      
   <td></td> <td>country_code</td>  <td>The country code of the payer. </td> <td>String</td>   </tr> <td>shipping_address</td> <td></td> <td>The address to which the item is to be shipped.</td> <td>String</td>
  </tr>
  <tr>      
   <td></td> <td>first_name</td>  <td>The first name of the customer.</td> <td>String</td>
  </tr>
  <tr>      
   <td></td> <td>last_name</td>  <td>The last name of the customer</td> <td>String</td>
  </tr>
   <tr>      
   <td></td> <td>email</td>  <td>The email address of the customer.</td> <td>String</td>
  </tr>
  <tr>      
   <td></td> <td>phone</td>  <td>The phone number of the customer.</td> <td>String</td> </tr><tr>      
   <td></td> <td>address</td>  <td>The postal address.</td> <td>String</td>
  </tr>
  <tr>      
   <td></td> <td>city</td>  <td>The name of the city.</td> <td>String</td>
  </tr>
   <tr>      
   <td></td> <td>postal_code</td>  <td>The postal code.</td> <td>String</td>
  </tr>
  <tr>      
   <td></td> <td>country_code</td>  <td>The country code.</td> <td>String</td>   </tr></table>




For more details, refer to [JSON Object](https://api-docs.midtrans.com/#json-object).

</article>
</details>

### Custom Transaction Expiry
Custom transaction expiry can be configured for all payment methods except for *Credit Card* payment methods. You can configure expiry time for the payment of a transaction with the *Transaction Status* : *Pending*. After the expiry time is elapsed, the customer will not be able to make a payment for the transaction. 
<!-- tabs:start -->

#### **JSON Parameters**
The JSON parameter added in the *Request Body* of a [Charge API Request](/en/core-api/e-wallet.md#_1-sending-transaction-data-to-charge-api-request), to configure custom transaction expiry, is shown below.

```json
...
  "custom_expiry": {
      "order_time": "2016-12-07 11:54:12 +0700",
      "expiry_duration": 60,
      "unit": "minute"
  }
...
```

#### **Sample Charge API Request**
The JSON object `custom_expiry` included in the sample Charge API Request is shown below.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  "payment_type": "gopay",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 13000
  },
  "custom_expiry": {
      "order_time": "2016-12-07 11:54:12 +0700",
      "expiry_duration": 60,
      "unit": "minute"
  }
}'
```
<!-- tabs:end -->

<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

The JSON parameters recommended to be included in the Charge API request, to configure custom transaction expiry, are described in the table given below.

Parameter| Description | Type | Required | Note
--- | --- | --- | --- | ---
order_time | The date and time at which the item was ordered.<br/>If not specified, transaction time (the time at which the payment method was confirmed) will be used as order_ time. | String (50) |Optional|It is in the format, *YYYY-MM-DD* *HH:MM:SS.*<br/>Time zone: Western Indonesian Time (GMT+7)
expiry_duration | The duration for which the transaction is valid. | String (50) |Required|
unit | The unit of expiry_duration. | String (50) |Required|Valid values are second, minute, hour or day.<br>Default value is minute.

</article>
</details>

### Custom Fields
Custom Fields is a feature that enables you to include any specific details about the transaction. These details will be sent to the Core API. These will be included in the HTTP notification sent from Midtrans to the merchant backend. These custom details will also be displayed on the *Dashboard* under order details.
<!-- tabs:start -->

#### **JSON Parameters**
The JSON parameters added in the *Request Body* of a [Charge API Request](/en/core-api/credit-card.md#_2-sending-transaction-data-to-charge-api), to include custom fields, are shown below.

```json
...
  "custom_field1": "this is custom text defined by merchant",
  "custom_field2": "order come from web",
  "custom_field3": "customer selected blue color variant"
...
```

#### **Sample Charge API Request**
The JSON objects `custom_field1`, `custom_field2`, `custom_field3` included in the sample Charge API Request are shown below.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 13000
  },
  "custom_field1": "this is custom text defined by merchant",
  "custom_field2": "order come from web",
  "custom_field3": "customer selected blue color variant"
}'
```
<!-- tabs:end -->

<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

The JSON parameters recommended to be included in the Charge API request, to configure custom transaction expiry, are described in the table given below.

Parameter| Description | Type |Required
--- | --- | --- | ---
custom_field1 | You can write custom details about the transaction. |String(255)|Optional
custom_field2 | You can write custom details about the transaction. |String(255)|Optional
custom_field3 | You can write custom details about the transaction. |String(255)|Optional

</article>
</details>

### Metadata
Metadata is similar to [Custom Fields](/en/core-api/advanced-features.md#custom-fields) which enables you to put **free-form JSON object** instead of String. You can use this metadata as a transaction tag and retrieve it using *Get Status* or *Notification Payload*. Additionally, you can also configure fraud detection rules based on the metadata fields.

<!-- tabs:start -->

#### **JSON Parameters**
The JSON parameter added in the *Request Body* of a [Charge API Request](/en/core-api/credit-card.md#_2-sending-transaction-data-to-charge-api), to include metadata, is shown below.

```json
...
  "metadata": {
	"you": "can",
	"put": "any",
	"parameter": "you like"
   }
...
```
#### **Sample Charge API Request**
The JSON object `metadata`, included in the sample Charge API Request is shown below.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 13000
  },
  "metadata": {
	"you": "can",
	"put": "any",
	"parameter": "you like"
   }
}'
```
<!-- tabs:end -->

<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

The JSON parameter recommended to be included in the Charge API request, to configure metadata, is described in the table given below.

Parameter| Description | Type |Required
--- | --- | --- | ---
metadata | Object containing the metadata parameters|Object|Optional

</article>
</details>

## Credit Card

### 3 Domain Secure (3DS)
Three Domain Secure (3DS) feature can be enabled/disabled for a specific transaction. By default, you **should always enable 3DS**. Please understand the risks involved in disabling 3DS. This will require you to have agreement and approval by the *Acquiring Bank*. Consult Midtrans Activation team to allow disabling 3DS.

<!-- tabs:start -->

#### **JSON Param**
The JSON parameter added in the *Request Body* of a [Charge API Request](/en/core-api/credit-card.md#_2-sending-transaction-data-to-charge-api), to enable 3DS, is shown below.

```json
...
  "credit_card": {
    "token_id": "<token_id from Get Card Token Step>",
    "authentication": true
  }
...
```
#### **Sample Charge API Request**
The JSON attribute ` authentication`, included in the sample Charge API Request is shown below.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 9000
  },
  "credit_card": {
    "token_id": "<token_id from Get Card Token Step>",
    "authentication": true
  }
}'
```
<!-- tabs:end -->

<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

The JSON parameter recommended to be included in the Charge API request, to enable/disable 3DS authentication, is described in the table given below.

| Parameter      | Description                            | Type    | Required | Values                                       |
| -------------- | -------------------------------------- | ------- | -------- | -------------------------------------------- |
| authentication | Flag to enable the 3DS authentication. | Boolean | Optional | True to enable 3DS.<br>False to disable 3DS. |

</article>
</details>

### Routing Transactions to Specific Acquiring Bank
You can specify a preferred *Acquiring Bank* for a specific transaction. Specify the bank name inside `bank` parameter. The transaction fund will be routed to that specific *Acquiring Bank*. Consult Midtrans Activation team to get information about the availability of the *Acquiring Bank*.
<!-- tabs:start -->

#### **JSON Parameters**
The JSON parameter added in the *Request Body* of a [Charge API Request](/en/core-api/credit-card.md#_2-sending-transaction-data-to-charge-api), to route the transaction fund to a specific *Acquiring Bank*, is shown below.

```json
{
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 9000
  },
  "credit_card": {
    "token_id": "<token_id from Get Card Token Step>",
    "authentication": true,
	"bank": "bca"
  }
}
```
#### **Sample Charge API Request**
The JSON attribute `bank`, included in the sample Charge API Request is shown below.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 9000
  },
  "credit_card": {
    "token_id": "<token_id from Get Card Token Step>",
    "authentication": true,
	"bank": "bca"
}'
```
<!-- tabs:end -->

<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

| Parameter | Description                             | Type   | Required | Values                                         |
| --------- | --------------------------------------- | ------ | -------- | ---------------------------------------------- |
| bank      | Name of the preferred *Acquiring Bank*. | String | Optional | mandiri, bni, cimb, bca, maybank, bri or mega. |

</article>
</details>



### Recurring/One Click Transaction
You can allow the customer to save their card credentials for future transactions. This adds to a better customer experience. Midtrans saves the card credentials securely. Store and associate each customer with a unique `saved_token_id` from the Charge API Response received during the first transaction.

<details>
<summary><b>Sequence Diagram</b></summary>
<article>
The Recurring/One Click end-to-end payment process can be illustrated in following sequence diagram.
![one click sequence diagram](../../asset/image/core_api-sequence_one_click.png)
</article>
</details>

#### Retrieving the `token_id`
`token_id` is retrieved from [Getting the Card Token](/en/core-api/credit-card#_1-getting-the-card-token). `token_id` is a representation of customer's card information used for the transaction. Merchant frontend JavaScript securely transmits card information to Midtrans Core API in exchange of card `token_id`. `token_id` should be retrieved using [MidtransNew3ds JS library](https://api.midtrans.com/v2/assets/js/midtrans-new-3ds.min.js). on merchant frontend. This avoids the risk of card information being transmitted to merchant backend.

For more details, refer to [Getting the Card Token](/en/core-api/credit-card#_1-getting-the-card-token).

#### Charge API Request for initial transaction
Additional attributes `token_id` and `save_token_id` are added in `credit_card` object in the *Request Body* during [Charge API Request](/en/core-api/bank-transfer.md?id=charge-api-request).

<!-- tabs:start -->

#### **JSON Parameters**
The JSON parameter added in the *Request Body* of a [Charge API Request](/en/core-api/credit-card.md#_2-sending-transaction-data-to-charge-api), to enable *One Click* transaction, is shown below.

```json
{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 10000
  },
  "credit_card": {
	"token_id": "<token_id from Get Card Token Step>",
	"authentication": true,
	"save_token_id": true     // <-- To flag that token is saved during initial charge
  }
}
```
#### **Sample Charge API Request for the First Transaction**
The JSON attribute `save_token_id`, included in the sample Charge API Request is shown below.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 9000
  },
  "credit_card": {
	"token_id": "<token_id from Get Card Token Step>",
	"authentication": true,
	"save_token_id": true
  }
}'
```
#### **Sample Charge API Response for the First Transaction**
The sample Charge API response for the first transaction is shown below.

```json
{
    "status_code": "201",
    "status_message": "Success, Credit Card transaction is successful",
    "transaction_id": "47df99ca-f997-41bd-864e-8598ccf2fc27",
    "order_id": "Order-123-1578978260",
    "redirect_url": "https://api.sandbox.veritrans.co.id/v2/token/rba/redirect/481111-1114-47df99ca-f997-41bd-864e-8598ccf2fc27",
    "merchant_id": "G816197673",
    "gross_amount": "10000.00",
    "currency": "IDR",
    "payment_type": "credit_card",
    "transaction_time": "2020-01-14 12:04:20",
    "transaction_status": "pending",
    "fraud_status": "accept",
    "masked_card": "481111-1114",
    "bank": "mandiri",
    "card_type": "credit"
}
```

?> ***Note***: The `transaction_status` is *Pending*. <br>The `redirect_url` received in the response is used in [Opening 3DS Authentication Page](#Opening 3DS Authentication Page).

<!-- tabs:end -->

#### Opening 3DS Authentication Page for the First Transaction
To open 3DS authentication page on merchant frontend, display the `redirect_url` retrieved from Charge API response. The redirect URL is displayed using `MidtransNew3ds.authenticate` or `MidtransNew3ds.redirect` function in [MidtransNew3DS JS library](https://api.midtrans.com/v2/assets/js/midtrans-new-3ds.min.js).

 For more details, refer to [Open 3DS Authentication Page JS Implementation](/en/core-api/credit-card?id=open-3ds-authentication-page-js-implementation).

?>***Note***: When the customer completes the transaction on the page, the *Transaction Status* changes from *Pending* to *Capture*.
#### Sample 3DS Authenticate JSON Response for the First Transaction


```json
{
  "status_code": "200"
  "status_message": "Success, Credit Card transaction is successful"
  "transaction_id": "0cc39431-4f74-4605-8b6c-4363822fb398"
  "order_id": "1578977094"
  "merchant_id": "G816197673"
  "gross_amount": "200000.00"
  "currency": "IDR"
  "payment_type": "credit_card"
  "transaction_time": "2020-01-14 11:44:55"
  "transaction_status": "capture"
  "fraud_status": "accept"
  "approval_code": "1578977095472"
  "eci": "05"
  "masked_card": "481111-1114"
  "bank": "mandiri"
  "card_type": "credit"
  "saved_token_id":"481111xDUgxnnredRMAXuklkvAON1114"
  "saved_token_id_expired_at": "2020-12-31 07:00:00"
  "channel_response_code": "00"
  "channel_response_message": "Approved"
}
```
<details>
<summary><b>Response Body JSON Attribute Description</b></summary>
<article>


| Parameter                 | Description                                                  | Type   | Note |
| ------------------------- | ------------------------------------------------------------ | ------ | ---- |
| saved_token_id            | Token ID of a credit card to be charged for recurring transactions. | String | --   |
| saved_token_id_expired_at | Expiry date and time of the Token ID. It is in the format YYYY-MM-DD HH:MM:SS | String | --   |

</article>
</details>
Store the `saved_token_id` in your database for recurring transactions using the same card.

#### Charge API Request for Recurring Transactions

For recurring transactions by the customer, add `saved_token_id` as the value of `token_id` attribute, while sending [Charge API Request](/en/core-api/credit-card.md#_2-sending-transaction-data-to-charge-api).

<!-- tabs:start -->

#### **JSON Parameter**
The JSON parameter added in the *Request Body* of a Charge API Request to allow *One Click* transaction, is shown below.

```json
{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-103",
    "gross_amount": 10000
  },
  "credit_card": {
	"token_id": "481111xDUgxnnredRMAXuklkvAON1114" // <-- saved_token_id from One Click Initial Transaction Response
  }
}
```
#### **Sample Charge API Request for recurring transactions**
The JSON attribute `token_id` included in the sample Charge API Request is shown below.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-103",
    "gross_amount": 10000
  },
  "credit_card": {
	"token_id": "<saved_token_id from One Click Initial Transaction Response>",
  }
}'
```
<!-- tabs:end -->

#### Charge API Response and Notifications for recurring transactions
The Charge API response for recurring transaction on the card is identical with [Card Payment Charge Response](/en/credit-card.md/#sample-response). Successful One Click transaction is flagged as `"transaction_status": "capture"` and is ready for settlement.

#### Sample Charge API Response for recurring transactions

```json
{
  "status_code": "200",
  "status_message": "Success, Credit Card transaction is successful",
  "transaction_id": "139c7a0f-204e-4c88-9c8c-63348b545b99",
  "order_id": "Order-123-1578977940",
  "merchant_id": "G816197673",
  "gross_amount": "10000.00",
  "currency": "IDR",
  "payment_type": "credit_card",
  "transaction_time": "2020-01-14 11:58:59",
  "transaction_status": "capture",
  "fraud_status": "accept",
  "approval_code": "1578977940108",
  "masked_card": "481111-1114",
  "bank": "bni",
  "card_type": "credit",
  "channel_response_code": "00",
  "channel_response_message": "Approved"
}
```

For more use-cases, refer to [One Click, Two click and Recurring Transactions](https://support.midtrans.com/hc/en-us/articles/360002419153-One-Click-Two-Clicks-and-Recurring-Transaction).

### Recurring Transaction with Register Card API
You can allow the customer to save their card credentials for future transactions. Midtrans saves the card credentials securely. You have to store and associate each customer with a unique `saved_token_id` from the Charge API Response received during the first transaction.

<details>
<summary><b>Sequence Diagram</b></summary>
<article>
The overall Register Card API end-to-end payment process can be illustrated in following sequence diagram:


![one click sequence diagram](../../asset/image/core_api-sequence_register_card.png)
</article>
</details>

#### Registering the Card
The card credentials can be saved on Midtrans and `saved_token_id` can be retrieved using MidtransNew3ds JS or Register API request.

<!-- tabs:start -->

#### **MidtransNew3ds JS**
To save card credentials on Midtrans and retrieve card's `saved_token_id`, use `MidtransNew3ds.registerCard` through [MidtransNew3ds JS library](https://api.midtrans.com/v2/assets/js/midtrans-new-3ds.min.js). Implement the following JavaScript on the payment page.
```javascript
// Create the card object with the required fields
var cardData = {
    card_number: "4811111111111114",
    card_cvv: "123",
    card_exp_month: "12",
    card_exp_year: "2025"
};

var options = {
    onSuccess: function(response) {
        // Implement success handling here, save the `saved_token_id` to your database
        console.log('Saved Token ID:',response.saved_token_id);
    },
    onFailure: function(response) {
        // Implement error handling here
        console.log('Fail to get saved card token',response.status_message);
    }
}

MidtransNew3ds.registerCard(cardData, options);


```

#### **Register API Request**

To save card credentials on Midtrans and retrieve card's `saved_token_id`, use `/card/register` API request.

#### Register API Request Details

Method | API Endpoint
--- | ---
GET | `https://api.sandbox.midtrans.com/v2/card/register`

#### Query Parameters

| Parameter      | Description                      | Type   | Note                                       |
| -------------- | -------------------------------- | ------ | ------------------------------------------ |
| card_number    | The card number of the customer. | String | --                                         |
| card_exp_month | The month of expiry on the card. | String | It is in MM format                         |
| card_exp_year  | The year of expiry on the card.  | String | It is in YYYY format.                      |
| client_key     | Your *Client Key*.               | String | It can be retrieved from your MAP account. |

#### Register API Sample Request

```bash
curl -X GET \
  'https://api.sandbox.midtrans.com/v2/card/register?card_number=5211111111111117&card_exp_month=12&card_exp_year=2021&client_key=<YOUR CLIENT KEY HERE>' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json'
```
</article>
</details>

#### Register API Sample Response
A sample response is given below.

```json
{
    "status_code": "200",
    "saved_token_id": "521111nHlLvTuKywNOOLhTlHZcab1117",
    "transaction_id": "cbd3ff55-2ead-43e9-84c5-5c3b7a8a1814",
    "masked_card": "521111-1117"
}
```
<!-- tabs:end -->

Store `saved_token_id` received in the response body, to your database.

#### Getting Card Token for the First Transaction
You need a `saved_token_id` from [Registering the Card](#registering-the-card).

The `token_id` is retrieved using `MidtransNew3ds.getCardToken` on [MidtransNew3ds JS library](https://api.midtrans.com/v2/assets/js/midtrans-new-3ds.min.js). Implement the following JavaScript on the payment page.

```javascript
// card data from customer input, for example
var cardData = {
  "token_id": <saved_token_id from Register Card API Response Step>,
  "card_cvv": 123,
};

// callback functions
var options = {
  onSuccess: function(response){
    // Success to get card token_id, implement as you wish here
    console.log('Success to get card token_id, response:', response);
    var token_id = response.token_id;
    console.log('This is the card token_id:', token_id);
  },
  onFailure: function(response){
    // Fail to get card token_id, implement as you wish here
    console.log('Fail to get card token_id, response:', response);
  }
};

// trigger `getCardToken` function
MidtransNew3ds.getCardToken(cardData, options);
```
For successful transactions, `token_id` is received inside `onSuccess` callback function. It is used as one of the JSON parameters for [`/charge` API request](en/core-api/advanced-features.md#sending-transaction-data-to-charge-api-for-the-first-transaction).

#### Sending Transaction Data to Charge API for the First Transaction
Charge API request is sent from merchant backend to acquire `redirect_url` which will need to open 3DS authentication page. 

<!-- tabs:start -->

#### **JSON Parameters**
The JSON parameters added in the *Request Body* of a Charge API Request are shown below.

```json
{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "order102",
    "gross_amount": 789000
  },
  "credit_card": {
    "token_id": "<token_id from Get Card Token Step>",
    "authentication": true,
  }
}
```
#### **Sample Charge API Request**
```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  	"payment_type": "credit_card",
  	"transaction_details": {
    	"order_id": "order102",
    	"gross_amount": 789000
  	},
  	"credit_card": {
    	"token_id": "<token_id from Get Card Token Step>",
    	"authentication": true,
  	}
}'
```
<!-- tabs:end -->

The parameters that are required for the API Charge request are given below.

| Requirement      | Description                                                  |
| ---------------- | ------------------------------------------------------------ |
| Server Key       | The server key. For more details, refer to [Retrieving API Access Keys](/en/midtrans-account/overview.md#retrieving-api-access-keys). |
| `order_id`       | The order_id of the transaction.                             |
| `gross_amount`   | The total amount of transaction.                             |
| `token_id`       | Represents customer's card information acquired from [Getting Card Token for the first transaction](#getting-card-token-for-the-first-transaction). |
| `authentication` | Flag to enable the 3D secure authentication.                 |

#### Opening 3DS Authentication Page for the First Transaction
To open 3DS authentication page on merchant frontend, display the `redirect_url` retrieved from Charge API response. The redirect URL is displayed using `MidtransNew3ds.authenticate` or `MidtransNew3ds.redirect` function in [MidtransNew3DS JS library](https://api.midtrans.com/v2/assets/js/midtrans-new-3ds.min.js).

For more details, refer to [Opening 3DS Authentication Page JS Implementation](/en/core-api/credit-card#open-3ds-authentication-page-js-implementation).

#### Charge API request For Future Transactions
For any future transaction using the same card credentials, retrieve `saved_token_id` saved on the database from [Registering the Card ](#registering-the-card).
<!-- tabs:start -->

#### **JSON Parameters**
The JSON parameter added in the *Request Body* of a [Charge API Request](/en/core-api/credit-card.md#_2-sending-transaction-data-to-charge-api) is shown below.

```json
{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 10000
  },
  "credit_card": {
	"token_id": "<saved_token_id from Get Card Token Step>"
  }
}
```

#### **Sample Charge API Requests**
The JSON attribute `token_id`, included in the Charge API Request is shown below.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 10000
  },
  "credit_card": {
	"token_id": "<token_id from Get Card Token Step>"
  }
}'
```
<!-- tabs:end -->

### Recurring Transaction with Subscriptions API
[Recurring Transaction with Subscriptions API](https://api-docs.midtrans.com/#recurring-api)

<!-- <TODO: elaborate Subscriptions API> -->

### Two Clicks Transaction
You can allow customer to save their card credentials, except the CVV number, for easier and faster future transactions. Midtrans saves the card credentials securely. You have to store and associate each customer with a unique `saved_token_id` from the initial Charge API Response.

<details>
<summary><b>Sequence Diagram</b></summary>
<article>
The Two Clicks end-to-end payment process is illustrated in following sequence diagram:
![one click sequence diagram](../../asset/image/core_api-sequence_two_clicks.png)
</article>
</details>


To configure *Two Clicks* transaction for a customer, follow the steps given below.

#### Retrieving the `token_id`
 `token_id` is a representation of customer's card information used for the transaction. `token_id` should be retrieved using [MidtransNew3ds JS library](https://api.midtrans.com/v2/assets/js/midtrans-new-3ds.min.js) on merchant frontend. Merchant frontend JavaScript securely transmits card information to Midtrans Core API in exchange of card `token_id`. This avoids the risk of card information being transmitted to merchant backend.

For more details, refer to [Getting the Card Token](/en/core-api/credit-card#_1-getting-the-card-token).

#### Charge API request for the First Transaction
The `token_id` retrieved is added as `save_token_id` attribute in `credit_card` object in the *Request Body* during [Charge API Request](/en/core-api/credit-card.md#_2-sending-transaction-data-to-charge-api).

<!-- tabs:start -->

#### **JSON Parameters**
The JSON parameter added in the *Request Body* of a Charge API Request to allow *Two-Click* transaction, is shown below. 

```json
{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 10000
  },
  "credit_card": {
	"token_id": "<token_id from Get Card Token Step>",
	"authentication": true,
	"save_token_id": true     // <-- To flag that token is saved during initial charge
  }
}
```

#### **Sample Charge API Request For the First Transaction**
The JSON attribute` save_token_id`, included in the sample Charge API Request is shown below.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 10000
  },
  "credit_card": {
	"token_id": "<token_id from Get Card Token Step>",
	"authentication": true,
	"save_token_id": true
  }
}'
```

#### Sample Charge API Response for initial transaction
The Charge API response includes the `redirect_url`.

```json
{
    "status_code": "201",
    "status_message": "Success, Credit Card transaction is successful",
    "transaction_id": "47df99ca-f997-41bd-864e-8598ccf2fc27",
    "order_id": "Order-123-1578978260",
    "redirect_url": "https://api.sandbox.veritrans.co.id/v2/token/rba/redirect/481111-1114-47df99ca-f997-41bd-864e-8598ccf2fc27",
    "merchant_id": "G816197673",
    "gross_amount": "10000.00",
    "currency": "IDR",
    "payment_type": "credit_card",
    "transaction_time": "2020-01-14 12:04:20",
    "transaction_status": "pending",
    "fraud_status": "accept",
    "masked_card": "481111-1114",
    "bank": "mandiri",
    "card_type": "credit"
}
```

?>***Note***: The `transaction_status` is *Pending*.

<!-- tabs:end -->

#### Opening 3DS Authentication Page for initial transaction
To open 3DS authentication page on merchant frontend, display the `redirect_url` retrieved from Charge API Response for the First Transaction. The redirect URL is displayed using `MidtransNew3ds.authenticate` or `MidtransNew3ds.redirect` function in [MidtransNew3DS JS library](https://api.midtrans.com/v2/assets/js/midtrans-new-3ds.min.js).

 When the customer completes the transaction, the *Transaction Status* changes from *Pending* to *Capture*.

 For more details, refer to [Opening 3DS Authentication Page JS Implementation](/en/core-api/credit-card#open-3ds-authentication-page-js-implementation).


Midtrans notifies the merchant backend with the new `transaction status` and `saved_token_id`.

#### Sample Response for 3DS authentication for the First Transaction

```json
{
  "status_code": "200",
  "status_message": "Success, Credit Card transaction is successful",
  "transaction_id": "0cc39431-4f74-4605-8b6c-4363822fb398",
  "order_id": "1578977094",
  "merchant_id": "G816197673",
  "gross_amount": "200000.00",
  "currency": "IDR",
  "payment_type": "credit_card",
  "transaction_time": "2020-01-14 11:44:55",
  "transaction_status": "capture",
  "fraud_status": "accept",
  "approval_code": "1578977095472",
  "eci": "05",
  "masked_card": "481111-1114",
  "bank": "mandiri",
  "card_type": "credit",
  "saved_token_id":"481111xDUgxnnredRMAXuklkvAON1114",
  "saved_token_id_expired_at": "2020-12-31 07:00:00",
  "channel_response_code": "00",
  "channel_response_message": "Approved",
}
```
?>***Note***: Store the `saved_token_id` to your database.

<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

| Parameter                 | Description                                                  | Type   |
| ------------------------- | ------------------------------------------------------------ | ------ |
| saved_token_id            | Token ID of a credit card to be charged for recurring transactions from the customer. | String |
| saved_token_id_expired_at | Expiry date of the Token ID                                  | String |

</article>
</details>

#### Getting Card Token For Future Transactions
The `saved_token_id` from Response for 3DS authentication for the First Transaction is used in this step.

To retrieve card `token_id`, use `MidtransNew3ds.getCardToken` function. Implement the following JavaScript on Midtrans payment page.
```javascript
// card data from customer input, for example
var cardData = {
  "token_id": <saved_token_id from Two Clicks Initials Charge Response>,
  "card_cvv": 123,
};

// callback functions
var options = {
  onSuccess: function(response){
    // Success to get card token_id, implement as you wish here
    console.log('Success to get card token_id, response:', response);
    var token_id = response.token_id;
    console.log('This is the card token_id:', token_id);
  },
  onFailure: function(response){
    // Fail to get card token_id, implement as you wish here
    console.log('Fail to get card token_id, response:', response);
  }
};

// trigger `getCardToken` function
MidtransNew3ds.getCardToken(cardData, options);
```
?>***Note***: You need `saved_token_id` retrieved from database.<br>For successful transactions, `token_id` is received inside `onSuccess` callback function. It will be used as one of the JSON parameters for [`/charge` API request](en/core-api/credit-card.md#_2-sending-transaction-data-to charge-api)

### BIN (Bank Identification Number) Filter
BIN (Bank Identification Number) filter is a feature that allows the merchant to accept credit cards within specific set of BIN numbers. It is useful for certain bank promotions or discount payments, by accepting only the credit cards issued by that bank. BIN is the six digits of the card number that identifies the bank, issuing the card. Generally, a bank has more than one BIN.

To use this feature, accumulate the list of BIN that accepts the promotion or uses the issuing bank's name. This transaction can be performed exclusively by using the credit card that is included in the BIN list or BIN under the particular defined issuing bank.
<!-- tabs:start -->

#### **JSON Parameters**
The JSON parameters added in the *Request Body* of a [Charge API Request](en/core-api/credit-card.md#_2-sending-transaction-data-to charge-api) to allow BIN filter, are shown below.

```json
{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 120000
  },
  "credit_card": {
    "token_id": "<token_id from Get Card Token Step>",
    "authentication": true,
    "bank": "bni",
    "bins": ["48111111", "bni", "5"]
  }
}
```
#### **Sample Charge API Request**

The JSON attribute `bank` and `bins` included in the sample Charge API Request are shown below.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 120000
  },
  "credit_card": {
    "token_id": "<token_id from Get Card Token Step>",
    "authentication": true,
    "bank": "bni",
    "bins": ["48111111", "bni", "5"]
  }
}'
```
<!-- tabs:end -->

?> ***Note***: By default, Midtrans populates BIN number for BNI, Mandiri, CIMB, BCA, and other partner banks. You can add the bank name as `bins` value.

### Installment Payment
#### Online Installment

*Online Installment* is the type of payment where *Card Issuing Bank* used for making an installment payment and the *Acquiring Bank* are the same. For example, a customer makes an installment payment using BNI Card and the *Acquiring Bank* is also BNI.

You should have agreements with the bank to activate the installment feature. For *Online Installment*, the bank will issue special installment Merchant ID (MID). This installment MID is used to automatically convert the transaction into installments. Please consult Midtrans Activation Team for installment MID. If MID is ready, add the installment parameter.

<!-- tabs:start -->

#### **JSON Parameters**
The JSON parameter added in the *Request Body* of a [Charge API Request](en/core-api/credit-card.md#_2-sending-transaction-data-to charge-api) to allow *Online Installment*, is shown below.

```json
{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 120000
  },
  "credit_card": {
    "token_id": "<token_id from Get Card Token Step>",
    "authentication": true,
    "bank": "bni",
    "installment_term": 3
  }
}
```
#### **Sample Charge API Response**
The JSON attribute `installment_term`, included in the sample Charge API Request is shown below.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 120000
  },
  "credit_card": {
    "token_id": "<token_id from Get Card Token Step>",
    "authentication": true,
    "bank": "bni",
    "installment_term": 3
  }
}'
```
<!-- tabs:end -->

<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

| Parameter        | Description                                                  | Type    | Required |
| ---------------- | ------------------------------------------------------------ | ------- | -------- |
| token_id         | Represents customer's credit card information acquired from [Get Card Token Response](/en/core-api/credit-card.md#get-card-token-response). | String  | Required |
| authentication   | Flag to enable the 3DS authentication.                       | Boolean | Required |
| bank             | The name of the *Card Issuing Bank* or *Acquiring Bank*. <br>Else, it will be treated as [Offline Installment](/en/core-api/advanced-features.md#offline-installment). | String  | Optional |
| installment_term | The tenor of installment.                                    | Integer | Required |

</article>
</details>

#### Offline Installment
*Offline Installment* is the type of payment where *Card Issuing Bank* used for making an installment payment and the *Acquiring Bank* are not the same. For example, a customer makes an installment payment using BNI Card and the *Acquiring Bank* is Mandiri.

You can use *Offline Installment* feature to allow installment feature with banks which do not issue MID. With offline installment feature, initially the transaction will be charged in full amount and later it will be converted into installments. Please consult Midtrans Activation Team for installment agreements.
This is the type of Installment where the Card Issuer and Acquiring Bank don't have to be same entity, for example BNI Card and Mandiri Acquiring Bank).


<!-- tabs:start -->

#### **JSON Parameters**
The JSON parameters added in the *Request Body* of a [Charge API Request](en/core-api/credit-card.md#_2-sending-transaction-data-to charge-api) to allow *Offline Installment*, are shown below.

```json
{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 120000
  },
  "credit_card": {
    "token_id": "<token_id from Get Card Token Step>",
    "authentication": true,
    "installment_term": 12,          
    "bins": ["48111111", "3111", "5"]
  }
}
```
#### **Sample Charge API Request**
The JSON attribute `installment` with `bins` filter feature included in the Charge API Request, are shown below. The purpose of `bins` filter is to limit certain cards from being allowed to do offline installment, based on the agreement between you and issuing banks.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 120000
  },
  "credit_card": {
    "token_id": "<token_id from Get Card Token Step>",
    "authentication": true,
    "installment_term": 12,
    "bins": ["48111111", "3111", "5"]
  }
}'
```
<!-- tabs:end -->

<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

Parameter | Description |Type|Required
--- | --- | --- | ---
token_id | Represents customer's credit card information acquired from [Get Card Token Response](/en/core-api/credit-card.md#get-card-token-response). |String|Required
authentication | Flag to enable the 3D secure authentication.|Boolean|Required
installment_term | The tenor of installment. |Integer|Required
bins | List of credit card's BIN (Bank Identification Number) that is allowed for transaction. |Array|Required

</article>
</details>

### Pre-Authorization Payment
*Pre-Authorization* payment feature will temporarily block the fund from the customer's account. The fund is not immediately deducted after the transaction. You can initiate "capture" action through [Capture API](https://api-docs.midtrans.com/#capture-transaction). By default, fund reservation will be released after 7 days if there is no "capture" action for that transaction.
<!-- tabs:start -->

#### **JSON Parameters**
The JSON parameter added in the *Request Body* of a [Charge API Request](en/core-api/credit-card.md#_2-sending-transaction-data-to charge-api) to pre-authorize a payment, is shown below.

```json
{
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 9000
  },
  "credit_card": {
    "secure": true,
    "authentication": true,
    "type": "authorize"
  }
}
```
#### **Sample Charge API Request**
The JSON attribute`"type": "authorize"` is included in the sample Charge API Request is shown below.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic <YOUR SERVER KEY ENCODED in Base64>' \
  -H 'Content-Type: application/json' \
  -d '{
  "payment_type": "credit_card",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 9000
  },
  "credit_card": {
    "token_id": "<token_id from Get Card Token Step>",
    "authentication": true,
    "type": "authorize"
  }
}'
```
<!-- tabs:end -->

<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

Parameter | Type | Description |Required|Note
--- | --- | --- | --- | ---
token_id | String | Represents customer's credit card information acquired from [Get Card Token Response](/en/core-api/credit-card.md#get-card-token-response). |Required|--
authentication | Boolean | Flag to enable the 3D secure authentication.|Required|--
type | String | Attribute to enable the pre-authorization feature. |Required|Valid value `authorize`.

</article>
</details>

## Credit Card - Full PAN

[Credit Card - Full PAN](https://api-docs.midtrans.com/#credit-card-full-pan)

<!-- <TODO: elaborate Full PAN> -->

## GoPay
### Redirecting Customer from the Gojek App
After completing payment using GoPay payment method, by default, the customer will remain on Gojek app. They need to manually close Gojek app to switch back to merchant website or application. `gopay.callback_url` parameter will allow customers to be automatically redirected from the Gojek app to the merchant website/application.
<!-- tabs:start -->

#### **JSON Parameters**
The JSON parameter added in the *Request Body* of a Charge API Request, to redirect the customer is shown below.

```json
{
  "payment_type": "gopay",
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 9000
  },
  "gopay": {
    "enable_callback": true,
    "callback_url": "https://tokoecommerce.com/finish"
  }
}
```
#### **Sample Charge API Request**
The JSON attribute `callback_url` included in the sample Charge API Request is shown below.

```bash
curl -X POST \
  https://api.sandbox.midtrans.com/v2/charge \
  -H 'Accept: application/json'\
  -H 'Authorization: Basic U0ItTWlkLXNlcnZlci1UT3ExYTJBVnVpeWhoT2p2ZnMzVV7LZU87' \
  -H 'Content-Type: application/json' \
  -d '{
  "transaction_details": {
    "order_id": "CustOrder-102",
    "gross_amount": 9000
  },
  "gopay": {
    "enable_callback": true,
    "callback_url": "https://tokoecommerce.com/finish"
  }
}'
```
<!-- tabs:end -->

<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

| Parameter       | Description                                 | Type    | Required | Values                                                       |
| --------------- | ------------------------------------------- | ------- | -------- | ------------------------------------------------------------ |
| enable_callback | Flag to enable or disable callback_url      | Boolean | Required | `true` to enable.<br>`false` to disable.                     |
| callback_url    | The URL to which the customer is redirected | String  | Required | Use http/https URL protocol for websites, or Deeplink protocol for mobile applications. |

</article>
</details>

The final redirect URL is appended with query parameters such as `order_id`, `result=xxx`.

| Redirect URL                           | Final Redirect URL                                           |
| :------------------------------------- | ------------------------------------------------------------ |
| https://tokoecommerce.com/gopay_finish | https://tokoecommerce.com/gopay_finish/?order_id=CustOrder-102123123&result=success |

| Query Parameter | Type   | Description                                                  | Value                   |
| --------------- | ------ | ------------------------------------------------------------ | ----------------------- |
| order_id        | String | Order ID sent on the Charge Request.                         | --                      |
| result          | String | Result of the transaction to decide what kind of page to show to customer. | `success` or `failure`. |

?> ***Note***: You may use the information to display custom message to your customer on your finish URL.

## Bank Transfer/VA
### Specifying Custom VA Number and VA Description
Midtrans creates random VA number for transactions using *Bank Transfer* payment method. In some cases, you can customize the VA number. You can do that with the following parameters.
<!-- tabs:start -->

####  **BCA**

##### JSON Parameters
The JSON parameters added in the *Request Body* of a Charge API Request, are shown below.

```json

...
   "bank_transfer":{
     "bank": "bca",
     "va_number": "111111",
     "free_text": {
          "inquiry": [
                {
                    "id": "Free Text ID Free Text ID Free Text ID",
                    "en": "Free Text EN Free Text EN Free Text EN"
                }
          ],
          "payment": [
               {
                    "id": "Free Text ID Free Text ID Free Text ID",
                    "en": "Free Text EN Free Text EN Free Text EN"
                }
          ]
     },
     "bca": {
        "sub_company_code": "00000"
     }
   }
...
```
<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

Parameter| Description | Type |Required|Note
--- | --- | --- | --- | ---
bank | The name of the bank which processes the transaction. |String (255)|Required|--
va_number | Custom VA number assigned by you. |String|Optional|Minimum Length: 1<br>Maximum length: 11
inquiry	| Texts to be displayed on ATM when the customer attempts to enquire the VA number. |Array (10)|Optional|--
Id	| Text message in Bahasa Indonesia. |String (50)|Required|--
En | Text message in English. |String (50)|Required|--
payment | Texts to be displayed on ATM when the customer attempts to make payments. |Array (10)|Optional|--
sub_company_code | BCA sub company code directed for this transactions. |String|Optional|Default value is 00000.

</article>
</details>

#### **BNI**

##### JSON Parameters
The JSON parameters added in the *Request Body* of Charge API Request, are shown below.

```json
...
  "bank_transfer":{
     "bank": "bni",
     "va_number": "111111"
  }
...
```
<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

Parameter| Description                                                  | Type |Required|Note
--- | --- | --- | --- | ---
bank | The name of the bank which processes the transaction using Bank Transfer payment method. |String (255)|Required|--
va_number | Custom VA number assigned by merchant. |String (255)|Optional|Minimum length:1<br>Maximum length:8

</article>
</details>

#### **Mandiri Bill**

##### JSON Parameters
The JSON parameters added in the *Request Body* of Charge API Request, are shown below.

```json
...
	"echannel" : {
	    "bill_info1" : "Payment For:",
	    "bill_info2" : "Tuition fee",
	    "bill_info3" : "Name:",
	    "bill_info4" : "Budi Utomo",
	    "bill_info5" : "Class:",
	    "bill_info6" : "Computer Science",
	    "bill_info7" : "ID:",
	    "bill_info8" : "VT-12345"
	}
...
```
<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

Parameter| Description |Type|Required|Note
--- | --- | --- | --- | ---
bill_info1 | Label 1 |String|Required|Maximum length: 10.<br/>Exceeding characters will be truncated.
bill_info2 | Value for Label 1 |String|Required|Maximum length: 30<br/>Exceeding characters will be truncated.
bill_info3 | Label 2 |String|Optional|Maximum length: 10 <br/>Exceeding characters will be truncated.
bill_info4 | Value for Label 2 |String|Optional|Maximum length: 30<br/>Exceeding characters will be truncated.
bill_info5 | Label 3 |String|Optional|Maximum length: 10<br/>Exceeding characters will be truncated.
bill_info6 | Value for Label 3 |String|Optional|Maximum length: 30<br/>Exceeding characters will be truncated.
bill_info7 | Label 4 |String|Optional|Maximum length: 10<br/>Exceeding characters will be truncated.
bill_info8 | Value for Label 4 |String|Optional|Maximum length: 30<br/>Exceeding characters will be truncated.

</article>
</details>

#### **Permata**

##### JSON Parameters

The JSON parameters added in the *Request Body* of a Charge API Request, are shown below.

```json
...
	"bank_transfer":{
	  "bank": "permata",
	  "va_number": "0123456789",
	  "permata": {
	    "recipient_name": "SUDARSONO"
	  }
	}
...
```
<details>
<summary><b>POST Body JSON Attribute Description</b></summary>
<article>

 Parameter | Description | Type |Required|Note
--- | --- | --- | --- | ---
bank | The name of the bank which processes the *Bank Transfer* transaction. |String (255)|Required|--
va_number | Custom VA number assigned by the merchant. |String (10)|Optional|Length should be equal to 10. <br>Only supported for B2B VA type.
recipient_name | The name of the recipient shown in the payment details.<br> |String (20)|Optional|Default value is your name.

</article>
</details>

<!-- tabs:end -->

Virtual Account number displayed to customer contains two parts; the company code and the  unique code. The table given below, explains this with an example.

| Virtual Account Number | Company Code | Unique Code  |
| ---------------------- | ------------ | ------------ |
| `{91012}{12435678}`    | `{91012}`    | `{12435678}` |

The unique code can be customized. 

Rules for customizing Virtual Account number is given below.

* Only digits are allowed.
* Different banks have different specifications on their custom VA numbers. Please see the documentation of the respective banks.
* If the number provided is already utilized for another order, then a unique number will be used instead.
* If the number provided is longer than required, then the unnecessary digits in the end will be truncated.
* If the number provided is shorter than required, then the number will be prefixed with zeros.

?>***Note***: In *Production* environment, all banks do not support custom VA number. It depends on the agreement. Please consult with Midtrans Activation team for further information.

## Consideration and Limitations
There are a few limitations to consider while using Midtrans API. These limitations are given below.

### 1. Maximum Request Size Limit
Midtrans API allows a maximum size of 16kb or 16000 total characters per request. Please try to keep it under the limit to avoid request failures.

?>***Tips***: Limit the number of `item_details` from your request, or group it into fewer `item_details`.

### 2. Card Token ID Expiry Time
For regular card transactions, the `token_id` (for non-recurring, non-one-click, non-two-click token) and the  3DS `redirect_url` expires in **10 minutes**.

For security reasons, it is designed to generate a unique `token_id` for each transaction. Please make sure to complete the card transaction within the time limit to avoid expired `token_id`.


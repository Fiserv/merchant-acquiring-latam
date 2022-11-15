# Payment URL

**/payment-url**

Payment URL is a functionality that allows you to provide a link to your customers (e.g. in an email invoice, WhatsApp message, SMS, QR code, etc. which then takes the customer to a Fiserv-hosted page to securely make the payment with their preferred payment method, whenever convenient for them.

This is especially useful in scenarios where goods get paid after delivery, where no goods get shipped at all (e.g. final payment for trips that have been booked months ago) or for the payment of monthly bills.

You can also implement this functionality for unsuccessful purchases where the original payment transaction has been declined so that you can proactively give your customer a second chance to make their purchase.

The Gateway provides

- The capability to request a Payment URL (link) for a specific amount through API

- A hosted payment page where the customer can select the preferred payment method (based on the payment methods that are activated for your account) and make the payment

- A hosted result page that tells the customer if the payment was successful or not, including a Retry button where the customer can chose a different payment method in case the transaction was not successful

## Creating a Payment URL
Use POST to make a call to /payment-url and specify the values for the payload as defined in the following table.

|**Attribute**|	**Explanation**|
|```transactionType```	|this attribute tells our platform what type of transaction to execute when the customer completes the payment via the URL. To take a payment, use SALE. To create a pre-authorization, use PREAUTH. To credit the customer, use CREDIT.|
|```transactionNotificationURL```	|Set the URL to which you would like notification posted when the payment has been completed by the customer|
|```expiration```	|This is the date on which the URL will expire and no longer be useable by the customer|
|```authenticateTransaction```	|set to TRUE to have the transaction authenticated by 3-D Secure (this will happen within our hosted page, not via the REST API driven 3-D Secure flow)|
|```dynamicMerchantName```	|This sets the merchant name that will appear on the customers card statement, so you can set this to whatever you want to appear there.|
|```invoiceNumber```|	Put your invoice number here.|
|```purchaseOrderNumber```	|Put the customers Purchase Order number here.|
|```hostedPaymentPageText```	|This sets the text that will appear on the hosted payment page that the customer uses to make payment|

The example below creates a URL for a sale payment to send to a customer.

```json
{
  "transactionAmount": {
    "total": "42.42",
    "currency": "EUR"
  },
  "transactionType": "SALE",
  "transactionNotificationURL": "https://mywebshop/Customer",
  "expiration": "4102358400",
  "authenticateTransaction": true,
  "dynamicMerchantName": "MyWebsite",
  "invoiceNumber": "96126098",
  "purchaseOrderNumber": "123055342",
  "hostedPaymentPageText": "Dear Customer, please pay our invoice 123456. "
}
```

The sample generator below shows the associated details for the /payments-url API.

```json
{
  "method": "post",
  "url": "https://prod.api.firstdata.com/ipp/payments-gateway/v2/payment-url",
  "headers": {
    "Content-Type": "application/json",
    "Client-Request-Id": "",
    "Api-Key": "",
    "Timestamp": "",
    "Message-Signature": ""
  },
  "body": {
    "transactionAmount": {
      "total": "42.42",
      "currency": "USD"
    },
    "transactionType": "SALE",
    "transactionNotificationURL": "https://mywebshop/notification",
    "expiration": "4102358400",
    "authenticateTransaction": true,
    "dynamicMerchantName": "MyWebsite",
    "invoiceNumber": "96126098",
    "purchaseOrderNumber": "123055342",
    "hostedPaymentPageText": "Dear Customer, please pay our invoice 123456."
  }
}
```

Other Payment URL functions
To delete a Payment URL, add your ```storeId``` and the ```transactionId``` from the Payment URL creation request response (```ipgTransactionId```) to the /payment-url header, and use the DELETE method to call the /payment-url API.

You can retrieve the data associated with a payment URL by sending a GET to /paymentURL. Add ```storeId``` and the ```transactionId``` from the Payment URL creation request response (```ipgTransactionId```) to the /payment-url header to retrieve the details for a specific Payment URL, or set ```storeId```, ```fromDate``` and ```toDate``` to call a response with all Payment URLs and their details created within a specific time range.

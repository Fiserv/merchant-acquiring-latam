# Currency Conversion

Use our Currency Conversion services to offer your customers the ability to pay in different currencies, typically their own domestic currency when ordering from overseas.

## Currency Conversion Types

We provide 2 types of Currency Conversion, one in which you'll request the optimal currency and rate from our exchange rate provider, who will then determine which currency to provide a price and exchange rate in (a DCC Exchange Rate Request), and another in which you'll be provided with a list of currencies and prices. You can then choose certain prices and currencies to present to the customer, or customer can select the currency they would like to pay in (a Dynamic Pricing Exchange Rate Request).

## Using Currency Conversion

To use our currency conversion services, use the POST method to ``/exchange-rates`` to request a price and exchange rate from our exchange rate providers. As with our other services, this resource is polymorphic. This means you'll need to submit a request type to tell the Exchange Rates resource how to treat your request.

|**Currency Conversion Type**	|**requestType**|	**Currency Conversion Scenario**|
|---------------------------|----------|---------------------------------|
|Exchange Rate Request	|DCCExchangeRateRequest	|Use this requestType to request a currency, price and exchange rate for a specific transaction, applicable to the customer for which you are requesting a rate.|
|Dynamic Pricing Request	|DynamicPricingExchangeRateRequest	|Use this requestType to request all available currencies and rates for a transaction.|

## Payloads

### Exchange Rate Request

To request a specific rate for a customer, use a POST method against the ```/exchange-rates``` resource as per the sample payload below:

```json
{
  "requestType": "DCCExchangeRateRequest",
  "baseAmount": "12.32",
  "bin": "411111"
}
```

The BIN value is important as this tells the exchange rate provider the home currency of the customer's card, which enables them to provide a rate and price tailored to that customer. The BIN value is the first 6 digits of the customer's card number.

The response from the ```/exchange-rates``` resource will present as follows:

```json
{
  "clientRequestId": "30dd879c-ee2f-11db-8314-0800200c9a66",
  "apiTraceId": "rrt-0bd552c12342d3448-b-ea-1142-12938318-7",
  "requestTime": 1592912760,
  "exchangeRateDetails": {
    "inquiryRateId": 49150,
    "foreignCurrency": "NOK",
    "foreignAmount": 130.33,
    "exchangeRate": 10.2968,
    "dccOffered": "true",
    "exchangeRateSourceTimestamp": "2015-06-23T13:46:00.000+02:00",
    "expirationTimestamp": "2015-06-23T13:46:00.000+02:00",
    "marginRatePercentage": "3",
    "exchangeRateSourceName": "REUTERS WHOLESALE INTERBANK"
  }
}
```

To use this rate in a transaction, include the ```currencyConversion``` object in the ```/payments``` POST request as follows, using the ```inquiryRateId``` from the response to the ```/exchange-rates``` POST request. Use the value and currency from the ```/exchange-rates``` POST response in the ```transactionAmount``` object, and set the ```conversionType``` to "DCC".

```json
{
  "requestType": "PaymentCardSaleTransaction",
  "transactionAmount": {
    "total": "130.33",
    "currency": "NOK"
  },
  "paymentMethod": {
    "paymentCard": {
      "number": "5424180279791732",
      "securityCode": "977",
      "expiryDate": {
        "month": "12",
        "year": "24"
      }
    }
  }
  "currencyConversion": {
    "conversionType": "Dcc",
    "inquiryRateId": "49150",
    "dccApplied": true
  }
}
```

### Dynamic Pricing

To request all available rates and currencies for your transaction, make a POST method request using the ```dynamicPricingExchangeRateRequest``` requestType.

```json
{
  "requestType": "DynamicPricingExchangeRateRequest",
  "baseAmount": "12.32",
  "foreignCurrency": "USD"
}
```

If successful, a response will be generated as follows, including the amount and the relevant ISO Currency Code for the currency to which the transaction amount has been translated.

```json
{
  "conversionType": "DynamicPricing",
  "inquiryRateId": "49151",
  "foreignCurrency": "978",
  "foreignAmount": "22.52"
}
```

To use this rate in a transaction, include the ```currencyConversion``` object in the ```/payments``` POST request as follows, using the ```inquiryRateId``` from the response to the ```/exchange-rates``` POST request. Use the value and currency from the ```/exchange-rates``` POST response in the ```transactionAmount``` object, and set the ```conversionType``` to "DynamicPricing".

```json
{
  "requestType": "PaymentCardSaleTransaction",
  "transactionAmount": {
    "total": "22.52",
    "currency": "EUR"
  },
  "paymentMethod": {
    "paymentCard": {
      "number": "5424180279791732",
      "securityCode": "977",
      "expiryDate": {
        "month": "12",
        "year": "24"
      }
    }
  }
  "currencyConversion": {
    "conversionType": "DynamicPricing",
    "inquiryRateId": "49151",
    "dccApplied": true
  }
}
```

---

## See Also

- [Request Types](?path=docs/3-1-request-types.md)
- [Payment Methods](?path=docs/3-2-payment-methods.md)
- [Payment Types](?path=docs/3-3-payment-types.md)
- [Post-authorisation & Returns](?path=docs/3-4-post-auth.md)
- [3-D Secure](?path=docs/3-5-3d-secure.md)
- [Card Verification](?path=docs/3-6-card-verification.md)
- [Managed Redirect](?path=docs/3-8-managed-redirect.md)
- [Orders](?path=docs/3-9-orders.md)
- [Payment URL](?path=docs/3-10-payment-url.md)
- [Recurring Payments](?path=docs/3-11-recurring-payments.md)
- [Tokenisation](?path=docs/3-12-tokenisation.md)
- [Error codes](?path=docs/3-13-error-codes.md)

---


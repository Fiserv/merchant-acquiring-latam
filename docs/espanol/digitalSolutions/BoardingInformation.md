
# Información de embarque


¡Bienvenido a nuestra documentación de soporte de API!

Para una breve introducción de&nbsp;cómo usar la APIS, acceda a nuestra [introducción](?path=docs/español/digitalSolutions/APIs-Introduction.md).

A continuación puede consultar cada enlace para acceder al documento detallado de cada servicio web (API), para que pueda desarrollar e implementar su negocio.

[Online Boarding and Status](../api/?type=post&path=/api/proposal)

[Online Boarding and Status - Boarding New Proposals](../api/?type=post&path=/api/proposal1/v3)

[Check Proposal Status](../api/?type=get&path=/api/proposal2/{proposalNumber})

[Declare Payment - Used for Device Sales](../api/?type=post&path=/api/payment/report)

[Verify Tax ID (CNPJ for company) at SERPRO](../api/?type=get&path=/api/serpro/cnpj/{cnpj})

[Verify Tax ID (CPF for individual) at SERPRO](../api/?type=get&path=/api/serpro/cpf/{cpf})

[Service Contract Parameters. It is an internal code used in Fiserv to identify the Partner](../api/?type=get&path=/config/service-contract)

[Acount Fees for Required Service Parameters (accountFees)](../api/?type=get&path=/config/account-fees/{serviceContract})

[Associations/Schemas Product Code for Settlement Parameters](../api/?type=get&path=/config/bank-accounts/{serviceContract})

[Associations/Schemas Product Code for Settlement Parameters with prepayment enable value](../api/?type=get&path=/config/bank-accounts/{serviceContract}/prepayment)

[List of Banks for Settlement to be used during boarding](../api/?type=get&path=/config/bank)

[List of CNAEs Parameter for Boarding](../api/?type=get&path=/config/cnae/{institution})

[Returns an object containing Merchant category identification code](../api/?type=get&path=/config/mcc/{institution}/{cnae-number})

[Returns the object 'ApiResult' with the status of professional license](../api/?type=get&path=/config/professional-license/{service-contract})

[Restricted/Unwanted CNAEs for Boarding](../api/?type=get&path=/config/restricted-cnae)

[MDR Service Fees Parameters (Standard Fees, for reference only)](../api/?type=get&path=/config/fees/{serviceContract})

[Associations/Schemas List](../api/?type=get&path=/config/acquisition/{serviceContract})

[Additional Services Parameters](../api/?type=get&path=/config/additional-services/{serviceContract})

[Frequency Cycles for Additional Services](../api/?type=get&path=/config/frequencies/{serviceContract})

[Capture Solutions Parameters](../api/?type=get&path=/config/capture-solution/{serviceContract})

[Phone Operators Parameters](../api/?type=get&path=/config/mobile-operator)

[Merchant - Compliance (Not Available)](../api/?type=get&path=/config/compliance/merchantId/{merchantId})

[List of Campaign Setup](../api/?type=get&path=/config/campaigns/simulator)

[Range of Revenue for the Campaign](../api/?type=get&path=/config/campaigns/billing-range/id-campaign/{id-campaign})

[List of Campaign Setup](../api/?type=get&path=/config/campaigns/factor-flex/id-campaign/{id-campaign})

[List of Campaign Setup - Get the Factor fees for MDR Flex associated to a campaign](../api/?type=get&path=/config/campaigns/factor-flex/billing-value/id-campaign/{id-campaign})

[List of Campaign Setup - Get the MDR Flex Fees associated to a campaign](../api/?type=get&path=/config/campaigns/mdr-flex/id-campaign/{id-campaign})

[List of Campaign Setup - Get the MDR Flex Fees associated to a campaign - Billing Value](../api/?type=get&path=/config/campaigns/mdr-flex/billing-value/id-campaign/{id-campaign})

[List of Campaign Setup - Get MDR Fees for a given campaign](../api/?type=get&path=/config/campaigns/mdr/id-campaign/{id-campaign})

[List of Campaign Setup - Get the MDR Fees associated to a campaign](../api/?type=get&path=/config/campaigns/mdr/billing-value/id-campaign/{id-campaign})

[List of Campaign Setup - Get the current campaign approvers](../api/?type=get&path=/config/campaigns/current-approvers/id-campaign/{id-campaign})

[List of Campaign Setup - Get possible approvers for a campaign](../api/?type=get&path=/config/campaigns/approvers/service-contract/{service-contract})

[List of Campaign Setup - Get the Business Point associated to a campaign - Billing value](../api/?type=get&path=/config/campaigns/business-point/billing-value/id-campaign/{id-campaign})

[List of Campaign Setup - Get the Business Point associated to a campaign](../api/?type=get&path=/config/campaigns/business-point/id-campaign/{id-campaign})

[List of Campaign Setup - Get the technology price discount fee associated to a campaign](../api/?type=get&path=/config/campaigns/technology-price-discount-fee/billing-value/id-campaign/{id-campaign})

[List of Campaign Setup - Get the Premium Rate according to the State/Servicecontract](../api/?type=get&path=/config/campaigns/premium-uf/service-contract/{service-contract})

[List of Campaign Setup - Get PrePayment Fees for Campaign](../api/?type=get&path=/config/campaigns/prepayment/id-campaign/{id-campaign})

[List of Campaign Setup - Get PrePayment Fees for Campaign V2](../api/?type=get&path=/config/campaigns/prepayment/billing-value/id-campaign/{id-campaign})

[List of Campaign Setup - Get Device Prices associated to a Campaign](../api/?type=get&path=/config/campaigns/pricing-technology/id-campaign/{id-campaign})

[List of Campaign Setup - Get the Available Campaigns](../api/?type=get&path=/config/campaigns/service-contract/{service-contract})

[List of Campaign Setup -  Return the JSON with a model of Fees to be sent](../api/?type=post&path=/config/proposal/build-fees)

[List of Setup to Send Proposal - Get the Proposal Status](../api/?type=get&path=/config/proposal/status:)

[List of Setup to Send Proposal -  Return the JSON with a model of Fees to be sent](../api/?type=post&path=/config/proposal/build-fees/v2)

[Proposal Status - Consult (Out of Online Boarding)](../api/?type=get&path=/bwa/proposta/status/{inst}/{doc})

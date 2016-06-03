Contents
<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Introduction](#introduction)
- [Billing operations](#billing-operations)
- [Payments](#payments)
- [Zuora 360](#zuora-360)
- [Zuora APIs](#zuora-apis)
	- [SOAP Snippets](#soap-snippets)
		- [Login](#login)
		- [Get product rate plan Id from product](#get-product-rate-plan-id-from-product)
		- [Create an amendment in subscription associated with an account](#create-an-amendment-in-subscription-associated-with-an-account)
		- [Get query used to create an export from UI](#get-query-used-to-create-an-export-from-ui)
		- [Create new export](#create-new-export)
- [Useful links](#useful-links)

<!-- /TOC -->

# Introduction

* Product - the thing being sold
* Rate plan - associated with a product; defines the product plan, rates etc
* Account - every user who pays for a product has an account
* Subscription - links an account to one or more products
* Product features - products can have features, which defines what additional
'things' the user gets, example a tablet with a mobile data plan
* When organizing products/product bundles, consider how the products appear
  - on website - pricing page
  - invoices
  - finance reports

# Billing operations

* Target date vs Invoice date vs Bill cycle date    
Start of subscription = 1 Jan 2016     
Bill cycle date = 1 Jan 2016    
Target date = 20 Jan 2016    
Invoice date = 25 Jan 2016    
Invoice received on 27 Jan (2 days in post) will be for £0    
Invoice received on 27 Feb will be for 1 jan to 1 feb amount
* Bill runs can be scheduled or run on an ad-hoc basis
* 0 is a valid authorization amount, depending on the payment gateway
  - authz amount is reversed, typically, within 48 hours

# Payments

* Payment runs are also scheduled based on bill run scheduled
    - Payment errors can be seen in the payments section associated with an
    account
    - Also visible under reporting section. Reporting -> Data Exports
* [Payment method updater](https://knowledgecenter.zuora.com/CB_Billing/L_Payment_Methods/D_Payment_Method_Updater)
    - Handles updates to customer payment method information, example new card
    numbers when the previous expires
    - Only available with certain gateways
    - Payment gateways usually charge merchants for this service

# Zuora 360

* Salesforce managed and unmanaged packages
* Usually 5 events when a subscription is created
  - Subscription
  - Account
  - Payment method / information
  - Invoice
  - ...

# Zuora APIs

## SOAP Snippets

### Login

    <SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns2="http://object.api.zuora.com/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns1="http://api.zuora.com/">
        <SOAP-ENV:Body>
            <ns1:login>
                <ns1:username>anurag.kapur@ft3.test</ns1:username>
                <ns1:password>xxxx</ns1:password>
            </ns1:login>
        </SOAP-ENV:Body>
    </SOAP-ENV:Envelope>

### Get product rate plan Id from product

    <x:Envelope xmlns:x="http://schemas.xmlsoap.org/soap/envelope/" xmlns:api="http://api.zuora.com/">
        <x:Header>
            <api:QueryOptions>
                <api:batchSize/>
                <api:caseSensitive/>
            </api:QueryOptions>
            <api:SessionHeader>
                <api:session>oLxisFxem29I_gyqAceKOui0cwHBjx7hZ-84bPolefq6RycQ2bw3kI6QZWM7jeuZ4TXf-wQgyeyu7JibbAXMQHRRD_rk89shm52JRMG3itZ8k9sLh236qrJbKhc0N-CJFcUT7jbeVXK4vqyppUVWrjv5qi9oBnuOCGsqgVoFlJ2NR3dsYIv-HwYi4y7s8o0iBX09VID7u7beDy9rjxoN9TXFnGfijg2WRQz3eUAol_esiMKPb7RG5BARsQVcsIhD</api:session>
            </api:SessionHeader>
        </x:Header>
        <x:Body>
            <api:query>
                <api:queryString>select id from productrateplan where productid='2c92c0f8547a3d64015494b080c17c3a'</api:queryString>
            </api:query>
        </x:Body>
    </x:Envelope>

### Create an amendment in subscription associated with an account    

    <x:Envelope xmlns:x="http://schemas.xmlsoap.org/soap/envelope/" xmlns:api="http://api.zuora.com/" xmlns:ns2="http://object.api.zuora.com/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns1="http://api.zuora.com/">
        <x:Header>
            <api:QueryOptions>
                <api:batchSize/>
                <api:caseSensitive/>
            </api:QueryOptions>
            <api:SessionHeader>
                <api:session>h5K6kbO-Q7musTMZV4Xx_KR1EDyQIKqFzEpBR9Z3hC_PJQfkh1-mxNAJuX9ojBi3LQdXdZigj2myX9sNA2XV9c31AsjDMw2KNA44_QvLROb4HCDYYlIf7Vob8rf35oBg3Vb2r1tk2PWJOrDf4sWG56hWl3Uz5eSU9M-dUL_6w48y7SRRiZhN_DEdnlyxLd9j2FVmyEIT-ES5gPFShKgADYowd4ZwDbPlGoDNkkmoRdaUFkszLrTjKalB8D62XXE6</api:session>
            </api:SessionHeader>
        </x:Header>
        <x:Body>
        <ns1:amend>
        <ns1:requests>
            <ns1:Amendments>
                <ns2:ContractEffectiveDate>2016-05-11</ns2:ContractEffectiveDate>
                <ns2:CustomerAcceptanceDate>2016-05-11</ns2:CustomerAcceptanceDate>
                <ns2:EffectiveDate>2016-05-11</ns2:EffectiveDate>
                <ns2:Name>SOAPApiTest</ns2:Name>
                <ns2:RatePlanData>
                    <ns1:RatePlan>
                      <ns2:ProductRatePlanId>2c92c0f8547a3ca2015494b125e165bc</ns2:ProductRatePlanId>
                    </ns1:RatePlan>
                </ns2:RatePlanData>
                <ns2:ServiceActivationDate>2016-05-11</ns2:ServiceActivationDate>
                <ns2:Status>Completed</ns2:Status>
                <ns2:SubscriptionId>2c92c0f8547a3d64015495cd3c78073e</ns2:SubscriptionId>
                <ns2:Type>NewProduct</ns2:Type>
            </ns1:Amendments>
            <ns1:AmendOptions>
                <ns1:GenerateInvoice>False</ns1:GenerateInvoice>
                <ns1:ProcessPayments>False</ns1:ProcessPayments>
            </ns1:AmendOptions>
            <ns1:PreviewOptions>
                <ns1:EnablePreviewMode>false</ns1:EnablePreviewMode>
            </ns1:PreviewOptions>
        </ns1:requests>
        </ns1:amend>
        </x:Body>
    </x:Envelope>  

### Get query used to create an export from UI

    <x:Envelope xmlns:x="http://schemas.xmlsoap.org/soap/envelope/" xmlns:api="http://api.zuora.com/">
        <x:Header>
            <api:QueryOptions>
                <api:batchSize/>
                <api:caseSensitive/>
            </api:QueryOptions>
            <api:SessionHeader>
                <api:session>oLxisFxem29I_gyqAceKOui0cwHBjx7hZ-84bPolefq6RycQ2bw3kI6QZWM7jeuZ4TXf-wQgyeyu7JibbAXMQHRRD_rk89shm52JRMG3itZ8k9sLh236qrJbKhc0N-CJFcUT7jbeVXK4vqyppUVWrjv5qi9oBnuOCGsqgVoFlJ2NR3dsYIv-HwYi4y7s8o0iBX09VID7u7beDy9rjxoN9TXFnGfijg2WRQz3eUAol_esiMKPb7RG5BARsQVcsIhD</api:session>
            </api:SessionHeader>
        </x:Header>
        <x:Body>
            <api:query>
                <api:queryString>select query from export where fileid='2c92c086549a191b01549f824a3e1a22'</api:queryString>
            </api:query>
        </x:Body>
    </x:Envelope>

### Create new export

    <x:Envelope xmlns:x="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns2="http://object.api.zuora.com/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns1="http://api.zuora.com/" xmlns:api="http://api.zuora.com/" xmlns:obj="http://object.api.zuora.com/">
        <x:Header>
            <api:CallOptions>
                <api:useSingleTransaction/>
            </api:CallOptions>
            <api:SessionHeader>
                <api:session>oLxisFxem29I_gyqAceKOui0cwHBjx7hZ-84bPolefq6RycQ2bw3kI6QZWM7jeuZ4TXf-wQgyeyu7JibbAXMQHRRD_rk89shm52JRMG3itZ8k9sLh236qrJbKhc0N-CJFcUT7jbeVXK4vqyppUVWrjv5qi9oBnuOCGsqgVoFlJ2NR3dsYIv-HwYi4y7s8o0iBX09VID7u7beDy9rjxoN9TXFnGfijg2WRQz3eUAol_esiMKPb7RG5BARsQVcsIhD</api:session>
            </api:SessionHeader>
        </x:Header>
        <x:Body>
    <ns1:create xmlns:ns1="http://api.zuora.com/">
     <ns1:zObjects xmlns:ns2="http://object.api.zuora.com/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="ns2:Export">
         <ns2:format>csv</ns2:format>
         <ns2:name>Training anurag SOAP test export</ns2:name>
         <ns2:query>select ProductRatePlanCharge.Id, ProductRatePlanCharge.Name, Product.Id, Product.Name, ProductRatePlan.Id, ProductRatePlan.Name from ProductRatePlanCharge</ns2:query>
         <ns2:Zip>False</ns2:Zip>
     </ns1:zObjects>
    </ns1:create>
        </x:Body>
    </x:Envelope>

# Useful links
* [Training Agenda](https://docs.google.com/presentation/d/1Y6pNkygApiSHYHPQWdxfmnls6t-5zYL30Mnq9AmMoFM/edit?ts=57288e0b#slide=id.p10)
* [Knowledge Center](https://knowledgecenter.zuora.com/)
* [Sandbox](http://apisandbox.zuora.com/apps)
* [Zuora Object Model](https://knowledgecenter.zuora.com/DC_Developers/SOAP_API/E0_API_Object_Relationships)

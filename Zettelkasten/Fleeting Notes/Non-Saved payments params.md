---
title: Non-Saved payments params
created_at: Thursday 23rd June 2022
uuid: 1655988302
tags: #refinement
---

**raw**

```
<ActionController::Parameters {"payment_method"=>"{\"id\":\"pm_1LDpQfAWJZkRaLifKNvLxzOB\",\"object\":\"payment_method\",\"billing_details\":{\"address\":{\"city\":\"Atlanta\",\"country\":\"US\",\"line1\":\"June 23\",\"line2\":null,\"postal_code\":\"30318\",\"state\":\"GA\"},\"email\":null,\"name\":\"Ash Ketchum\",\"phone\":null},\"card\":{\"brand\":\"visa\",\"checks\":{\"address_line1_check\":null,\"address_postal_code_check\":null,\"cvc_check\":null},\"country\":\"US\",\"exp_month\":4,\"exp_year\":2043,\"funding\":\"credit\",\"generated_from\":null,\"last4\":\"4242\",\"networks\":{\"available\":[\"visa\"],\"preferred\":null},\"three_d_secure_usage\":{\"supported\":true},\"wallet\":null},\"created\":1655988398,\"customer\":null,\"livemode\":false,\"type\":\"card\"}", "pending_purchase_transaction_uuid"=>"4335e3d665a31830e5db20945062f77c", "authenticity_token"=>"yRUed5Az2BW34SSaCH9OeVxgbKU9zF8V3CHrtPc+KNC2f4n/3MDkKVQm9ZjdgLRePf8GarKgj9kzD3NcBvnkGQ==", "controller"=>"api/payments/stripes", "action"=>"authorize"} permitted: false>
```

**keys**
```json
[4] pry(#<Api::Payments::StripesController>)> params.keys
=> ["payment_method", "pending_purchase_transaction_uuid", "authenticity_token", "controller", "action"]
```

**payment method**
```json
[3] pry(#<Api::Payments::StripesController>)> JSON.parse(params[:payment_method])
=> {"id"=>"pm_1LDpQfAWJZkRaLifKNvLxzOB",
 "object"=>"payment_method",
 "billing_details"=>
  {"address"=>{"city"=>"Atlanta", "country"=>"US", "line1"=>"June 23", "line2"=>nil, "postal_code"=>"30318", "state"=>"GA"},
   "email"=>nil,
   "name"=>"Ash Ketchum",
   "phone"=>nil},
 "card"=>
  {"brand"=>"visa",
   "checks"=>{"address_line1_check"=>nil, "address_postal_code_check"=>nil, "cvc_check"=>nil},
   "country"=>"US",
   "exp_month"=>4,
   "exp_year"=>2043,
   "funding"=>"credit",
   "generated_from"=>nil,
   "last4"=>"4242",
   "networks"=>{"available"=>["visa"], "preferred"=>nil},
   "three_d_secure_usage"=>{"supported"=>true},
   "wallet"=>nil},
 "created"=>1655988398,
 "customer"=>nil,
 "livemode"=>false,
 "type"=>"card"}

```

**payment creator**
```json
 <ActionController::Parameters {"city"=>"Atlanta", "country"=>"US", "first_name"=>"Ash", "last_name"=>"Ketchum", "state"=>"GA", "street_address"=>"June 23", "zip"=>"30318", "authenticity_token"=>"0LsU0rTQL/L6HyZY1Y/eb8NdrfzGYpG4J1Ldkgj4fsOv0YNa+CMTzhnY91oAcCRIosLHM0kOQXTIfEV6+T+yCg==", "controller"=>"api/payments/stripes", "action"=>"create"} permitted: false>

params.keys
=> ["city", "country", "first_name", "last_name", "state", "street_address", "zip", "authenticity_token", "controller", "action"]

```



**createPaymentMethod return**
```js
{paymentMethod: {…}}
{
    "paymentMethod": {
        "id": "pm_1LDuRUAWJZkRaLifci7VWAHK",
        "object": "payment_method",
        "billing_details": {
            "address": {
                "city": "Atlanta",
                "country": "US",
                "line1": "23 June new",
                "line2": null,
                "postal_code": "30318",
                "state": "GA"
            },
            "email": null,
            "name": "Ash Ketchum",
            "phone": null
        },
        "card": {
            "brand": "visa",
            "checks": {
                "address_line1_check": null,
                "address_postal_code_check": null,
                "cvc_check": null
            },
            "country": "US",
            "exp_month": 3,
            "exp_year": 2048,
            "funding": "credit",
            "generated_from": null,
            "last4": "4242",
            "networks": {
                "available": [
                    "visa"
                ],
                "preferred": null
            },
            "three_d_secure_usage": {
                "supported": true
            },
            "wallet": null
        },
        "created": 1656007668,
        "customer": null,
        "livemode": false,
        "type": "card"
    }
}
```




**authorizeStripePayment return**
```js

```



## References
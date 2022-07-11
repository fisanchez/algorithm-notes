---
title: Saved Payments Params
created_at: Thursday 23rd June 2022
uuid: 1655988220
tags: #refinement
---


**initial**

```
 <ActionController::Parameters {"authenticity_token"=>"xdGE3IkIpnpbZDSYu3xVCbhd/pjGI3FXd7upjca+HtS6uxNUxfuaRrij5Zpug68u2cKUV0lPoZuYlTFlN3nSHQ==", "controller"=>"api/payments/stripes", "action"=>"process_saved_payment", "stripe"=>{}} permitted: false>
```

**adding pending purchase uuid**

```
<ActionController::Parameters {"authenticity_token"=>"xdGE3IkIpnpbZDSYu3xVCbhd/pjGI3FXd7upjca+HtS6uxNUxfuaRrij5Zpug68u2cKUV0lPoZuYlTFlN3nSHQ==", "controller"=>"api/payments/stripes", "action"=>"process_saved_payment", "stripe"=>{}, "pending_purchase_transaction_uuid"=>"43ee3bc680532640236eef622690f762"} permitted: false>
```

**Adding payment method**
```
<ActionController::Parameters {"authenticity_token"=>"xdGE3IkIpnpbZDSYu3xVCbhd/pjGI3FXd7upjca+HtS6uxNUxfuaRrij5Zpug68u2cKUV0lPoZuYlTFlN3nSHQ==", "controller"=>"api/payments/stripes", "action"=>"process_saved_payment", "stripe"=>{}, "pending_purchase_transaction_uuid"=>"43ee3bc680532640236eef622690f762", "payment_method"=>"{\"id\":\"pm_1L9D5yAWJZkRaLifaxDL6aMf\",\"object\":\"payment_method\",\"billing_details\":{\"address\":{\"city\":\"Atlanta\",\"country\":\"US\",\"line1\":\"10 Happy St\",\"line2\":null,\"postal_code\":\"30318\",\"state\":\"GA\"},\"email\":null,\"name\":\"Ash Ketchum\",\"phone\":null},\"card\":{\"brand\":\"visa\",\"checks\":{\"address_line1_check\":\"pass\",\"address_postal_code_check\":\"pass\",\"cvc_check\":\"pass\"},\"country\":\"US\",\"exp_month\":4,\"exp_year\":2043,\"fingerprint\":\"2IRdkCKtUBUnPU6n\",\"funding\":\"credit\",\"generated_from\":null,\"last4\":\"4242\",\"networks\":{\"available\":[\"visa\"],\"preferred\":null},\"three_d_secure_usage\":{\"supported\":true},\"wallet\":null},\"created\":1654887731,\"customer\":\"cus_LqqsLcBco3rbxC\",\"livemode\":false,\"metadata\":{},\"type\":\"card\"}"} permitted: false>
```


## References
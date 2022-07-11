---
title: 06220222 Wednesday
created_at: Wednesday 22nd June 2022
uuid: 1655897765
tags: #refinement #diary
---

## Todo 

## Notes


### Code

**Stripes controller**

`payment_creator.response`  =>
`payment_creator_service.run` =>

```ruby
creator = PaymentServices::Creator.new(
	pending_purchase_attributes: pending_purchase_attributes,
	service: PaymentServices::Stripe,
	service_attributes: params
).run
```

The update method calls `PaymentServices::Creator.response` ?
<span style="color:red">
YES IT DOES
</span>

``` ruby
# creator returns a hash
{:json=>
  {:taxes=>{:details=>nil, :flatTaxMultiplier=>0, :hasNZTax=>false, :isCalculated=>true, :label=>"Tax", :total=>"$1.12", :vatTaxMessage=>""},
   :cart=>{:formattedSavingsTotal=>"$0.00", :formattedSubTotal=>"$15.95", :itemsTotalCount=>1, :savingsTotal=>0.0, :subTotal=>15.95, :total=>"$17.07"},
   :pending_purchase_transaction_uuid=>"c73b64212215a9c9fad984c845a2fc91",
   :trigger_recaptcha=>false},
 :status=>:ok}
```


`PaymentServices::Creator.response` creates a pending_purchase_transaction_uuid which is just `pending_purchase.transaction_uuid`

<span style="color:red">
I don't need to do this step if I already have billing details - 
</span>

![[Pasted image 20220622080440.png]]
**How we process transaction currently** 
1. Hit stripes#create
2. Web uses Stripe javascript library to call stripe.createPaymentMethod
3. We then finalize given this payment method in stripes#authorize
4. profit


**What the Authorizer do**
```ruby
def execute
	authorize_payment

	institution_tax_updater if valid?
	validate_transaction_allowed_by_vst if valid?
	validate_order_allowed_by_fraud_prevention

	handle_errors
ensure
	send_google_analytics_events unless valid?
end

authorizer = service::Authorizer.new(service_attributes)
      authorizer.run

```


1. `PaymentServices::Stripe::Authorizer.new(params).run`
2. 


```json
def payment_method
        binding.pry
        ::Stripe::PaymentMethod.construct_from(payment_method_params)
      end
#> {"id"=>"pm_1LDT3lAWJZkRaLifHRY6s0zA",
 "object"=>"payment_method",
 "billing_details"=>
  {"address"=>{"city"=>"Atlanta", "country"=>"US", "line1"=>"22 Happy st", "line2"=>nil, "postal_code"=>"30218", "state"=>"GA"},
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
 "created"=>1655902410,
 "customer"=>nil,
 "livemode"=>false,
 "type"=>"card"}
```



**Non-saved payments params**
```json
[12] pry(#<Api::Payments::StripesController>)> params.keys
=> ["payment_method", "pending_purchase_transaction_uuid", "authenticity_token", "controller", "action"]

pry(#<Api::Payments::StripesController>)> params[:authenticity_token]
=> "QhMMuol4UqvdiC4Dd3wV+70a8Cc1HIVTlkgBSey/mMM9eZsyxYtulz5P/wGig+/c3IWa6LpwVZ95ZpmhHXhUCg=="

[13] pry(#<Api::Payments::StripesController>)> params[:pending_purchase_transaction_uuid]
=> "bf424463a03e77a3d279e1ad32ffd344"

pry(#<Api::Payments::StripesController>)> JSON.parse(params[:payment_method])
=> {"id"=>"pm_1LDTOqAWJZkRaLifUxUzNnrK",
 "object"=>"payment_method",
 "billing_details"=>
  {"address"=>{"city"=>"Atlanta", "country"=>"US", "line1"=>"22 Happy st", "line2"=>nil, "postal_code"=>"30218", "state"=>"GA"},
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
 "created"=>1655903717,
 "customer"=>nil,
 "livemode"=>false,
 "type"=>"card"}
 permitted: false>
```


**Saved Payments params**
```json
pry(#<Api::Payments::StripesController>)> params.keys
=> ["authenticity_token", "controller", "action", "stripe", "pending_purchase_transaction_uuid", "payment_method", "saved_payment"]

		
```

### Refinement

**VST-46343**
Robots.txt Disallow User Agents
We want to add a list of agents that are scrapping our site

**VST-46369**
Updates the title and subtitle

**VST-46370**
Updating the product details info

**VST-46731**
Updates the cover image and share button


## References
---
title: 06082020 Wednesday
created_at: Wednesday 8th June 2022
uuid: 1654699298
tags: #refinement #diary
---

## Todo 
- [x] Deploy bulk tickets to dev
- [x] Address 40739 observations
- [x] Commit translations for VST-40731
- [x] Review PR for VST-28190
	Talked with Barnabas to review his changes
- [ ] Start work on 28110 branching off 28109

## Notes
semantic color naming:
	Instead of using words like 'blue', 'red', etc. Use words like 
	'primary', 'warning', 'etc'


- User has one customer
- Customer has many saved payments ( we are going to pretend they only have one)
- Customer belongs to user and we're not always creating a customer
- User is a customer that has made a purchase, but only save payment if they elect to
- Everything starts with `stripe/authorizer.rb` then goes to `executor.rb`
- Payment method is structured in `#payment_method`
- [ ] After billing address, before cc form
- `SavedPaymentMethod`, `User`, `Customer`
## References

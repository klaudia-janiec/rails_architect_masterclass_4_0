# Week 5 Homework

## Actors
1. Sales person
2. Company owning products
3. Commission platform

## Requirements
1. Sales person sells a product. They get a commission based on agreed conditions, from the company. The commission platform receives an agreed (with the company) N% from each commission too. 
2. Sales people can sell products from different companies
3. The company can see, each month, how much they need to pay to each sales person and why
4. The platform admins can see hot much they will charge the companies
5. The sales person knows at any moment how much of their sales they made - how much commission was made


## What ifs
1. we get a sale information, but the product was not provided yet?
2. we get a sale info, but we don't have the commission agreement with the sales man?
3. what if the commission agreement can change, also back in time?

## Solution

**Read models**:
- `salesmen_commissions` - summary of how much commissions each company should pay salesmen, should subscribe `salesman_commission_calculated` event,
- `company_fees` - summary of how much platform charge each company, should subscribe `comission_fee_calculated` event,
- `salesman_earnings` - summary of how much commissions sales person get, should subscribe `salesman_commission_calculated` event,
- `product` - products which sales person can sell, should subscribe `product_sold` event.

**Value objects**: `fee` (for salesman and comission platform) \
**Entities**: `salesman`, `company`, `product` \
**Aggregate roots**: `sale`, `comission_agreement` \
**Commands**:
- `sell_product` - command which is emitted when salesman sells product.

**Domain events**:
- `product_sold` - it is broadcasted when product is sold,
- `salesman_commission_calculated` - it is bradcasted when commission for salesperson is calculated,
- `comission_fee_calculated` - it is broadcasted when fee which company should pay is calculated.

**What if we get a sale information, but the product was not provided yet?**\
We should have `state` on sale. If product was not provided yet we should set sale `state` to `unconfirmed`. We should introduce new domain event eg. `sale_not_confirmed`. Then we should introduce new command `provide_product`. If we get that command we should move all sales which were `unconfirmed` and contained that product to `confirmed` and send `product_sold` event. Also we should cancel sale if product was not provided in certain period of time. The sale state should be changed to `cancelled` and emit event `sale_cancelled`.

**What if we get a sale info, but we don't have the commission agreement with the sales man?**\
I think we should add new commands `salesman_agree_commission` and `company_agree_commission`. Unless we get both commands the sale state should be `unconfirmed` and `sale_not_confirmed` event should be emitted. If we get both commands the sale state should be changed to `confirmed` and `product_sold` event emitted. If we don't get both agreements in given period of time the sale state should be changed to `cancelled` and emit `sale_cancelled`.

**What if the commission agreement can change, also back in time?**\
We should add new command `change_commission_agreement`. Then when we should recalculate all commissions and broadcast `salesman_commission_calculated` and `comission_fee_calculated`.

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

**Read models**: `company_sale_summary`, `company_fees`, `salesman_commission_summary`, `product` \
**Value objects**: `fee` (for salesman and comission platform) \
**Entities**: `salesman`, `company`, `product` \
**Aggregate roots**: `sale` `comission_agreement` \
**Commands**: `sell_product`, `calculate_salesman_commission`, `calculate_commission_fee`, `agree_commission` \
**Domain events**: `product_sold`, `salesman_commission_calculated`, `comission_fee_calculated`, `comission_aggreed` 

*What if we get a sale information, but the product was not provided yet?*

*What if we get a sale info, but we don't have the commission agreement with the sales man?*

*What if the commission agreement can change, also back in time?*

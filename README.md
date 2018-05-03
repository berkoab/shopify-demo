# Create new discount code using Shopify API

## Create a new discount rule
curl -X POST -H 'Content-Type: application/json' 'https://key:pass@aryeh-berkowitz.myshopify.com/admin/price_rules.json' -d '{  "price_rule": {    "title": "SUMMERSALE10OFF",    "target_type": "line_item",    "target_selection": "all",    "allocation_method": "across",    "value_type": "fixed_amount",    "value": "-10.0",    "customer_selection": "all", "starts_at": "2018-05-02T17:59:10Z"  }}'

## New discount rule response:
{"price_rule":{"id":279307124787,"value_type":"fixed_amount","value":"-10.0","customer_selection":"all","target_type":"line_item","target_selection":"all","allocation_method":"across","once_per_customer":false,"usage_limit":null,"starts_at":"2018-05-02T13:59:10-04:00","ends_at":null,"created_at":"2018-05-03T09:31:50-04:00","updated_at":"2018-05-03T09:31:50-04:00","entitled_product_ids":[],"entitled_variant_ids":[],"entitled_collection_ids":[],"entitled_country_ids":[],"prerequisite_saved_search_ids":[],"prerequisite_customer_ids":[],"prerequisite_subtotal_range":null,"prerequisite_quantity_range":null,"prerequisite_shipping_price_range":null,"title":"SUMMERSALE10OFF"}}

## Use the new rule and create a new discount code:
curl -X POST -H 'Content-Type: application/json' 'https://key:pass@aryeh-berkowitz.myshopify.com//admin/price_rules/279307124787/discount_codes.json' -d '{"discount_code": {    "code": "SUMMERSALE10OFF"  }}'

## New discount rule response:
{"discount_code":{"id":1200153198643,"price_rule_id":279307124787,"code":"SUMMERSALE10OFF","usage_count":0,"created_at":"2018-05-03T09:35:24-04:00","updated_at":"2018-05-03T09:35:24-04:00"}}

## Finally, include the new discount code in an email link
https://aryeh-berkowitz.myshopify.com/discount/SUMMERSALE10OFF

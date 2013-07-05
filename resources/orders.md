## Resources
<table class="table table-bordered ">
  <thead>
   <tr>
     <th>Resource</th>
   </tr>
 </thead>
 <tbody>
   <tr>
     <td><a href="#get-ordersjson">GET  /orders.json</a></td>
     
   </tr>
   
   <tr>
     <td><a href="#get-ordersidjson">GET /orders/id.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#put-ordersidjson">PUT /orders/id.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#get-orderscountjson">GET /orders/count.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#delete-ordersjson">DELETE /orders.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#delete-ordersidjson">DELETE /orders/id.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#post-ordersjson">POST /orders.json</a></td>
     
   </tr>
   
 </tbody>
</table>
   
## Description
### GET orders.json
GET orders from a store

#### Request
These fields can be used to filter the query. By default, without any filters, the GET request returns all the orders.

<table class="table table-bordered ">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>description</th>
   </tr>
  </thead>
  <tbody>
   
   <tr>
    <td > min_id </td>
    <td > int </td>
    <td > The min ID of the order. This is auto-generated for new orders. </td>
    </tr>

    <tr>
    <td > max_id </td>
    <td > int </td>
    <td > The min ID of the order. This is auto-generated for new orders. </td>
    </tr>

    <tr>
    <td > min_total </td>
    <td > decimal </td>
    <td > The min total of the order.</td>
    </tr>

    <tr>
    <td > max_total </td>
    <td > decimal </td>
    <td > The max total of the order.</td>
    </tr>

    <tr>
    <td > customer_id </td>
    <td > int </td>
    <td > The ID of the customer that placed the order or 0 if it was a guest order. </td>
    </tr>

    <tr>
    <td > min_date_created </td>
    <td > date </td>
    <td > The min date when the order was created. If you want to get the orders past a certain date, use this field. The date should be RFC format - 'Tue, 20 Nov 2012 00:00:00 +0000' </td>
    </tr>

    <tr>
    <td > max_date_created </td>
    <td > date </td>
    <td > The max date when the order was created. If you want to get the orders until a certain date, use this field. The date should be RFC format - 'Tue, 20 Nov 2012 00:00:00 +0000' </td>
    </tr>

    <tr>
    <td > status_id </td>
    <td > int </td>
    <td > The status of the order. A list of available statuses can be retrieved from Order Statuses resource </td>
    </tr>

    <tr>
  <td > payment_method </td>
  <td > string </td>
  <td > The payment method used for the order. </td>
  </tr>

  <tr>
  <td > is_deleted </td>
  <td > boolean </td>
  <td > Indicates if the order was deleted (archived). </td>
  </tr>
  </tbody>
</table>

#### Response
List of orders
<pre>
[
  {
    "id": 100,
    "customer_id": 10,
    "date_created": "Wed, 14 Nov 2012 19:26:23 +0000",
    "date_modified": "Wed, 14 Nov 2012 19:26:23 +0000",
    "date_shipped": "",
    "status_id": 11,
    "status": "Awaiting Fulfillment",
    "subtotal_ex_tax": "79.0000",
    "subtotal_inc_tax": "79.0000",
    "subtotal_tax": "0.0000",
    "base_shipping_cost": "0.0000",
    "shipping_cost_ex_tax": "0.0000",
    "shipping_cost_inc_tax": "0.0000",
    "shipping_cost_tax": "0.0000",
    "shipping_cost_tax_class_id": 2,
    "base_handling_cost": "0.0000",
    "handling_cost_ex_tax": "0.0000",
    "handling_cost_inc_tax": "0.0000",
    "handling_cost_tax": "0.0000",
    "handling_cost_tax_class_id": 2,
    "base_wrapping_cost": "0.0000",
    "wrapping_cost_ex_tax": "0.0000",
    "wrapping_cost_inc_tax": "0.0000",
    "wrapping_cost_tax": "0.0000",
    "wrapping_cost_tax_class_id": 3,
    "total_ex_tax": "79.0000",
    "total_inc_tax": "79.0000",
    "total_tax": "0.0000",
    "items_total": 1,
    "items_shipped": 0,
    "payment_method": "cash",
    "payment_provider_id": null,
    "payment_status": "",
    "refunded_amount": "0.0000",
    "order_is_digital": false,
    "store_credit_amount": "0.0000",
    "gift_certificate_amount": "0.0000",
    "ip_address": "50.58.18.2",
    "geoip_country": "",
    "geoip_country_iso2": "",
    "currency_id": 1,
    "currency_code": "USD",
    "currency_exchange_rate": "1.0000000000",
    "default_currency_id": 1,
    "default_currency_code": "USD",
    "staff_notes": "",
    "customer_message": "",
    "discount_amount": "0.0000",
    "coupon_discount": "0.0000",
    "shipping_address_count": 1,
    "is_deleted": false,
    "billing_address": {
        "first_name": "Trisha",
        "last_name": "McLaughlin",
        "company": "",
        "street_1": "12345 W Anderson Ln",
        "street_2": "",
        "city": "Austin",
        "state": "Texas",
        "zip": "78757",
        "country": "United States",
        "country_iso2": "US",
        "phone": "",
        "email": "elsie@example.com"
    },
    "products": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/orders/100/products.json",
        "resource": "/orders/100/products"
    },
    "shipping_addresses": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/orders/100/shippingaddresses.json",
        "resource": "/orders/100/shippingaddresses"
    },
    "coupons": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/orders/100/coupons.json",
        "resource": "/orders/100/coupons"
    }
  }
]
</pre>

### GET orders/id.json
GET a order from a store

#### Request
This GET request does not take any parameters.

#### Response
order by ID
<pre>
{
    "id": 100,
    "customer_id": 10,
    "date_created": "Wed, 14 Nov 2012 19:26:23 +0000",
    "date_modified": "Wed, 14 Nov 2012 19:26:23 +0000",
    "date_shipped": "",
    "status_id": 11,
    "status": "Awaiting Fulfillment",
    "subtotal_ex_tax": "79.0000",
    "subtotal_inc_tax": "79.0000",
    "subtotal_tax": "0.0000",
    "base_shipping_cost": "0.0000",
    "shipping_cost_ex_tax": "0.0000",
    "shipping_cost_inc_tax": "0.0000",
    "shipping_cost_tax": "0.0000",
    "shipping_cost_tax_class_id": 2,
    "base_handling_cost": "0.0000",
    "handling_cost_ex_tax": "0.0000",
    "handling_cost_inc_tax": "0.0000",
    "handling_cost_tax": "0.0000",
    "handling_cost_tax_class_id": 2,
    "base_wrapping_cost": "0.0000",
    "wrapping_cost_ex_tax": "0.0000",
    "wrapping_cost_inc_tax": "0.0000",
    "wrapping_cost_tax": "0.0000",
    "wrapping_cost_tax_class_id": 3,
    "total_ex_tax": "79.0000",
    "total_inc_tax": "79.0000",
    "total_tax": "0.0000",
    "items_total": 1,
    "items_shipped": 0,
    "payment_method": "cash",
    "payment_provider_id": null,
    "payment_status": "",
    "refunded_amount": "0.0000",
    "order_is_digital": false,
    "store_credit_amount": "0.0000",
    "gift_certificate_amount": "0.0000",
    "ip_address": "50.58.18.2",
    "geoip_country": "",
    "geoip_country_iso2": "",
    "currency_id": 1,
    "currency_code": "USD",
    "currency_exchange_rate": "1.0000000000",
    "default_currency_id": 1,
    "default_currency_code": "USD",
    "staff_notes": "",
    "customer_message": "",
    "discount_amount": "0.0000",
    "coupon_discount": "0.0000",
    "shipping_address_count": 1,
    "is_deleted": false,
    "billing_address": {
        "first_name": "Trisha",
        "last_name": "McLaughlin",
        "company": "",
        "street_1": "12345 W Anderson Ln",
        "street_2": "",
        "city": "Austin",
        "state": "Texas",
        "zip": "78757",
        "country": "United States",
        "country_iso2": "US",
        "phone": "",
        "email": "elsie@example.com"
    },
    "products": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/orders/100/products.json",
        "resource": "/orders/100/products"
    },
    "shipping_addresses": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/orders/100/shippingaddresses.json",
        "resource": "/orders/100/shippingaddresses"
    },
    "coupons": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/orders/100/coupons.json",
        "resource": "/orders/100/coupons"
    }
}  
</pre>    


### GET orders/count.json
Get a total number of orders in the store

#### Request
This request does not take any parameters.

#### Response
Returns the number of orders in the store 
<pre>
  {
    "count": 10
  }
</pre>
Here are resources to delete orders. This is a potentially destrutive operation. Remember that you cannot recover deleted orders.

### DELETE orders.json
DELETE all orders

### DELETE orders/id.json
DELETE a order

### POST orders.json

Effectively the Orders POST API allows you to submit a manual order.

The API allows you to create overrides for values, e.g: product prices, subtotal and totals. When not supplied the API will use the store's values and do the calculation automatically as if an order was made through the store, respecting tax rules set by the store which are applicable to the billing/shipping address of the order.

##### Specifics on Products

- All products are specified by product_id.
- If price is not specified, it will automatically pick up the price from the store's product catalog, however you can override it via price_inc_tax and price_ex_tax.
- Tax will be calculated based on the tax rules specified in the store, however you can optionally override the tax values by specifying price_inc_tax and price_ex_tax.
- For products which are configured to track stock, the quantity specified on the order will reduce the stock on hand. When there is not enough inventory to fulfil the order, it will be rejected with an 'out of stock' error code.
- For products which have min and max quantities specified in their settings, the API will honor these and reject orders appropriately.
- For Products where product options are required, the API will validate these requirements to ensure the product options are specified.
- Product quantity must be specified.
- Custom products are not supported at this time.

##### Specifics on Totals

- When not specified, order subtotal and total are automatically calculated.
- You can override order subtotal and/or total. If you choose to override one, we strongly recommend that override both as the system will not be able to accurately calculate the other.

##### Specifics on Orders

- status_id can be specified resulting in the the corresponding 'status' to automatically be set. When not specified, status_id will be automatically set to 1 resulting in 'status' to be set to 'Pending'
- Billing address is mandatory.
- Shipping address is not mandatory and can optionally be specified as composite records.
	* When the shipping address is not specified, the system will fall back to using the billing address as the shipping address 
	* Multiple shipments are not supported so it will assume the first address in the collection
- In the shipping and billing address, their is no requirement to specify 'country' when 'country_ISO2' is specified.
	* The value specified for 'country_ISO2' will always override any value specified for 'country'
- Coupon redemption is not supported at this time.
- Set customer_id to 0 to specify a guest checkout.
- order_source cannot be specified and it will be set to 'external'.
	* You can optionally specify a value for external_source to specify which external source the order is coming from - ie. POS system X, accounting system Y, etc


#### Request



<table class="table table-bordered ">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>description</th>
   </tr>
  </thead>
  <tbody>
  	<tr>
  		<td>customer_id</td>
  		<td>int</td>
  		<td>The ID of the customer placing the order or 0 if it was a guest order.</td>
  	</tr>
  	<tr>
  		<td>date_created</td>
  		<td>date</td>
  		<td>The date this order was created, if not specified will default to current time. The date should be in RFC format - 'Tue, 20 Nov 2012 00:00:00 +0000'</td>
  	</tr>
  	<tr>
  		<td>status_id</td>
  		<td>int</td>
  		<td>The status ID from <a href="/api/orderstatuses/">orderstatuses</a> documentation.</td>
  	</tr>
  	<tr>
  		<td>subtotal_ex_tax</td>
  		<td>decimal</td>
  		<td>Override value for subtotal excluding tax. If specified, the field subtotal_inc_tax is also required.</td>
  	</tr>
  	<tr>
  		<td>subtotal_inc_tax</td>
  		<td>decimal</td>
  		<td>Override value for subtotal including tax. If specified, the field subtotal_ex_tax is also required.</td>
  	</tr>
  	<tr>
  		<td>base_shipping_cost</td>
  		<td>decimal</td>
  		<td>The value of the base shipping cost</td>
  	</tr>
  	<tr>
  		<td>shipping_cost_ex_tax</td>
  		<td>decimal</td>
  		<td>The value of shipping cost excluding tax</td>
  	</tr>
  	<tr>
  		<td>shipping_cost_inc_tax</td>
  		<td>decimal</td>
  		<td>The value of shipping cost including tax</td>
  	</tr>
  	<tr>
  		<td>base_handling_cost</td>
  		<td>decimal</td>
  		<td>The value of the base handling cost</td>
  	</tr>
  	<tr>
  		<td>handling_cost_ex_tax</td>
  		<td>decimal</td>
  		<td>The value of the handling cost excluding tax</td>
  	</tr>
  	<tr>
  		<td>handling_cost_inc_tax</td>
  		<td>decimal</td>
  		<td>The value of the handling cost including tax</td>
  	</tr>
  	<tr>
  		<td>base_wrapping_cost</td>
  		<td>decimal</td>
  		<td>The value of the base wrapping cost</td>
  	</tr>
  	<tr>
  		<td>wrapping_cost_inc_tax</td>
  		<td>decimal</td>
  		<td>The value of the wrapping cost including tax</td>
  	</tr>
  	<tr>
  		<td>wrapping_cost_ex_tax</td>
  		<td>decimal</td>
  		<td>The value of the wrapping cost including tax</td>
  	</tr>
  	<tr>
  		<td>total_ex_tax</td>
  		<td>decimal</td>
  		<td>Override value for the total, excluding tax. If specified, the field total_inc_tax is also required.</td>
  	</tr>
  	<tr>
  		<td>total_inc_tax</td>
  		<td>decimal</td>
  		<td>Override value for the total, including tax. If specified, the field total_ex_tax is also required.</td>
  	</tr>
  	<tr>
  		<td>items_shipped</td>
  		<td>int</td>
  		<td>The number of items that has been shipped.</td>
  	</tr>
  	<tr>
  		<td>payment_method</td>
  		<td>string</td>
  		<td>The payment method for this order.</td>
  	</tr>
  	<tr>
  		<td>payment_provider_id</td>
  		<td>string</td>
  		<td>The ID of the payment provider if payment provier was used.</td>
  	</tr>
  	<tr>
  		<td>refunded_amount</td>
  		<td>decimal</td>
  		<td>The amount refunded from this transaction.</td>
  	</tr>
  	<tr>
  		<td>order_is_digital</td>
  		<td>boolean</td>
  		<td>Whether this order is an order for digital products.</td>
  	</tr>
  	<tr>
  		<td>ip_address</td>
  		<td>string</td>
  		<td>IP Address of the customer if known.</td>
  	</tr>
  	<tr>
  		<td>geoip_country</td>
  		<td>string</td>
  		<td>The full country name where the customer made the purchase based on the IP.</td>
  	</tr>
  	<tr>
  		<td>geoip_country_iso2</td>
  		<td>string</td>
  		<td>The country where the customer made the purchase based on the IP is ISO2 format.</td>
  	</tr>
  	<tr>
  		<td>currency_id</td>
  		<td>int</td>
  		<td>The ID of the currency being used in this transaction.</td>
  	</tr>
  	<tr>
  		<td>currency_code</td>
  		<td>string</td>
  		<td>The currency code of the currency being used in this transaction</td>
  	</tr>
  	<tr>
  		<td>currency_exchage_rate</td>
  		<td>decimal</td>
  		<td>The exchange rate of the currency being used against the store's default currency.</td>
  	</tr>
  	<tr>
  		<td>defaut_currency_id</td>
  		<td>int</td>
  		<td>The ID of the default currency for this type of transaction.</td>
  	</tr>
  	<tr>
  		<td>default_currency_code</td>
  		<td>string</td>
  		<td>The currency code of the default currency for this type of transaction</td>
  	</tr>
  	<tr>
  		<td>staff_notes</td>
  		<td>text</td>
  		<td>Any additional notes for staff.</td>
  	</tr>
  	<tr>
  		<td>customer_message</td>
  		<td>text</td>
  		<td>Message for the customer.</td>
  	</tr>
  	<tr>
  		<td>discount_amount</td>
  		<td>text</td>
  		<td>Amount of discount for this transaction.</td>
  	</tr>
  	<tr class="mandatory">
  		<td>billing_address</td>
  		<td>object</td>
  		<td>The billing address of the customer. See: "Address Fields"</td>
  	</tr>
  	<tr>
  		<td>shipping_addresses</td>
  		<td>object_array</td>
  		<td>The shipping addresses for this order. See: "Address Fields"</td>
  	</tr>
  	<tr>
  		<td>external_source</td>
  		<td>string</td>
  		<td>The name of the external source where this order was made. e.g: POS</td>
  	</tr>
  	<tr class="mandatory">
  		<td>products</td>
  		<td>object_array</td>
  		<td>The products being purchased in this transaction. See: "Product Fields"</td>
  	</tr>
  	
  </tbody>
</table>

#### Address Fields

<table class="table table-bordered ">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>description</th>
   </tr>
  </thead>
  <tbody>
  	<tr>
  		<td>first_name</td>
  		<td>string</td>
  		<td>Contact first name</td>
  	</tr>
  	<tr>
  		<td>last_name</td>
  		<td>string</td>
  		<td>Contact last name</td>
  	</tr>
  	<tr>
  		<td>company</td>
  		<td>string</td>
  		<td>Company name</td>
  	</tr>
  	<tr>
  		<td>street_1</td>
  		<td>string</td>
  		<td>Line 1 of street address</td>
  	</tr>
  	<tr>
  		<td>street_2</td>
  		<td>string</td>
  		<td>Line 2 of street address</td>
  	</tr>
  	<tr>
  		<td>city</td>
  		<td>string</td>
  		<td>Name of city</td>
  	</tr>
  	<tr>
  		<td>zip</td>
  		<td>string</td>
  		<td>Zip or postal code</td>
  	</tr>
  	<tr>
  		<td>country</td>
  		<td>string</td>
  		<td>Country full name</td>
  	</tr>
  	<tr>
  		<td>country_iso2</td>
  		<td>string</td>
  		<td>Country code in ISO 3166-1 alpha-2 format. (e.g: US, AU)</td>
  	</tr>
  	<tr>
  		<td>state</td>
  		<td>string</td>
  		<td>State/province name</td>
  	</tr>
  	<tr>
  		<td>email</td>
  		<td>string</td>
  		<td>Contact email address</td>
  	</tr>
  	<tr>
  		<td>phone</td>
  		<td>string</td>
  		<td>Contact phone number</td>
  	</tr>
  </tbody>
</table>

#### Product Fields

<table class="table table-bordered ">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>description</th>
   </tr>
  </thead>
  <tbody>
  	<tr class="mandatory">
  		<td>product_id</td>
  		<td>int</td>
  		<td>The ID of the product</td>
  	</tr>
  	<tr class="mandatory">
  		<td>quantity</td>
  		<td>int</td>
  		<td>The quantity of the purchase for this product</td>
  	</tr>
  	<tr>
  		<td>price_inc_tax</td>
  		<td>decimal</td>
  		<td>The override value for the price including tax. If specified, you will also need to specify "price_ex_tax". If NOT specified, store price will be used.</td>
  	</tr>
  	<tr>
  		<td>price_ex_tax</td>
  		<td>decimal</td>
  		<td>The override value for the price excluding tax. If specified, you will also need to specify "price_inc_tax". If NOT speicified, store price will be used.</td>
  	</tr>
  	<tr>
  		<td>product_options</td>
  		<td>object_array</td>
  		<td>The options chosen for this product purchase. See: "Options Fields"</td>
  	</tr>
  </tbody>
</table>

#### Options Fields

<table class="table table-bordered ">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>description</th>
   </tr>
  </thead>
  <tbody>
  	<tr class="mandatory">
  		<td>id</td>
  		<td>int</td>
  		<td>The ID of the <a href="/api/products/options">product option</a></td>
  	</tr>
  	<tr class="mandatory">
  		<td>value</td>
  		<td>text</td>
  		<td>The value for the option from <a href="/api/options/values">/options/values</a></td>
  	</tr>
  </tbody>
</table>

#### Sample payload

<pre>
{
    "customer_id": 0,
    "date_created": "Thu, 04 Oct 2012 03:24:40 +0000",
    "subtotal_ex_tax": 1705.00,
    "subtotal_inc_tax": 1915.00,
    "base_shipping_cost": 0,
    "shipping_cost_ex_tax": 0,
    "shipping_cost_inc_tax": 0,
    "base_handling_cost": 0,
    "handling_cost_ex_tax": 0,
    "handling_cost_inc_tax": 0,
    "base_wrapping_cost": 0,
    "wrapping_cost_ex_tax": 0,
    "wrapping_cost_inc_tax": 0,
    "total_ex_tax": 1705.00,
    "total_inc_tax": 1915.00,
    "refunded_amount": 0,
    "order_is_digital": false,
    "store_credit_amount": 0,
    "gift_certificate_amount": 0,
    "staff_notes": "",
    "customer_message": "",
    "discount_amount": 10,
    "shipping_address_count": 2,
    "is_deleted": false,
    "billing_address": {
      "first_name": "Trisha",
      "last_name": "McLaughlin",
      "company": "",
      "street_1": "12345 W Anderson Ln",
      "street_2": "",
      "city": "Austin",
      "state": "Texas",
      "zip": "78757",
      "country": "United States",
      "country_iso2": "US",
      "phone": "",
      "email": "elsie@example.com"
    },
"shipping_addresses": [{
      "first_name": "Trisha",
      "last_name": "McLaughlin",
      "company": "Acme Pty Ltd",
      "street_1": "566 Sussex St",
      "street_2": "",
      "city": "Austin",
      "state": "Texas",
      "zip": "78757",
      "country": "United States",
      "country_iso2": "US",
      "phone": "",
      "email": "elsie@example.com"
    }],
    "products": [ {
         "product_id": 6,
         "quantity": 2,
         "product_options": [
             { "id": 22, "value":  19 },
             { "id": 23, "value":  27 },
             { "id": 24, "value":  30 }
         ]
    },
    {
         "product_id": 6,
         "quantity": 2,
         "product_options": [
             { "id": 22, "value":  19 },
             { "id": 23, "value":  27 },
             { "id": 24, "value":  30 }
         ]
    },
    {
       "product_id": 27,
       "quantity": 3
    },
    {
       "product_id": 25,
       "quantity": 3
    }

    ],
    "external_source": "POS"
  }
</pre>

#### Sample success response

<pre>
Status Code: 201 Created

{
  "id": 100,
  "customer_id": 0,
  "date_created": "Thu, 04 Oct 2012 03:24:40 +0000",
  "date_modified": "Thu, 30 May 2013 01:48:39 +0000",
  "date_shipped": "",
  "status_id": 1,
  "status": "Pending",
  "subtotal_ex_tax": "1705.0000",
  "subtotal_inc_tax": "1915.0000",
  "subtotal_tax": "210.0000",
  "base_shipping_cost": "0.0000",
  "shipping_cost_ex_tax": "0.0000",
  "shipping_cost_inc_tax": "0.0000",
  "shipping_cost_tax": "0.0000",
  "shipping_cost_tax_class_id": 0,
  "base_handling_cost": "0.0000",
  "handling_cost_ex_tax": "0.0000",
  "handling_cost_inc_tax": "0.0000",
  "handling_cost_tax": "0.0000",
  "handling_cost_tax_class_id": 0,
  "base_wrapping_cost": "0.0000",
  "wrapping_cost_ex_tax": "0.0000",
  "wrapping_cost_inc_tax": "0.0000",
  "wrapping_cost_tax": "0.0000",
  "wrapping_cost_tax_class_id": 0,
  "total_ex_tax": "1705.0000",
  "total_inc_tax": "1915.0000",
  "total_tax": "210.0000",
  "items_total": 4,
  "items_shipped": 0,
  "payment_method": "Manual",
  "payment_provider_id": null,
  "payment_status": "",
  "refunded_amount": "0.0000",
  "order_is_digital": false,
  "store_credit_amount": "0.0000",
  "gift_certificate_amount": "0.0000",
  "ip_address": "",
  "geoip_country": "",
  "geoip_country_iso2": "",
  "currency_id": 0,
  "currency_code": null,
  "currency_exchange_rate": "0.0000000000",
  "default_currency_id": 0,
  "default_currency_code": null,
  "staff_notes": "",
  "customer_message": "",
  "discount_amount": "10.0000",
  "coupon_discount": "0.0000",
  "shipping_address_count": 1,
  "is_deleted": false,
  "billing_address": {
    "first_name": "Trisha",
    "last_name": "McLaughlin",
    "company": "",
    "street_1": "12345 W Anderson Ln",
    "street_2": "",
    "city": "Austin",
    "state": "Texas",
    "zip": "78757",
    "country": "United States",
    "country_iso2": "US",
    "phone": "",
    "email": "elsie@example.com"
  },
  "order_source": "external",
  "external_source": "POS",
  "products": {
    "url": "https://store-bwvr466.mybigcommerce.com/api/v2/orders/100/products.json",
    "resource": "/orders/100/products"
  },
  "shipping_addresses": {
    "url": "https://store-bwvr466.mybigcommerce.com/api/v2/orders/100/shippingaddresses.json",
    "resource": "/orders/100/shippingaddresses"
  },
  "coupons": {
    "url": "https://store-bwvr466.mybigcommerce.com/api/v2/orders/100/coupons.json",
    "resource": "/orders/100/coupons"
  }
}
</pre>

#### Sample response with inventory error

<pre>
[
  {
    "status": 409,
    "message": "Quantities of one or more products are out of stock or did not meet quantity requirements.",
    "details": {
      "errors": [
        {
          "type": "OutOfStock",
          "product": {
            "id": 6,
            "name": "[Sample Product] MacBook Pro",
            "sku": {
              "id": 5,
              "sku": "MACBOOKPRO-1-A",
              "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/6/skus/5.json",
              "resource": "/products/6/skus/5",
              "inventory_level": 5
            },
            "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/6.json",
            "resource": "/products/6"
          }
        },
        {
          "type": "ExceedsMaxQuantity",
          "product": {
            "id": 27,
            "name": "[Sample Product] Apple iPhone Bluetooth Headset",
            "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/27.json",
            "resource": "/products/27",
            "maximum_quantity": 5
          }
        },
        {
          "type": "InsufficientQuantity",
          "product": {
            "id": 25,
            "name": "[Sample Product] Incase Sports Armband for iPod Nano",
            "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/25.json",
            "resource": "/products/25",
            "minimum_quantity": 2
          }
        }
      ]
    }
  }
]
</pre>


#### Sample response with product options errors

<pre>
[
  {
    "status": 400,
    "message": "The options of one or more products are invalid.",
    "details": {
      "errors": [
        {
          "type": "MandatoryProductOptions",
          "product": {
            "id": 6,
            "name": "[Sample Product] MacBook Pro",
            "required_product_options": [
              {
                "id": 22,
                "option_id": 5,
                "display_name": "CPU",
                "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/6/options/22.json",
                "resource": "/products/6/options/22"
              },
              {
                "id": 23,
                "option_id": 6,
                "display_name": "HDD Size",
                "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/6/options/23.json",
                "resource": "/products/6/options/23"
              },
              {
                "id": 24,
                "option_id": 7,
                "display_name": "Video Memory",
                "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/6/options/24.json",
                "resource": "/products/6/options/24"
              }
            ],
            "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/6.json",
            "resource": "/products/6"
          }
        },
        {
          "type": "MandatoryProductOptions",
          "product": {
            "id": 5,
            "name": "[Sample Product] MacBook",
            "required_product_options": [
              {
                "id": 15,
                "option_id": 5,
                "display_name": "Clock Speeds (CPU)",
                "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/5/options/15.json",
                "resource": "/products/5/options/15"
              },
              {
                "id": 16,
                "option_id": 6,
                "display_name": "HDD Sizes",
                "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/5/options/16.json",
                "resource": "/products/5/options/16"
              }
            ],
            "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/5.json",
            "resource": "/products/5"
          }
        },
        {
          "type": "InvalidProductOption",
          "product": {
            "id": 6,
            "name": "[Sample Product] MacBook Pro",
            "value": 222,
            "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/6.json",
            "resource": "/products/6"
          }
        },
        {
          "type": "InvalidProductOptionValue",
          "product": {
            "id": 6,
            "name": "[Sample Product] MacBook Pro",
            "product_option": {
              "id": 24,
              "option_id": 7,
              "display_name": "Video Memory",
              "value": 300,
              "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/6/options/24.json",
              "resource": "/products/6/options/24"
            },
            "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/6.json",
            "resource": "/products/6"
          }
        }
      ]
    }
  }
]
</pre>

### PUT orders/id.json

UPDATE an order from a store. Orders PUT supports the same fields as the POST method. Refer to the <a href="#post-ordersjson">order POST documentation</a> for more information on what the resource supports, its caveats and sample input.

The following fields will trigger a recalculation of the subtotal and total.

- products
- discount_amount
- shipping_cost_ex_tax
- shipping_cost_inc_tax
- handling_cost_ex_tax
- handling_cost_inc_tax
- wrapping_cost_ex_tax
- wrapping_cost_inc_tax
- billing_address
- shipping_addresses

__NOTE:__ *Be wary that the Orders API currently does not support coupon redemptions and discounts apart from manual discount. You should ideally only modify the above fields if you have created the order via the POST API or you are overriding the subtotals and totals manually.*


#### Request


<table class="table table-bordered ">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>description</th>
   </tr>
  </thead>
  <tbody>
	<tr>
  		<td>id</td>
  		<td>int</td>
  		<td>The ID of the order.</td>
  	</tr>
  	<tr>
  		<td>customer_id</td>
  		<td>int</td>
  		<td>The ID of the customer placing the order or 0 if it was a guest order.</td>
  	</tr>
  	<tr>
  		<td>date_created</td>
  		<td>date</td>
  		<td>The date this order was created, if not specified will default to current time. The date should be in RFC format - 'Tue, 20 Nov 2012 00:00:00 +0000'</td>
  	</tr>
  	<tr>
  		<td>status_id</td>
  		<td>int</td>
  		<td>The status ID from <a href="/api/orderstatuses/">orderstatuses</a> documentation.</td>
  	</tr>
  	<tr>
  		<td>subtotal_ex_tax</td>
  		<td>decimal</td>
  		<td>Override value for subtotal excluding tax. If specified, the field subtotal_inc_tax is also required.</td>
  	</tr>
  	<tr>
  		<td>subtotal_inc_tax</td>
  		<td>decimal</td>
  		<td>Override value for subtotal including tax. If specified, the field subtotal_ex_tax is also required.</td>
  	</tr>
  	<tr>
  		<td>base_shipping_cost</td>
  		<td>decimal</td>
  		<td>The value of the base shipping cost</td>
  	</tr>
  	<tr>
  		<td>shipping_cost_ex_tax</td>
  		<td>decimal</td>
  		<td>The value of shipping cost excluding tax</td>
  	</tr>
  	<tr>
  		<td>shipping_cost_inc_tax</td>
  		<td>decimal</td>
  		<td>The value of shipping cost including tax</td>
  	</tr>
  	<tr>
  		<td>base_handling_cost</td>
  		<td>decimal</td>
  		<td>The value of the base handling cost</td>
  	</tr>
  	<tr>
  		<td>handling_cost_ex_tax</td>
  		<td>decimal</td>
  		<td>The value of the handling cost excluding tax</td>
  	</tr>
  	<tr>
  		<td>handling_cost_inc_tax</td>
  		<td>decimal</td>
  		<td>The value of the handling cost including tax</td>
  	</tr>
  	<tr>
  		<td>base_wrapping_cost</td>
  		<td>decimal</td>
  		<td>The value of the base wrapping cost</td>
  	</tr>
  	<tr>
  		<td>wrapping_cost_inc_tax</td>
  		<td>decimal</td>
  		<td>The value of the wrapping cost including tax</td>
  	</tr>
  	<tr>
  		<td>wrapping_cost_ex_tax</td>
  		<td>decimal</td>
  		<td>The value of the wrapping cost including tax</td>
  	</tr>
  	<tr>
  		<td>total_ex_tax</td>
  		<td>decimal</td>
  		<td>Override value for the total, excluding tax. If specified, the field total_inc_tax is also required.</td>
  	</tr>
  	<tr>
  		<td>total_inc_tax</td>
  		<td>decimal</td>
  		<td>Override value for the total, including tax. If specified, the field total_ex_tax is also required.</td>
  	</tr>
  	<tr>
  		<td>items_shipped</td>
  		<td>int</td>
  		<td>The number of items that has been shipped.</td>
  	</tr>
  	<tr>
  		<td>payment_method</td>
  		<td>string</td>
  		<td>The payment method for this order.</td>
  	</tr>
  	<tr>
  		<td>payment_provider_id</td>
  		<td>string</td>
  		<td>The ID of the payment provider if payment provier was used.</td>
  	</tr>
  	<tr>
  		<td>refunded_amount</td>
  		<td>decimal</td>
  		<td>The amount refunded from this transaction.</td>
  	</tr>
  	<tr>
  		<td>order_is_digital</td>
  		<td>boolean</td>
  		<td>Whether this order is an order for digital products.</td>
  	</tr>
  	<tr>
  		<td>ip_address</td>
  		<td>string</td>
  		<td>IP Address of the customer if known.</td>
  	</tr>
  	<tr>
  		<td>geoip_country</td>
  		<td>string</td>
  		<td>The full country name where the customer made the purchase based on the IP.</td>
  	</tr>
  	<tr>
  		<td>geoip_country_iso2</td>
  		<td>string</td>
  		<td>The country where the customer made the purchase based on the IP is ISO2 format.</td>
  	</tr>
  	<tr>
  		<td>currency_id</td>
  		<td>int</td>
  		<td>The ID of the currency being used in this transaction.</td>
  	</tr>
  	<tr>
  		<td>currency_code</td>
  		<td>string</td>
  		<td>The currency code of the currency being used in this transaction</td>
  	</tr>
  	<tr>
  		<td>currency_exchage_rate</td>
  		<td>decimal</td>
  		<td>The exchange rate of the currency being used against the store's default currency.</td>
  	</tr>
  	<tr>
  		<td>defaut_currency_id</td>
  		<td>int</td>
  		<td>The ID of the default currency for this type of transaction.</td>
  	</tr>
  	<tr>
  		<td>default_currency_code</td>
  		<td>string</td>
  		<td>The currency code of the default currency for this type of transaction</td>
  	</tr>
  	<tr>
  		<td>staff_notes</td>
  		<td>text</td>
  		<td>Any additional notes for staff.</td>
  	</tr>
  	<tr>
  		<td>customer_message</td>
  		<td>text</td>
  		<td>Message for the customer.</td>
  	</tr>
  	<tr>
  		<td>discount_amount</td>
  		<td>text</td>
  		<td>Amount of discount for this transaction.</td>
  	</tr>
  	<tr>
  		<td>billing_address</td>
  		<td>object</td>
  		<td>The billing address of the customer. See: "Address Fields"</td>
  	</tr>
  	<tr>
  		<td>shipping_addresses</td>
  		<td>object_array</td>
  		<td>The shipping addresses for this order. See: "Address Fields"</td>
  	</tr>
  	<tr>
  		<td>external_source</td>
  		<td>string</td>
  		<td>The name of the external source where this order was made. e.g: POS</td>
  	</tr>
  	<tr>
  		<td>products</td>
  		<td>object_array</td>
  		<td>The products being purchased in this transaction. See: "Product Fields"</td>
  	</tr>
  	
  </tbody>
</table>

#### Address Fields

<table class="table table-bordered ">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>description</th>
   </tr>
  </thead>
  <tbody>
  	<tr>
  		<td>id</td>
  		<td>int</td>
  		<td>The ID of the order shipping address</td>
  	</tr>
  	<tr>
  		<td>first_name</td>
  		<td>string</td>
  		<td>Contact first name</td>
  	</tr>
  	<tr>
  		<td>last_name</td>
  		<td>string</td>
  		<td>Contact last name</td>
  	</tr>
  	<tr>
  		<td>company</td>
  		<td>string</td>
  		<td>Company name</td>
  	</tr>
  	<tr>
  		<td>street_1</td>
  		<td>string</td>
  		<td>Line 1 of street address</td>
  	</tr>
  	<tr>
  		<td>street_2</td>
  		<td>string</td>
  		<td>Line 2 of street address</td>
  	</tr>
  	<tr>
  		<td>city</td>
  		<td>string</td>
  		<td>Name of city</td>
  	</tr>
  	<tr>
  		<td>zip</td>
  		<td>string</td>
  		<td>Zip or postal code</td>
  	</tr>
  	<tr>
  		<td>country</td>
  		<td>string</td>
  		<td>Country full name</td>
  	</tr>
  	<tr>
  		<td>country_iso2</td>
  		<td>string</td>
  		<td>Country code in ISO 3166-1 alpha-2 format. (e.g: US, AU)</td>
  	</tr>
  	<tr>
  		<td>state</td>
  		<td>string</td>
  		<td>State/province name</td>
  	</tr>
  	<tr>
  		<td>email</td>
  		<td>string</td>
  		<td>Contact email address</td>
  	</tr>
  	<tr>
  		<td>phone</td>
  		<td>string</td>
  		<td>Contact phone number</td>
  	</tr>
  </tbody>
</table>

#### Product Fields

<table class="table table-bordered ">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>description</th>
   </tr>
  </thead>
  <tbody>
	<tr>
  		<td>id</td>
  		<td>int</td>
  		<td>The ID of the order product</td>
  	</tr>
  	<tr>
  		<td>product_id</td>
  		<td>int</td>
  		<td>The ID of the product</td>
  	</tr>
  	<tr>
  		<td>quantity</td>
  		<td>int</td>
  		<td>The quantity of the purchase for this product</td>
  	</tr>
  	<tr>
  		<td>price_inc_tax</td>
  		<td>decimal</td>
  		<td>The override value for the price including tax. If specified, you will also need to specify "price_ex_tax". If NOT specified, store price will be used.</td>
  	</tr>
  	<tr>
  		<td>price_ex_tax</td>
  		<td>decimal</td>
  		<td>The override value for the price excluding tax. If specified, you will also need to specify "price_inc_tax". If NOT speicified, store price will be used.</td>
  	</tr>
  	<tr>
  		<td>product_options</td>
  		<td>object_array</td>
  		<td>The options chosen for this product purchase. See: "Options Fields"</td>
  	</tr>
  </tbody>
</table>

#### Options Fields

<table class="table table-bordered ">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>description</th>
   </tr>
  </thead>
  <tbody>
  	<tr class="mandatory">
  		<td>id</td>
  		<td>int</td>
  		<td>The ID of the <a href="/api/products/options">product option</a></td>
  	</tr>
  	<tr class="mandatory">
  		<td>value</td>
  		<td>text</td>
  		<td>The value for the option from <a href="/api/options/values">/options/values</a></td>
  	</tr>
  </tbody>
</table>

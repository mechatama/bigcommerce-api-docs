## Resources
<table class="table table-bordered ">
  <thead>
   <tr>
     <th>Resource</th>
   </tr>
 </thead>
 <tbody>
   <tr>
     <td><a href="#get-couponsjson">GET  /coupons.json</a></td>
   </tr>
   <tr>
     <td><a href="#get-couponsidjson">GET /coupons/id.json</a></td>
   </tr>

   <tr>
     <td><a href="#post-couponsjson">POST /coupons.json </a></td>
   </tr>

   <tr>
     <td><a href="#get-couponsidjson">GET /coupons/id.json</a></td>
   </tr>

   <tr>
     <td><a href="#put-couponsidjson">PUT /coupons/id.json</a></td>
   </tr>

   <tr>
     <td><a href="#delete-couponsjson">DELETE /coupons.json</a></td>
   </tr>

   <tr>
     <td><a href="#delete-couponsidjson">DELETE /coupons/id.json</a></td>
   </tr>

 </tbody>
</table>

## Description
### GET coupons.json
GET coupons from a store

#### Request
These fields can be used to filter the query. By default, without any filters, the GET request returns the first 50 coupons.

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
     <td>min_id</td>
     <td>int</td>
     <td>The minimum ID of the coupon</td>
   </tr>
   <tr>
     <td>max_id</td>
     <td>int</td>
     <td>The maximum ID of the coupon</td>
   </tr>
   <tr>
     <td>limit</td>
     <td>int</td>
     <td>The number of coupons your query should return (the max is 250 per page)</td>
   </tr>
   <tr>
     <td>page</td>
     <td>int</td>
     <td>The page number of the results. If you have say 300 coupons, you can use the page=1&limit=200 to get the first 200 coupons and increment the page counter to get the next 100.</td>
   </tr>
   <tr>
     <td>id</td>
     <td>int</td>
     <td>coupon id</td>
   </tr>
   <tr>
     <td>code</td>
     <td>string</td>
     <td>coupon code</td>
   </tr>
   <tr>
     <td>name</td>
     <td>string</td>
     <td>coupon name</td>
   </tr>
   <tr>
     <td>type</td>
     <td>string</td>
     <td>coupon type</td>
   </tr>
  </tbody>
</table>

#### Response
List of coupons

<pre>
[{
    "id": 1,
    "name": "5% off order total",
    "type": "per_item_discount",
    "amount": "5.0000",
    "min_purchase": "0.0000",
    "expires": "",
    "enabled": true,
    "code": "4F75AF0C3802D39",
    "applies_to": {
        "entity": "categories",
        "ids": [0]
    },
    "num_uses": 0,
    "max_uses": 0,
    "max_uses_per_customer": 0,
    "restricted_to": {
        "countries": ["AU"]
    },
    "shipping_methods": null
}, {
    "id": 2,
    "name": "10% off order total",
    "type": "per_item_discount",
    "amount": "10.0000",
    "min_purchase": "0.0000",
    "expires": "",
    "enabled": true,
    "code": "CBD1455FDA13815",
    "applies_to": {
        "entity": "categories",
        "ids": [0]
    },
    "num_uses": 0,
    "max_uses": 0,
    "max_uses_per_customer": 0,
    "restricted_to": {
        "states": {
            "AU": ["Australian Capital Territory"]
        }
    },
    "shipping_methods": null
}, {
    "id": 3,
    "name": "Free shipping",
    "type": "free_shipping",
    "amount": "0.0000",
    "min_purchase": "0.0000",
    "expires": "",
    "enabled": true,
    "code": "7E97D5F3F75FA2D",
    "applies_to": {
        "entity": "categories",
        "ids": [0]
    },
    "num_uses": 0,
    "max_uses": 0,
    "max_uses_per_customer": 0,
    "restricted_to": {
        "zips": {
            "AU": ["2000", "20??"]
        }
    },
    "shipping_methods": null
}, {
    "id": 4,
    "name": "$5 off shipping",
    "type": "shipping_discount",
    "amount": "5.0000",
    "min_purchase": "0.0000",
    "expires": "",
    "enabled": true,
    "code": "DC0C1CC8807DAC8",
    "applies_to": {
        "entity": "categories",
        "ids": [0]
    },
    "num_uses": 0,
    "max_uses": 0,
    "max_uses_per_customer": 0,
    "restricted_to": null,
    "shipping_methods": null
}, {
    "id": 5,
    "name": "only for shipping_flatrate",
    "type": "0",
    "amount": "0.0000",
    "min_purchase": "100.0000",
    "expires": "Thu, 31 Jan 2013 00:00:00 +0000",
    "enabled": false,
    "code": "shippingFlatrate-2",
    "applies_to": {
        "entity": "products",
        "ids": [32]
    },
    "num_uses": 0,
    "max_uses": 10,
    "max_uses_per_customer": 0,
    "restricted_to": null,
    "shipping_methods": ["shipping_flatrate"]
}]
</pre>

### POST coupons.json
Create coupons in a store

#### Request
The POST request allows following fields. Mandatory fields are in bold.

<table class="table table-bordered">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>description</th>
   </tr>
 </thead>
 <tbody>

   <tr>
     <td><b>name</b></td>
     <td>string</td>
     <td>The name of the coupon.</td>
   </tr>

   <tr>
     <td><b>code</b></td>
     <td>string</td>
     <td>The coupon code which customers will use to receive their discounts. Must be Unique.</td>
   </tr>

   <tr>
     <td><b>type</b></td>
     <td>enum</td>
     <td>The coupon type field is an enumerated field and a value from the following list should be used.
        <ul><li>per_item_discount</li>
            <li>per_total_discount</li>
            <li>shipping_discount</li>
            <li>free_shipping</li>
            <li>percentage_discount</li>
        </ul>
     </td>
   </tr>

   <tr>
     <td><b>amount</b></td>
     <td>decimal</td>
     <td>The amount is a decimal field which can either be the monetary discount to be applied to an order or a percentage discount to be applied to an order. The type of this field is determined by the coupon type.</td>
   </tr>

   <tr>
     <td>min_purchase</td>
     <td>decimal</td>
     <td>This is a decimal field which specifies the minimum value an order must have before the coupon can be applied to it.</td>
   </tr>

   <tr>
     <td>enabled</td>
     <td>boolean</td>
     <td>True, if coupon is enabled. False otherwise.</td>
   </tr>

   <tr>
     <td>expires</td>
     <td>date</td>
     <td>This is a date field which specifies when a coupon expires. Coupons need not have an expiry date as you can also control expiry via max_uses and max_uses_per_customer. The date field must be formatted as per <a href="http://tools.ietf.org/html/rfc2822#section-3.3">RFC-2822</a>.</td>
   </tr>

   <tr>
     <td>applies_to</td>
     <td>object</td>
     <td>This object provides
         <ul>
             <li>ability to restrict a coupon to an entity type (category/product)</li>
             <li>and ability to restrict a coupon specific categories/products, where 0 is all categories/products.</li>
        </ul>
     </td>
   </tr>

   <tr>
     <td>num_uses</td>
     <td>integer</td>
     <td>Number of times this coupon has been used. This is a readonly field and can't be changed via PUT or POST.</td>
   </tr>

   <tr>
     <td>max_uses</td>
     <td>integer</td>
     <td>Maximum number of times this coupon can be used.</td>
   </tr>

   <tr>
     <td>max_uses_per_customer</td>
     <td>integer</td>
     <td>Maximum number of times each customer can use this coupon.</td>
   </tr>

   <tr>
     <td>restricted_to</td>
     <td>array</td>
     <td>This field provides the ability to restrict coupon usage based on locations as follows
     <ul>
     <li>If a coupon is restricted by country then a list of ISO2 country codes is provided. To retrieve these you can do a GET request on /countries.json endpoint.
<pre>
"restricted_to": {
    "countries": ["AU"]
}
</pre>
     </li>
     <li>If a coupon is restricted by states then a list of state names is provided indexed by the ISO2 country code for each country. To retrieve these you can do a GET request on /countries.json endpoint and then a GET request on /countries/:id/states.json endpoint.
<pre>
"restricted_to": {
    "states": {
        "AU": ["Australian Capital Territory"]
    }
}
</pre>
     </li>
     <li>If a coupon is restricted by zip codes then a list of zip codes indexed by the ISO2 country code for each country is provided as follows. Please refer to this <a href="http://www.viewkb.com/inlinehelp.php?searchOverride=86&tplHeader=Bigcommerce&helpid=850">KB article</a>
<pre>
"restricted_to": {
    "zips": {
        "AU": ["2000", "20??"]
    }
}
</pre>
     </li>
     </ul>
     </td>
   </tr>

   <tr>
     <td>shipping_methods</td>
     <td>array</td>
     <td>This is a list of shipping method names. If a shipping method isn't enabled on the store it can't be used to with a coupon. To check which shipping methods are enabled please do a GET request on the /shipping/methods.json endpoint.</td>
   </tr>

 </tbody>
</table>

#### Response
Creates a coupon
<pre>
{
    "id": 1,
    "name": "5% off order total",
    "type": "per_item_discount",
    "amount": "5.0000",
    "min_purchase": "0.0000",
    "expires": "",
    "enabled": true,
    "code": "4F75AF0C3802D39",
    "applies_to": {
        "entity": "categories",
        "ids": [0]
    },
    "num_uses": 0,
    "max_uses": 0,
    "max_uses_per_customer": 0,
    "restricted_to": null,
    "shipping_methods": null
}
</pre>


### GET coupons/id.json
GET a coupon from a store

#### Request
This GET request does not take any parameters.

#### Response
coupon by ID

<pre>
{
    "id": 1,
    "name": "5% off order total",
    "type": "per_item_discount",
    "amount": "5.0000",
    "min_purchase": "0.0000",
    "expires": "",
    "enabled": true,
    "code": "4F75AF0C3802D39",
    "applies_to": {
        "entity": "categories",
        "ids": [0]
    },
    "num_uses": 0,
    "max_uses": 0,
    "max_uses_per_customer": 0,
    "restricted_to": null,
    "shipping_methods": null
}
</pre>

### PUT coupons/id.json
UPDATE a coupon from a store

#### Request
This PUT request can take any field that the POST request takes with the exception of the _id_ field as its _readonly_. All fields are optional thus allowing the ability to only PUT those fields that you wish to update. Please refer to the POST section of this document for an explanation of all the fields.

#### Response
A successful put udpates a coupon in the store and responds with the entire coupon metadata

<pre>
{
    "id": 1,
    "name": "5% off order total",
    "type": "per_item_discount",
    "amount": "5.0000",
    "min_purchase": "0.0000",
    "expires": "",
    "enabled": true,
    "code": "4F75AF0C3802D39",
    "applies_to": {
        "entity": "categories",
        "ids": [0]
    },
    "num_uses": 0,
    "max_uses": 0,
    "max_uses_per_customer": 0,
    "restricted_to": null,
    "shipping_methods": null
}
</pre>


Here are resources to delete coupons. This is a destructive operation. Remember that you cannot recover deleted coupons.

### DELETE coupons.json
DELETE all coupons

### DELETE coupons/id.json
DELETE a coupon


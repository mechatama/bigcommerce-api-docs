## Resources

<table class="table table-bproducted ">
  <thead>
   <tr>
     <th>Resource</th>
   </tr>
 </thead>
 <tbody>

   <tr>
     <td><a href="#get-productsidrulesjson">GET /products/id/rules.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#post-productsidrulesjson">POST /products/id/rules.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#get-productsidrulesidjson">GET /products/id/rules/id.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#get-productsidrulescountjson">GET /products/id/rules/count.json</a></td>
     
   </tr>

   <tr>
     <td><a href="#delete-productsidrulesjson">DELETE /products/id/rules.json</a></td>
     
   </tr>

   <tr>
     <td><a href="#delete-productsidrulesidjson">DELETE /products/id/rules/id.json</a></td>
     
   </tr>
   
 </tbody>
</table>
   
## Description

### GET products/id/rules.json
GET all rules for an product

#### Request
This GET request does not take any parameters.

#### Response
product by ID
<pre>
[
    {
        "id": 1,
        "product_id": 3,
        "sort_order": 0,
        "is_enabled": true,
        "is_stop": false,
        "price_adjuster": null,
        "weight_adjuster": null,
        "is_purchasing_disabled": false,
        "purchasing_disabled_message": "",
        "is_purchasing_hidden": false,
        "image_file": "attribute_rule_images/1_source.jpg",
        "conditions": [
            {
                "product_option_id": 4,
                "option_value_id": 7,
                "sku_id": null
            }
        ]
    },
    {
        "id": 2,
        "product_id": 3,
        "sort_order": 1,
        "is_enabled": true,
        "is_stop": false,
        "price_adjuster": null,
        "weight_adjuster": null,
        "is_purchasing_disabled": false,
        "purchasing_disabled_message": "",
        "is_purchasing_hidden": false,
        "image_file": "attribute_rule_images/2_source.jpg",
        "conditions": [
            {
                "product_option_id": 4,
                "option_value_id": 8,
                "sku_id": null
            }
        ]
    },
    ...
]
</pre> 

### POST products/id/rules.json
create a product rule

#### Request
This request allows the following fields
<!-- do not change this. for rendering on the main site -->
<style type="text/css">
tr.mandatory {
  color: aliceblue;
}
</style>
<!-- style complete -->

<table class="table table-bordered">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>description</th>
   </tr>
  </thead>
  <tbody>
   <tr class="mandatory">
     <td >product_id</td>
     <td>integer</td>
     
     <td>The ID of the product the rule belongs to</td>
   </tr>
   <tr>
     <td>image_file</td>
     <td>string</td>
     
     <td>When specifying a product rule, the image_file should be specified as either: A path to an rule already uploaded via FTP in the import directory and the path should be relative from the import directory. It can be a URL to an rule accessible on the internet.</td>
   </tr>
   <tr >
     <td >is_thumbnail</td>
     <td>boolean</td>
     
     <td>If true, the rule is used as product thumbnail</td>
   </tr>
   <tr >
     <td >sort_order</td>
     <td>integer</td>
     
     <td>The order in which the rule will be displayed on the product page. When updating if the rule is given a lower priority, all rule with a sort_order the same or greater than the rules new sort_order value will have their sort_order reordered</td>
   </tr>
   <tr >
     <td >description</td>
     <td>text</td>
     
     <td>The description for the rule</td>
   </tr>

   <tr >
     <td >is_enabled</td>
     <td>boolean</td>
     
     <td>If set to true, the rule will be evaluated when a customer configures a products options.</td>
   </tr>

  <tr >
     <td >is_stop</td>
     <td>boolean</td>
     
     <td>If set to true and the rule evaluates to true, no more rules with a higher sort_order will be processed. </td>
   </tr>

  <tr >
     <td >price_adjuster</td>
     <td>object</td>
     
     <td>See the adjuster object definition below</td>
   </tr>

    <tr >
     <td >weight_adjuster</td>
     <td>object</td>
     
     <td>See the adjuster object definition below</td>
   </tr>
  
  <tr >
     <td >is_purchasing_disabled</td>
     <td>boolean</td>
     
     <td>If true this rule prohibits purchasing the product with the configured option values. </td>
   </tr>

   <tr >
     <td >purchasing_disabled_message</td>
     <td>string</td>
     
     <td>The message to display if the rule disabled purchasing the product. </td>
   </tr>

   <tr >
     <td >is_purchasing_hidden</td>
     <td>boolean</td>
     
     <td>If true the rule hides the options on the product. Setting this to true has no effect if the rule is based on an SKU or has conditions from multiple product options.</td>
   </tr>
   
   <tr >
     <td >conditions</td>
     <td>object</td>
     
     <td>See the conditions object definition below</td>
   </tr>
  </tbody>
</table>

#### Price/Weight Adjustor
<table class="table table-bordered">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>description</th>
   </tr>
  </thead>
  <tbody>
   <tr class="">
     <td >adjustor</td>
     <td>enum</td>
     
     <td>The adjuster for this rule: 
      <ul>
      <li>percent - Reduce or increase the price/weight based by the percentage in the adjuster_value field. For example, setting adjuster_value for a price to 5.25 will increase the price of the product by 5.25%.</li>
      <li>relative - Reduce or increase the price/weight based by the relative value in the adjuster_value field. The adjuster_value field is assumed to be the store's default currency or weight.</li>
      <li>absolute - Set the price/weight based to the value in the adjuster_value field, regardless of any adjustments made by higher priority rules.</li>
    </ul>
  </td>
   </tr>
   <tr >
     <td >adjustor_value</td>
     <td>decimal</td>
     
     <td>The value that which the rule will adjust the product by.</td>
   </tr>
   
  </tbody>
</table>

#### price Adjustor
<table class="table table-bordered">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>description</th>
   </tr>
  </thead>
  <tbody>
   <tr class="">
     <td >product_option_id</td>
     <td>int</td>
     
     <td>The ID of the product option this condition will test against. </td> 
      
   </tr>
   <tr class="">
     <td >option_value_id</td>
     <td>int</td>
     
     <td>The ID of the option value this condition will test against. </td> 
      
   </tr>
   <tr class="">
     <td >sku_id</td>
     <td>int</td>
     
     <td>The ID of the sku this condition will test against. </td> 
      
   </tr>
   
   
  </tbody>
</table>

#### Response
new rule for an product
<pre>
{
        "id": 10,
        "product_id": 3,
        "sort_order": 1,
        "is_enabled": true,
        "is_stop": false,
        "price_adjuster": null,
        "weight_adjuster": null,
        "is_purchasing_disabled": false,
        "purchasing_disabled_message": "",
        "is_purchasing_hidden": false,
        "image_file": "attribute_rule_images/2_source.jpg",
        "conditions": [
            {
                "product_option_id": 4,
                "option_value_id": 8,
                "sku_id": null
            }
        ]
    }
</pre> 


### GET products/id/rules/id.json
GET a specific rule


#### Request
This GET request does not take any parameters.


#### Response
product rule by ID
<pre>
{
    "id": 2,
    "product_id": 3,
    "sort_order": 1,
    "is_enabled": true,
    "is_stop": false,
    "price_adjuster": null,
    "weight_adjuster": null,
    "is_purchasing_disabled": false,
    "purchasing_disabled_message": "",
    "is_purchasing_hidden": false,
    "image_file": "attribute_rule_images/2_source.jpg",
    "conditions": [
        {
            "product_option_id": 4,
            "option_value_id": 8,
            "sku_id": null
        }
    ]
}
</pre>

### PUT products/id/rules/id.json
update a specific rule


#### Request
This PUT request takes following parameters.
<table class="table table-bordered">
<thead>
 <tr>
   <th style="width: 100px;">Field</th>
   <th style="width: 50px;">Type</th>
   <th>description</th>
 </tr>
</thead>
<tbody>
 <tr class="mandatory">
   <td >product_id</td>
   <td>integer</td>
   
   <td>The ID of the product the rule belongs to</td>
 </tr>
 <tr>
   <td >image_file</td>
   <td>string</td>
   
   <td>When specifying a product rule, the image_file should be specified as either: A path to an rule already uploaded via FTP in the import directory and the path should be relative from the import directory. It can be a URL to an rule accessible on the internet.</td>
 </tr>
 <tr >
   <td >is_thumbnail</td>
   <td>boolean</td>
   
   <td>If true, the rule is used as product thumbnail</td>
 </tr>
 <tr >
   <td >sort_order</td>
   <td>integer</td>
   
   <td>The order in which the rule will be displayed on the product page. When updating if the rule is given a lower priority, all rule with a sort_order the same or greater than the rules new sort_order value will have their sort_order reordered</td>
 </tr>
 <tr >
   <td >description</td>
   <td>text</td>
   
   <td>The description for the rule</td>
 </tr>
 
</tbody>
</table>

#### Response
Update product rule by ID
<pre>
{
    "id": 2,
    "product_id": 3,
    "sort_order": 2,
    "is_enabled": true,
    "is_stop": false,
    "price_adjuster": null,
    "weight_adjuster": null,
    "is_purchasing_disabled": false,
    "purchasing_disabled_message": "",
    "is_purchasing_hidden": false,
    "image_file": "attribute_rule_images/2_source.jpg",
    "conditions": [
        {
            "product_option_id": 4,
            "option_value_id": 8,
            "sku_id": null
        }
    ]
}  
</pre>

### GET products/id/rules/count.json
Get a total number of rules 

#### Request
This request does not take any parameters.

#### Response
Returns the number of product rules  
<pre>
  {
    "count": 2
  }
</pre>

### DELETE products/id/rules.json
DELETE all product rules

### DELETE products/id/rules/id.json
DELETE an product rule
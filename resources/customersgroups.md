
## About

Customer groups allow you to apply rules to particular segments of a store’s customer base. For example, the store might cater to both retail and wholesale customers who require access to different categories of products. Or the store might provide special discounts for certain groups such as students or senior citizens.

## Contents

### Reference

<table class="table table-bordered ">
 <tbody>
   <tr>
     <td><a href="#filters">Filters</a></td>
   </tr>
   <tr>
     <td><a href="#schema">Schema</a></td>
   </tr>
 </tbody>
</table>

### Resources

<table class="table table-bordered ">
 <tbody>
   <tr>
     <td><a href="#get-customer-groups">Get Customer Groups</a></td>
   </tr>
   <tr>
     <td><a href="#create-customer-group">Create Customer Group</a></td>
   </tr>
   <tr>
     <td><a href="#get-customer-group">Get Customer Group</a></td>
   </tr>
   <tr>
     <td><a href="#update-customer-group">Update Customer Group</a></td>
   </tr>
   <tr>
     <td><a href="#get-customer-groups-count">Get Customer Groups Count</a></td>
   </tr>
   <tr>
     <td><a href="#delete-customer-groups">Delete Customer Groups</a></td>
   </tr>
   <tr>
     <td><a href="#delete-customer-group">Delete Customer Group</a></td>
   </tr>
 </tbody>
</table>

## Reference

## Filters

These fields can be used to filter the query. By default, without any filters, the GET request returns the first 50 groups.

<table class="table table-bordered ">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>Description</th>
   </tr>
  </thead>
  <tbody>
   <tr>
     <td>limit</td>
     <td>int</td>
     <td>The number of groups your query should return (the max is 250 per page)</td>
   </tr>
   <tr>
     <td>page</td>
     <td>int</td>
     <td>The page number of the results. If you have say 300 groups, you can use the page=1&limit=200 to get the first 200 groups and increment the page counter to get the next 100.</td>
   </tr>
   <tr>
     <td>name</td>
     <td>string</td>
     <td>Name of the group</td>
   </tr>
   <tr>
     <td>is_default</td>
     <td>boolean</td>
     <td>Whether customers are assigned to these groups by default</td>
   </tr>
  </tbody>
</table>

## Schema

Any combination of the following fields can be sent to create or update a customer group:

<table class="table table-bordered">
  <thead>
   <tr>
     <th style="width: 100px;">Field</th>
     <th style="width: 50px;">Type</th>
     <th>Description</th>
   </tr>
 </thead>
 <tbody>
   <tr>
     <td>name (required)</td>
     <td>string</td>
     <td>Name of the group</td>
   </tr>
   <tr>
     <td>is_default</td>
     <td>boolean</td>
     <td>Determines whether new customers are assigned to this group by default</td>
   </tr>
    <tr>
     <td>category_access</td>
     <td>object</td>
     <td>Determines which categories customers in this group have access to view and order products from.

        <p><strong>type</strong> is an enum specifying the method of category access applied to customers in this group:
            <ul>
                <li><strong>all</strong>: customers can access all categories</li>
                <li><strong>specific</strong>: customers can access a specific list of categories</li>
                <li><strong>none</strong>: customers are prevented from viewing any of the categories in this group</li>
            </ul>
        </p>
        <p><strong>categories</strong> is an array of category ids and should only be supplied if <b>type</b> is <b>specific</b>.</p>
    </td>
   </tr>
    <tr>
     <td>discount_rules</td>
     <td>object_array</td>
     <td>A collection of discount rules which are automatically applied for customers who are members of the group.

        <p>All discount rules have the following properties:</p>

        <p><strong>type</strong> is an enum specifying the type of discount rule:
            <ul>
                <li><strong>all</strong>: a store-wide rule (applies to everything)</li>
                <li><strong>product</strong>: a rule applying to a specific product</li>
                <li><strong>category</strong>: a rule applying to a specific category</li>
            </ul>
        </p>
        <p><strong>method</strong> is an enum which specifies a price modifying strategy:
            <ul>
                <li><strong>price</strong> modify the price by the given amount</li>
                <li><strong>percent</strong> modify the price by the given percentage</li>
                <li><strong>fixed</strong> modify the price with a fixed discount</li>
            </ul>
        </p>
        <p><strong>amount</strong> is a decimal which specifies the value applied to the price modifier</p>

        <p><strong>product</strong> and <strong>category</strong> rules also require a <strong>product_id</strong> or <strong>category_id</strong> field, respectively.</p>

    </td>
   </tr>
 </tbody>
</table>

## Resources

### Get Customer Groups

<pre>
GET /api/v2/customer_groups
</pre>

Gets the collection of customer groups.

#### Response

By default, without any filters, the request returns the entire collection.

<pre>
[
{
    "id":1,
    "name":"Retail Customers",
    "is_default":true,
    "category_access":{
        "type":"all"
    },
    "discount_rules":[]
},
{
    "id":2,
    "name":"Wholesale Customers",
    "is_default":false,
    "category_access":{
        "type":"all"
    },
    "discount_rules":[]
},
]
</pre>

### Create Customer Group

<pre>
POST /api/v2/customer_groups
</pre>

Creates a new customer group.

### Request

A minimal request requires only the customer group name:

<pre>
{
    "name": "Wholesale Customers"
}
</pre>

To assign all new customers to the group by default, set <strong>is default</strong> to true:

<pre>
{
    "name": "Retail Customers",
    "is_default": true
}
</pre>

To restrict customers in the group to only view and order products from a specific set of categories, provide a <strong>category access</strong> type:

<pre>
{
    "name": "Bulk Purchasers",
    "category_access": {
        "type": "specific",
        "categories": [7, 12, 20]
    }
}
</pre>

To provide a 5% store-wide discount for customers in the group, provide a <strong>discount rule</strong> of type <strong>all</strong>:

<pre>
{
    "name": "Student Discounts",
    "discount_rules": 
    [{
        "type": "all",
        "method": "percent",
        "amount": 5.00
    }]
}
</pre>

### Get Customer Group

<pre>
GET /api/v2/customer_groups/{id}
</pre>

Returns a single customer group.

#### Response

<pre>
{
    "id":3,
    "name":"Student Discounts",
    "is_default":true,
    "category_access":{
        "type":"all"
    },
    "discount_rules":[
     {
        "type":"percent",
        "method":true,
        "amount":"5.0000"
     }
    ]
}
}
</pre>

### Update Customer Group

<pre>
PUT /api/v2/customer_groups/{id}
</pre>

Updates the given customer group.

#### Request

Any combination of fields can be updated at once. Discount rules are treated in bulk. The entire set of rules is overwritten when a request is sent.

The following request will remove any existing rules, and apply the new ones:

<pre>
    {
        "discount_rules": [
            {
                "type": "all",
                "method": "percent",
                "amount": 2.50
            },
            {
                "type": "product",
                "product_id": 33,
                "method": "percent",
                "amount": 5.00
            },
            {
                "type": "category",
                "category_id": 7,
                "method": "price",
                "amount": 12.00
            }
        ]
    }
</pre>

### Get Customer Groups Count

<pre>
GET /api/v2/customer_groups/count
</pre>

Get a total number of customers in the store.

#### Response

<pre>
  {
    "count": 10
  }
</pre>

### Delete Customer Groups

<pre>
DELETE /api/v2/customer_groups
</pre>


Bulk deletes a collection of customer groups.

If no filter is supplied the entire collection is deleted.

### Delete Customer Group

<pre>
DELETE /api/v2/customer_groups/{id}
</pre>

Deletes a single customer group.

All existing customers are unassigned from the group when it is deleted.

## Resources
<table class="table table-bordered ">
  <thead>
   <tr>
     <th>Resource</th>
   </tr>
 </thead>
 <tbody>
   <tr>
     <td><a href="#get-customersjson">GET /customers.json</a></td>
   </tr>
   <tr>
     <td><a href="#post-customersjson">POST /customers.json</a></td>
   </tr>   
   <tr>
     <td><a href="#get-customersidjson">GET /customers/id.json</a></td>
   </tr>
   <tr>
     <td><a href="#put-customersidjson">PUT /customers/id.json</a></td>
   </tr>
   <tr>
     <td><a href="#get-customerscountjson">GET /customers/count.json</a></td>
   </tr>
   <tr>
     <td><a href="#delete-customersjson">DELETE /customers.json</a></td>
   </tr>
   <tr>
     <td><a href="#delete-customersidjson">DELETE /customers/id.json</a></td>
   </tr>      
 </tbody>
</table>
   
## Description
### GET customers.json
GET customers from a store

#### Request
These fields can be used to filter the query. By default, without any filters, the GET request returns the first 50 customers.

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
     <td>The minimum ID of the customer</td>
   </tr>
   <tr>
     <td>max_id</td>
     <td>int</td>
     <td>The maximum ID of the customer</td>
   </tr>
   <tr>
     <td>limit</td>
     <td>int</td>
     <td>The number of customers your query should return (the max is 250 per page)</td>
   </tr>
   <tr>
     <td>page</td>
     <td>int</td>
     <td>The page number of the results. If you have say 300 customers, you can use the page=1&limit=200 to get the first 200 customers and increment the page counter to get the next 100.</td>
   </tr>
   <tr>
     <td>first_name</td>
     <td>string</td>
     <td>First name of customer</td>
   </tr>
   <tr>
     <td>last_name</td>
     <td>string</td>
     <td>Last name of customer</td>
   </tr>
   <tr>
     <td>company</td>
     <td>string</td>
     <td>Company customer is part of</td>
   </tr>
   <tr>
     <td>email</td>
     <td>string</td>
     <td>Email address of the customer</td>
   </tr>
   <tr>
     <td>phone</td>
     <td>string</td>
     <td>Phone number of customer</td>
   </tr>
   <tr>
     <td>store_credit</td>
     <td>decimal</td>
     <td>The amount of credit the customer has</td>
   </tr>
   <tr>
     <td>customer_group_id</td>
     <td>int</td>
     <td>The group the customer belongs to</td>
   </tr>
   <tr>
     <td>min_date</td>
     <td>date</td>
     <td>The minimum creation date of the customer</td>
   </tr>
   <tr>
     <td>max_date</td>
     <td>date</td>
     <td>The maximumn creation date of the customer</td>
   </tr>
  </tbody>
</table>

#### Response
List of customers
<pre>
[
  {
      "id": 1,
      "company": "",
      "first_name": "Random ",
      "last_name": "Joe Bob",
      "email": "random.joebob@example.com",
      "phone": "252-101-2010",
      "date_created": "Tue, 13 Nov 2012 21:16:41 +0000",
      "date_modified": "Tue, 13 Nov 2012 21:16:41 +0000",
      "store_credit": "0.0000",
      "registration_ip_address": "50.58.18.2",
      "customer_group_id": 0,
      "notes": "",
      "addresses": {
          "url": "https://store-bwvr466.mybigcommerce.com/api/v2/customers/1/addresses.json",
          "resource": "/customers/1/addresses"
      }
  },
  {
      "id": 2,
      "company": "",
      "first_name": "Test",
      "last_name": "Customer",
      "email": "foo@randomcustomer.com",
      "phone": "",
      "date_created": "Wed, 14 Nov 2012 04:47:28 +0000",
      "date_modified": "Wed, 14 Nov 2012 04:47:28 +0000",
      "store_credit": "0.0000",
      "registration_ip_address": "99.191.105.74",
      "customer_group_id": 0,
      "notes": "",
      "addresses": {
          "url": "https://store-bwvr466.mybigcommerce.com/api/v2/customers/2/addresses.json",
          "resource": "/customers/2/addresses"
      }
  }
  ...
]
</pre>

### POST customers.json
Create a new customer

#### Request

The following fields are supported for creating customers. The `first_name`, `last_name` and `email` fields are required:

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
     <td>first_name</td>
     <td>string</td>
     
     <td>First name of customer</td>
   </tr>

   <tr class="mandatory">
     <td>last_name</td>
     <td>string</td>
     
     <td>Last name of customer</td>
   </tr>
   <tr class="mandatory">
     <td>email</td>
     <td>string</td>
     
     <td>Email address of the customer</td>
   </tr>
   <tr>
     <td>company</td>
     <td>string</td>
     
     <td>Company customer is part of</td>
   </tr>
   <tr>
     <td>phone</td>
     <td>string</td>
     
     <td>Phone number of customer</td>
   </tr>

   <tr>
     <td>store_credit</td>
     <td>decimal</td>
     
     <td>The amount of credit the customer has</td>
   </tr>
  <tr>
     <td>registration_ip_address</td>
     <td>string</td>
     
     <td>The IP address of the customer when they signed up</td>
   </tr>
   <tr>
     <td>customer_group_id</td>
     <td>int</td>
     
     <td>The group the customer belongs to</td>
   </tr>
  <tr>
     <td>notes</td>
     <td>string</td>
     
     <td>Store owner notes on the customer</td>
   </tr>
    <tr>
     <td>_authentication</td>
     <td>object</td>
     
     <td>The customer’s ability to log in to the store</td>
   </tr> 
 </tbody>
</table>

#### Managing Customer Authentication

The `_authentication` object exposes functionality associated with the customer’s ability to log in to your store.

When the `_authentication` object is not supplied in a request, the API will default to the following behaviour:

- When a customer is created via `POST` and a password value is not supplied, then a new password is generated
- When a customer is updated via `PUT` and a password value is not supplied, then the existing password remains the same.

All properties of the `_authentication` object are optional.

#### Creating and Updating Passwords

To manually write a customer password in the same way as the Control Panel, supply a value for the `password` field:

<pre>
{
    "_authentication": {
        "password": "12w69Y217PYR96J"
    }
}
</pre>

#### Confirming Passwords

An additional optional `password_confirmation` field can also be sent, providing password confirmation as a service:

<pre>
{
    "_authentication": {
       "password": "12w69Y217PYR96J"
       "password_confirmation": "12w69Y217PYR96J"
    }
}
</pre>

### GET customers/id.json
GET a customer from a store

#### Request
This GET request does not take any parameters.

#### Response
customer by ID
<pre>
{
    "id": 1,
    "company": "",
    "first_name": "Random ",
    "last_name": "Joe Bob",
    "email": "random.joebob@example.com",
    "phone": "252-101-2010",
    "date_created": "Tue, 13 Nov 2012 21:16:41 +0000",
    "date_modified": "Tue, 13 Nov 2012 21:16:41 +0000",
    "store_credit": "0.0000",
    "registration_ip_address": "50.58.18.2",
    "customer_group_id": 0,
    "notes": "",
    "addresses": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/customers/1/addresses.json",
        "resource": "/customers/1/addresses"
    }
}
</pre>    

### PUT customers/id.json

Any combination of the following fields can be edited on an existing customer resource:

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
     <td>first_name</td>
     <td>string</td>
     
     <td>First name of customer</td>
   </tr>

   <tr>
     <td>last_name</td>
     <td>string</td>
     
     <td>Last name of customer</td>
   </tr>
   <tr>
     <td>email</td>
     <td>string</td>
     
     <td>Email address of the customer</td>
   </tr>
   <tr>
     <td>company</td>
     <td>string</td>
     
     <td>Company customer is part of</td>
   </tr>
   <tr>
     <td>phone</td>
     <td>string</td>
     
     <td>Phone number of customer</td>
   </tr>

   <tr>
     <td>store_credit</td>
     <td>decimal</td>
     
     <td>The amount of credit the customer has</td>
   </tr>
  <tr>
     <td>registration_ip_address</td>
     <td>string</td>
     
     <td>The IP address of the customer when they signed up</td>
   </tr>
   <tr>
     <td>customer_group_id</td>
     <td>int</td>
     
     <td>The group the customer belongs to</td>
   </tr>
  <tr>
     <td>notes</td>
     <td>string</td>
     
     <td>Store owner notes on the customer</td>
   </tr>
    <tr>
     <td>_authentication</td>
     <td>object</td>
     
     <td>The customer’s ability to log in to the store</td>
   </tr> 
 </tbody>
</table>

### GET customers/count.json
Get a total number of customers in the store

#### Request
This request does not take any parameters.

#### Response
Returns the number of customers in the store 
<pre>
  {
    "count": 10
  }
</pre>

### DELETE customers.json
Bulk delete a collection of customers. If no filter is supplied the entire collection is removed.

### DELETE customers/id.json
Delete an individual customer.

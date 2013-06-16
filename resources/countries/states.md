## Resources

<table class="table table-bordered ">
  <thead>
   <tr>
     <th>Resource</th>
   </tr>
 </thead>
 <tbody>
   <tr>
     <td><a href="#get-countriestatesjson">GET  /countries/states.json</a></td>
     
   </tr>

   <tr>
     <td><a href="#get-countriesidstatesidjson">GET /countries/id/states/id.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#get-countriesstatesidjson">GET /countries/states/id.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#get-countriesstatescountjson">GET /countries/states/count.json</a></td>
     
   </tr>
   
 </tbody>
</table>
   
## Description

### GET countries/states.json
GET states from a store

#### Request
These fields can be used to filter the query. By default, without any filters, the GET request returns the first 50 states.

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
     <td>limit</td>
     <td>int</td>
     <td>The number of states your query should return (the max is 250 per page)</td>
   </tr>
   <tr>
     <td>page</td>
     <td>int</td>
     <td>The page number of the results. If you have say 300 states, you can use the page=1&limit=200 to get the first 200 states and increment the page counter to get the next 100.</td>
   </tr>
   <tr>
     <td>state</td>
     <td>string</td>
     <td>state name</td>
   </tr>
   <tr>
     <td>state_abbreviation</td>
     <td>string</td>
     <td>state abbreviation</td>
   </tr>
  </tbody>
</table>

#### Response
List of countries
<pre>
[
  {
      "id": 1,
      "state": "Alabama",
      "state_abbreviation": "AL",
      "country_id": 226
  },
  {
      "id": 2,
      "state": "Alaska",
      "state_abbreviation": "AK",
      "country_id": 226
  }
  ...
]
</pre>

### GET countries/id/states/id.json
GET a state by ID from a store

#### Request
This GET request does not take any parameters.

#### Response
country by ID
<pre>
{
    "id": 1,
    "state": "Alabama",
    "state_abbreviation": "AL",
    "country_id": 226
}
</pre> 

### GET countries/states/id.json
GET a specific state

#### Request
This GET request does not take any parameters.

#### Response
country by ID
<pre>
{
    "id": 1,
    "state": "Alabama",
    "state_abbreviation": "AL",
    "country_id": 226
}
</pre>    


### GET countries/states/count.json
Get a total number of states in the store

#### Request
This request does not take any parameters.

#### Response
Returns the number of states in the store 
<pre>
  {
    "count": 50
  }
</pre>

## Resources
<table class="table table-bordered ">
  <thead>
   <tr>
     <th>Resource</th>
   </tr>
 </thead>
 <tbody>
   <tr>
     <td><a href="#get-countriesjson">GET  /countries.json</a></td>

   </tr>
   <tr>
     <td><a href="#get-countriesidjson">GET /countries/id.json</a></td>

   </tr>
   <tr>
     <td><a href="#get-countriescountjson">GET /countries/count.json</a></td>

   </tr>

 </tbody>
</table>

## Description
### GET countries.json
GET countries from a store

#### Request
These fields can be used to filter the query. By default, without any filters, the GET request returns the first 50 countries.

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
     <td>The number of countries your query should return (the max is 250 per page)</td>
   </tr>
   <tr>
     <td>page</td>
     <td>int</td>
     <td>The page number of the results. If you have say 300 countries, you can use the page=1&limit=200 to get the first 200 countries and increment the page counter to get the next 100.</td>
   </tr>
   <tr>
     <td>country</td>
     <td>string</td>
     <td>Country name</td>
   </tr>
   <tr>
     <td>country_iso2</td>
     <td>string</td>
     <td>2 letter countryt code</td>
   </tr>
   <tr>
     <td>country_iso3</td>
     <td>string</td>
     <td>3 letter country code</td>
   </tr>
  </tbody>
</table>

#### Response
List of countries
<pre>
[
  {
      "id": 1,
      "country": "Afghanistan",
      "country_iso2": "AF",
      "country_iso3": "AFG",
      "states": {
          "url": "https://store-bwvr466.mybigcommerce.com/api/v2/countries/1/states.json",
          "resource": "/countries/1/states"
      }
  },
  {
      "id": 2,
      "country": "Albania",
      "country_iso2": "AL",
      "country_iso3": "ALB",
      "states": {
          "url": "https://store-bwvr466.mybigcommerce.com/api/v2/countries/2/states.json",
          "resource": "/countries/2/states"
      }
  },
  ...
]
</pre>


### GET countries/id.json
GET a country from a store

#### Request
This GET request does not take any parameters.

#### Response
country by ID
<pre>
{
    "id": 226,
    "country": "United States",
    "country_iso2": "US",
    "country_iso3": "USA",
    "states": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/countries/226/states.json",
        "resource": "/countries/226/states"
    }
}
</pre>


### GET countries/count.json
Get a total number of countries in the store

#### Request
This request does not take any parameters.

#### Response
Returns the number of countries in the store
<pre>
  {
    "count": 10
  }
</pre>

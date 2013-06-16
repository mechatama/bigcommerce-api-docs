## Resources
<table class="table table-bordered ">
  <thead>
   <tr>
     <th>Resource</th>
   </tr>
 </thead>
 <tbody>
   <tr>
     <td><a href="#get-brandsjson">GET  /brands.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#post-brandsjson">POST /brands.json </a></td>
     
   </tr>
   <tr>
     <td><a href="#get-brandsidjson">GET /brands/id.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#put-brandsidjson">PUT /brands/id.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#get-brandscountjson">GET /brands/count.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#delete-brandsjson">DELETE /brands.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#delete-brandsidjson">DELETE /brands/id.json</a></td>
     
   </tr>
   
 </tbody>
</table>
   
## Description
### GET brands.json
GET brands from a store

#### Request
These fields can be used to filter the query. By default, without any filters, the GET request returns the first 50 brands.

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
     <td>The minimum ID of the brand</td>
   </tr>
   <tr>
     <td>max_id</td>
     <td>int</td>
     <td>The maximum ID of the brand</td>
   </tr>
   <tr>
     <td>limit</td>
     <td>int</td>
     <td>The number of brands your query should return (the max is 250 per page)</td>
   </tr>
   <tr>
     <td>page</td>
     <td>int</td>
     <td>The page number of the results. If you have say 300 brands, you can use the page=1&limit=200 to get the first 200 brands and increment the page counter to get the next 100.</td>
   </tr>
   <tr>
     <td>name</td>
     <td>string(255)</td>
     <td>The name of the brand. Must be unique.</td>
   </tr>
 </tbody>
</table>

#### Response
List of brands
<pre>
  [
      {
      "id": 1,
      "name": "Apple",
      "page_title": "",
      "meta_keywords": "",
      "meta_description": "",
      "image_file": "",
      "search_keywords": ""
    },
    {
    "id": 2,
    "name": "Microsoft",
    "page_title": "",
    "meta_keywords": "",
    "meta_description": "",
    "image_file": "",
    "search_keywords": ""
  }
  ]
</pre>

### POST brands.json
Create brands in a store

#### Request
The POST request allows following fields. Mandatory fields are styled blue.
<style type="text/css">
tr.mandatory {
  color: aliceblue;
}
</style>

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
     <td >name</td>
     <td>string</td>
     
     <td>The name of the brand. Must be unique.</td>
   </tr>
   <tr>
     <td>page_title</td>
     <td>string</td>
     
     <td>The title shown in the browser while viewing the brand</td>
   </tr>
   <tr>
     <td>meta_keywords</td>
     <td>text</td>
     
     <td>Comma separated list of meta keywords to include in the HTML</td>
   </tr>
   <tr>
     <td>meta_description</td>
     <td>text</td>
     
     <td>A meta description to include</td>
   </tr>
   <tr class="mandatory">
     <td >image_file</td>
     <td>string</td>
     
     <td>A valid image</td>
   </tr>
   <tr>
     <td>search_keywords</td>
     <td>string</td>
     
     <td>A comma separated list of keywords that can be used to locate this brand</td>
   </tr>
   
 </tbody>
</table>

#### Response
Creates a brand
<pre>
    {
    "id": 10,
    "name": "Xmen",
    "page_title": "X men brand",
    "meta_keywords": null,
    "meta_description": null,
    "image_file": "t/apirmzk0a__43675.jpg",
    "search_keywords": "xmen, awesomeness"
    }
</pre>   

### GET brands/id.json
GET a brand from a store

#### Request
This GET request does not take any parameters.

#### Response
Brand by ID
<pre>
    {
      "id": 1,
      "name": "Apple",
      "page_title": "",
      "meta_keywords": "",
      "meta_description": "",
      "image_file": "",
      "search_keywords": ""
    }
</pre>    

### PUT brands/id.json
UPDATE a brand from a store

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
   
<tr >
  <td >name</td>
  <td>string</td>

  <td>The name of the brand. Must be unique.</td>
</tr>
<tr>
  <td>page_title</td>
  <td>string</td>
  <td>The title shown in the browser while viewing the brand</td>
</tr>
<tr>
  <td>meta_keywords</td>
  <td>text</td>
  <td>Comma separated list of meta keywords to include in the HTML</td>
</tr>
<tr>
  <td>meta_description</td>
  <td>text</td>
  <td>A meta description to include</td>
</tr>
<tr >
  <td >image_file</td>
  <td>string</td>
  <td>A valid image</td>
</tr>
<tr>
  <td>search_keywords</td>
  <td>string</td>
  <td>A comma separated list of keywords that can be used to locate this brand</td>
</tr>
 
</tbody>
</table>

#### Response
A successful put udpates a brand in the store 
<pre>
  {
    "id": 10,
    "name": "Xmen",
    "page_title": "X men brand",
    "meta_keywords": null,
    "meta_description": null,
    "image_file": "t/apirmzk0a__43675.jpg",
    "search_keywords": "xmen, awesomeness"
  }
</pre>
### GET brands/count.json
Get a total number of brands in the store

#### Request
This request does not take any parameters.

#### Response
Returns the number of brands in the store 
<pre>
  {
    "count": 10
  }
</pre>
Here are resources to delete brands. This is a potentially destrutive operation. Remember that you cannot recover deleted brands.

### DELETE brands.json
DELETE all brands

### DELETE brands/id.json
DELETE a brand

## Resources
<table class="table table-bordered ">
  <thead>
   <tr>
     <th>Resource</th>
   </tr>
 </thead>
 <tbody>
   <tr>
     <td><a href="#get-categoriesjson">GET  /categories.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#post-categoriesjson">POST /categories.json </a></td>
     
   </tr>
   <tr>
     <td><a href="#get-categoriesidjson">GET /categories/id.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#put-categoriesidjson">PUT /categories/id.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#get-categoriescountjson">GET /categories/count.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#delete-categoriesjson">DELETE /categories.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#delete-categoriesidjson">DELETE /categories/id.json</a></td>
     
   </tr>
   
 </tbody>
</table>
   
## Description
### GET categories.json
GET categories from a store

#### Request
These fields can be used to filter the query. By default, without any filters, the GET request returns the first 50 categories.

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
     <td>The minimum ID of the category</td>
   </tr>
   <tr>
     <td>max_id</td>
     <td>int</td>
     <td>The maximum ID of the category</td>
   </tr>
   <tr>
     <td>limit</td>
     <td>int</td>
     <td>The number of categories your query should return (the max is 250 per page)</td>
   </tr>
   <tr>
     <td>page</td>
     <td>int</td>
     <td>The page number of the results. If you have say 300 categories, you can use the page=1&limit=200 to get the first 200 categories and increment the page counter to get the next 100.</td>
   </tr>
   <tr>
     <td>parent_id</td>
     <td>int</td>
     <td>The category id of the parent</td>
   </tr>
   <tr>
     <td>name</td>
     <td>string</td>
     <td>The name of the category</td>
   </tr>
   <tr>
     <td>is_visible</td>
     <td>boolean</td>
     <td>Indicates whether the category is visible</td>
   </tr>
  </tbody>
</table>

#### Response
List of categories
<pre>
  [
    {
        "id": 1,
        "parent_id": 0,
        "name": "Shop Mac",
        "description": "",
        "sort_order": 0,
        "page_title": "",
        "meta_keywords": "",
        "meta_description": "",
        "layout_file": "category.html",
        "parent_category_list": [
            1
        ],
        "image_file": "",
        "is_visible": true,
        "search_keywords": "",
        "url": "/shop-mac/"
    }
  ]
</pre>

### POST categories.json
Create categories in a store

#### Request
The POST request allows following fields. Mandatory fields are styled blue.
<!-- do not change this. for rendering on the main site -->
<style type="text/css">
tr.mandatory {
  color: aliceblue;
}
</style>
<!-- style complete -->

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
     <td>parent_id</td>
     <td>int</td>
     
     <td>The ID of the parent category this belongs to</td>
   </tr>
   <tr class="mandatory">
     <td >name</td>
     <td>string</td>
     
     <td>The name of the category. Must be unique.</td>
   </tr>
   <tr>
     <td>sort_order</td>
     <td>integer</td>
     
     <td>The sort order of the category</td>
   </tr>
   <tr>
     <td>description</td>
     <td>string</td>
     
     <td>A category description</td>
   </tr>
   <tr>
     <td>page_title</td>
     <td>string</td>
     
     <td>The page title for the category page</td>
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
   <tr>
     <td >image_file</td>
     <td>string</td>
     
     <td>A valid image</td>
   </tr>
   <tr>
     <td >layout_file</td>
     <td>string</td>
     
     <td>A valid layout file. Refer to <a href="https://support.Bigcommerce.com/questions/1156/What+are+the+standard+template+layouts%3F" target="_blank">this article</a> on creating category files.</td>
   </tr>
   <tr>
     <td>search_keywords</td>
     <td>string</td>
     
     <td>A comma separated list of keywords that can be used to locate this brand</td>
   </tr>
   <tr>
     <td>is_visible</td>
     <td>boolean</td>
     
     <td>Is the category visible?</td>
   </tr>
   
  </tbody>
</table>

#### Response
Creates a category
<pre>
{
    "id": 10,
    "parent_id": 1,
    "name": "Xmen toys",
    "description": "",
    "sort_order": 2,
    "page_title": "",
    "meta_keywords": null,
    "meta_description": null,
    "layout_file": "category.html",
    "parent_category_list": [
        1,
        10
    ],
    "image_file": "d/apiy2uz6q__69888.jpg",
    "is_visible": true,
    "search_keywords": "",
    "url": "/xmen-toys/"
}
</pre>   

### GET categories/id.json
GET a category from a store

#### Request
This GET request does not take any parameters.

#### Response
category by ID
<pre>
{
    "id": 10,
    "parent_id": 1,
    "name": "Xmen toys",
    "description": "",
    "sort_order": 2,
    "page_title": "",
    "meta_keywords": null,
    "meta_description": null,
    "layout_file": "category.html",
    "parent_category_list": [
        1,
        10
    ],
    "image_file": "d/apiy2uz6q__69888.jpg",
    "is_visible": true,
    "search_keywords": "",
    "url": "/xmen-toys/"
}
</pre>    

### <a id="categories_r4"></a>PUT categories/id.json
UPDATE a category from a store

#### Request
This PUT request takes following parameters.
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
     <td>parent_id</td>
     <td>int</td>
     
     <td>The ID of the parent category this belongs to</td>
   </tr>
   <tr class="mandatory">
     <td >name</td>
     <td>string</td>
     
     <td>The name of the category. Must be unique.</td>
   </tr>
   <tr>
     <td>sort_order</td>
     <td>integer</td>
     
     <td>The sort order of the category</td>
   </tr>
   <tr>
     <td>description</td>
     <td>string</td>
     
     <td>A description for the category</td>
   </tr>
   <tr>
     <td>page_title</td>
     <td>string</td>
     
     <td>The page title for the category page</td>
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
   <tr class="mandatory">
     <td >layout_file</td>
     <td>string</td>
     
     <td>A valid layout file. Refer to <a href="https://support.Bigcommerce.com/questions/1156/What+are+the+standard+template+layouts%3F" target="_blank">this article</a> on creating category files.</td>
   </tr>
   <tr>
     <td>search_keywords</td>
     <td>string</td>
     
     <td>A comma separated list of keywords that can be used to locate this brand</td>
   </tr>
   <tr>
     <td>is_visible</td>
     <td>boolean</td>
     
     <td>Is the category visible?</td>
   </tr>
   
  </tbody>
</table>

#### Response
A successful put udpates a category in the store 
<pre>
{
    "id": 10,
    "parent_id": 1,
    "name": "Xmen toys",
    "description": "",
    "sort_order": 2,
    "page_title": "",
    "meta_keywords": null,
    "meta_description": null,
    "layout_file": "category.html",
    "parent_category_list": [
        1,
        10
    ],
    "image_file": "d/apiy2uz6q__69888.jpg",
    "is_visible": true,
    "search_keywords": "",
    "url": "/xmen-toys/"
}
</pre>
### GET categories/count.json
Get a total number of categories in the store

#### Request
This request does not take any parameters.

#### Response
Returns the number of categories in the store 
<pre>
  {
    "count": 10
  }
</pre>
Here are resources to delete categories. This is a potentially destrutive operation. Remember that you cannot recover deleted categories.

### DELETE categories.json
DELETE all categories

### DELETE categories/id.json
DELETE a category

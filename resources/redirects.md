
## About

Redirects repesent 301 redirect mappings that are used to map a custom URL path to another resource (such as a product, category, brand, etc.) or a manually defined static URL.

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
     <td><a href="#get-redirects">Get Redirects</a></td>
   </tr>
   <tr>
     <td><a href="#create-redirect">Create Redirect</a></td>
   </tr>
   <tr>
     <td><a href="#get-redirect">Get Redirect</a></td>
   </tr>
   <tr>
     <td><a href="#update-redirect">Update Redirect</a></td>
   </tr>
   <tr>
     <td><a href="#get-redirects-count">Get Redirects Count</a></td>
   </tr>
   <tr>
     <td><a href="#delete-redirects">Delete Redirects</a></td>
   </tr>
   <tr>
     <td><a href="#delete-redirect">Delete Redirect</a></td>
   </tr>
 </tbody>
</table>

## Reference

## Filters

These fields can be used to filter the query. By default, without any filters, the GET request returns the first 50 redirects.

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
     <td>The number of redirects your query should return (the max is 250 per page)</td>
   </tr>
   <tr>
     <td>page</td>
     <td>int</td>
     <td>The page number of the results. If you have say 300 redirects, you can use the page=1&limit=200 to get the first 200 redirects and increment the page counter to get the next 100.</td>
   </tr>
  </tbody>
</table>

## Schema

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
      <td>id (read only)</td>
      <td>int</td>
      <td>ID of the redirect</td>
    </tr>
    <tr>
      <td>path</td>
      <td>string</td>
      <td>The path that will be redirected from</td>
    </tr>
    <tr>
      <td>forward</td>
      <td>object</td>
      <td>The destination of the redirect</td>
    </tr>
    <tr>
      <td>forward.type</td>
      <td>enum</td>
      <td>The type of the redirect destination. The following values will redirect to the associated page determined by the reference provided in `forward.ref`:

* 'product'
* 'category'
* 'brand'
* 'page'
* 'news'

Alternatively, a static mapping can be created, redirecting to another URL defined in `forward.ref` by using a forward type value of:

* 'manual'
      </td>
    </tr>
    <tr>
      <td>forward.ref</td>
      <td>string | int</td>
      <td>The reference of the redirect destination. For redirects that forward to another resource, this value should contain the ID of the associated resource. If `forward.type` is `manual` then this value should be a string representing a URL to forward to, starting with either `https://`, `http://` or `/`</td>
    </tr>
    <tr>
      <td>url (read only)</td>
      <td>string</td>
      <td>The generated URL that this redirect would forward to</td>
    </tr>
  </tbody>
</table>

## Resources

### Get Redirects

<pre>
GET /api/v2/redirects
</pre>

Gets the collection of redirects.

#### Response

By default, without any filters, the request returns the entire collection.

<pre>
[{
  "id": 1,
  "path": "/redirect_path1",
  "forward": {
    "type": "manual",
    "ref": "http://www.bigcommerce.com"
  },
  "url": "http://www.bigcommerce.com"
},
{
  "id": 2,
  "path": "/redirect_path2",
  "forward": {
    "type": "product",
    "ref": 35
  },
  "url": "http://store.example.com/product-no-35"
}]
</pre>

### Create Redirect

<pre>
POST /api/v2/redirects
</pre>

Creates a new redirect.

### Request

<pre>
{
  "path": "/mens_clothing",
  "forward": {
    "type": "category",
    "ref": 3
  }
}
</pre>

### Response

<pre>
{
  "id": 3,
  "path": "/mens_clothing",
  "forward": {
    "type": "category",
    "ref": 3
  },
  "url": "http://store.example.com/mens"
}
</pre>

### Get Redirect

<pre>
GET /api/v2/redirects/{id}
</pre>

Returns a single redirect.

#### Response

<pre>
{
  "id": 1,
  "path": "/redirect_path1",
  "forward": {
    "type": "manual",
    "ref": "http://www.bigcommerce.com"
  },
  "url": "http://www.bigcommerce.com"
}
</pre>

### Update Redirect

<pre>
PUT /api/v2/redirects/{id}
</pre>

Updates the given redirect.

#### Request

The `path`, `forward.type` and `forward.ref` fields of an existing redirect can be updated.

<pre>
{
  "path": "/new_path",
  "forward": {
    "type": "news",
    "ref": 3
  }
}
</pre>

### Get Redirects Count

<pre>
GET /api/v2/redirects/count
</pre>

Get a total number of redirects in the store.

#### Response

<pre>
  {
    "count": 10
  }
</pre>

### Delete Redirects

<pre>
DELETE /api/v2/redirects
</pre>

Deletes all redirects.

### Delete Redirect

<pre>
DELETE /api/v2/redirects/{id}
</pre>

Deletes a single redirect.


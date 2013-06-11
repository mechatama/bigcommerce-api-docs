## Resources
<table class="table table-bordered ">
  <thead>
   <tr>
     <th>Resource</th>
   </tr>
 </thead>
 <tbody>
   <tr>
     <td><a href="#get-storejson">GET  /store.json</a></td>
     
   </tr>
  
 </tbody>
</table>
   
## Description
### GET store.json
Store information resource.

Provides basic metadata about a store’s identity, and default settings.

#### Request
There are no filters accepted on this request


#### Response
Store resource
<pre>
{
	"id": "store-1234",
	"domain": "mystore.com",
	"name": "My Store",
	"address": "13170 Round Bluff Crossing, St. Benedict, Texas, 77174-3311",
	"phone": "(254) 923-8162",
	"admin_email": "admin@mystore.com",
	"order_email": "orders@mystore.com",
	"language": "en",
	"currency": "USD",
	"currency_symbol": "$",
	"decimal_separator": ".",
	"thousands_separator": ",",
	"decimal_places": 2,
	"currency_symbol_location": "left",
	"weight_units": "LBS",
	"dimension_units": "Inches"
}
</pre>

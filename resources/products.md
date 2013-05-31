## Resources
<table class="table table-bordered ">
  <thead>
   <tr>
     <th>Resource</th>
   </tr>
 </thead>
 <tbody>
   <tr>
     <td><a href="#get-productsjson">GET  /products.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#post-productsjson">POST /products.json </a></td>
     
   </tr>
   <tr>
     <td><a href="#get-productsidjson">GET /products/id.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#put-productsidjson">PUT /products/id.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#get-productscountjson">GET /products/count.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#delete-productsjson">DELETE /products.json</a></td>
     
   </tr>
   <tr>
     <td><a href="#delete-productsidjson">DELETE /products/id.json</a></td>
     
   </tr>
   
 </tbody>
</table>
   
## Description
### GET products.json
GET products from a store

#### Request
These fields can be used to filter the query. By default, without any filters, the GET request returns all the products.

<table class="table table-bordered table-striped">
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
     
     <td>The minimum ID of the product</td>
   </tr>
   <tr>
     <td>max_id</td>
     <td>int</td>
     
     <td>The maximum ID of the product</td>
   </tr>
   <tr>
     <td>limit</td>
     <td>integer</td>
     
     <td>The number of products your query should return (the max is 200 per page)</td>
   </tr>
   <tr>
     <td>page</td>
     <td>integer</td>
     
     <td>The page number of the results. If you have say 300 products, you can use the page=1&limit=200 to get the first 200 products and increment the page counter to get the next 100.</td>
   </tr>
   <tr>
     <td>name</td>
     <td>string</td>
     
     <td>The product name</td>
   </tr>
   <tr>
     <td>sku</td>
     <td>string</td>
     
     <td>The product sku</td>
   </tr>
   <tr>
     <td>description</td>
     <td>string</td>
     
     <td>The product description</td>
   </tr>
   <tr>
     <td>condition</td>
     <td>enum</td>
     
     <td>The product condition - [New, Used, Refurbished]</td>
   </tr>
   <tr>
     <td>availability</td>
     <td>enum</td>
     
     <td>The availability of the product - [available, disabled, preorder]</td>
   </tr>
   <tr>
     <td>brand_id</td>
     <td>int</td>
     
     <td>The product's brand</td>
   </tr>
   <tr>
     <td>min_date_created</td>
     <td>date</td>
     
     <td>The minimum date when the product was created</td>
   </tr>
   <tr>
     <td>max_date_created</td>
     <td>date</td>
     
     <td>The maximum date when the product was created</td>
   </tr>
   <tr>
     <td>min_date_modified</td>
     <td>date</td>
     
     <td>The minimum date when the product was modified</td>
   </tr>
   <tr>
     <td>max_date_modified</td>
     <td>date</td>
     
     <td>The maximum date when the product was last modified</td>
   </tr>
   <tr>
     <td>min_date_last_imported</td>
     <td>date</td>
     
     <td>The minimum date when the product was imported</td>
   </tr>
   <tr>
     <td>max_date_last_imported</td>
     <td>date</td>
     
     <td>The maximum date when the product was imported</td>
   </tr>
   <tr>
     <td>is_visible</td>
     <td>boolean</td>
     
     <td>Product visibility status</td>
   </tr>
   <tr>
     <td>is_featured</td>
     <td>booelan</td>
     
     <td>Product featured status</td>
   </tr>
   <tr>
     <td>min_inventory_level</td>
     <td>int</td>
     
     <td>The minimum inventory level when inventory tracking is enabled</td>
   </tr>
   <tr>
     <td>max_inventory_level</td>
     <td>int</td>
     
     <td>The maximum inventory level when inventory tracking in enabled</td>
   </tr>
   <tr>
     <td>include_sku</td>
     <td>boolean</td>
     
     <td>Include products which inventory is tracked by SKU, to be used in conjunction with the "max_inventory_level" and "min_inventory_level" filter.
   </tr>
   <tr>
     <td>min_price</td>
     <td>float</td>
     
     <td>The minimum product price</td>
   </tr>
   <tr>
     <td>max_price</td>
     <td>float</td>
     
     <td>The maximum product price</td>
   </tr>
   <tr>
     <td>min_number_sold</td>
     <td>int</td>
     
     <td>The minimum number of products sold</td>
   </tr>
   <tr>
     <td>max_number_sold</td>
     <td>int</td>
     
     <td>The maximum number of products sold</td>
   </tr>
  </tbody>
</table>

#### Response
List of products
<pre>
[
  {
      "id": 29,
      "keyword_filter": null,
      "name": "startrek",
      "type": "physical",
      "sku": "",
      "description": null,
      "search_keywords": null,
      "availability_description": "",
      "price": "19.9900",
      "cost_price": "0.0000",
      "retail_price": "0.0000",
      "sale_price": "0.0000",
      "sort_order": 0,
      "is_visible": false,
      "is_featured": false,
      "related_products": "",
      "inventory_level": 0,
      "inventory_warning_level": 0,
      "warranty": null,
      "weight": "0.0000",
      "width": "0.0000",
      "height": "0.0000",
      "depth": "0.0000",
      "fixed_cost_shipping_price": "0.0000",
      "is_free_shipping": false,
      "inventory_tracking": "none",
      "rating_total": 0,
      "rating_count": 0,
      "total_sold": 0,
      "date_created": "Wed, 12 Dec 2012 20:29:45 +0000",
      "brand_id": 0,
      "view_count": 0,
      "page_title": "",
      "meta_keywords": null,
      "meta_description": null,
      "layout_file": "",
      "is_price_hidden": false,
      "price_hidden_label": "",
      "categories": [
          2
      ],
      "date_modified": "Wed, 12 Dec 2012 20:29:45 +0000",
      "event_date_field_name": "",
      "event_date_type": "none",
      "event_date_start": "",
      "event_date_end": "",
      "myob_asset_account": "",
      "myob_income_account": "",
      "myob_expense_account": "",
      "peachtree_gl_account": "",
      "condition": "New",
      "is_condition_shown": false,
      "preorder_release_date": "",
      "is_preorder_only": false,
      "preorder_message": "",
      "order_quantity_minimum": 0,
      "order_quantity_maximum": 0,
      "open_graph_type": "product",
      "open_graph_title": "",
      "open_graph_description": "",
      "is_open_graph_thumbnail": true,
      "upc": "",
      "date_last_imported": "",
      "option_set_id": null,
      "tax_class_id": 0,
      "option_set_display": "right",
      "bin_picking_number": "",
      "custom_url": "/startrek/",
      "availability": "available",
      "brand": {
          "url": "https://store-bwvr466.mybigcommerce.com/api/v2/brands/0.json",
          "resource": "/brands/0"
      },
      "images": {
          "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/images.json",
          "resource": "/products/29/images"
      },
      "discount_rules": {
          "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/discountrules.json",
          "resource": "/products/29/discountrules"
      },
      "configurable_fields": {
          "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/configurablefields.json",
          "resource": "/products/29/configurablefields"
      },
      "custom_fields": {
          "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/customfields.json",
          "resource": "/products/29/customfields"
      },
      "videos": {
          "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/videos.json",
          "resource": "/products/29/videos"
      },
      "skus": {
          "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/skus.json",
          "resource": "/products/29/skus"
      },
      "rules": {
          "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/rules.json",
          "resource": "/products/29/rules"
      },
      "option_set": null,
      "options": {
          "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/options.json",
          "resource": "/products/29/options"
      },
      "tax_class": {
          "url": "https://store-bwvr466.mybigcommerce.com/api/v2/taxclasses/0.json",
          "resource": "/taxclasses/0"
      }
  },
  ...
]   
</pre>

### POST products.json
Create products in a store

#### Request
The POST request allows following fields. Mandatory fields are styled blue. Please note that when creating products via API, the is_visible field defaults to false. You need to explicitly set this field to true or else the product won't be visible in the store.
<style type="text/css">
tr.mandatory {
  color: aliceblue;
}
</style>

<table class="table table-bordered" ><thead>
      <tr >
  <th  data-column="0"><div><p>Field </p></div></th>
  <th  data-column="1"><div><p>Type </p></div></th>
  <th  data-column="2"><div><p>Description </p></div></th>
  </tr></thead><tbody>

  <tr class="mandatory">
  <td> name </td>
  <td> string </td>
  <td> The product name. </td>
  </tr>
  <tr class="mandatory">
  <td> type </td>
  <td> enum </td>
  <td> The product type: </p>
  <ul>
    <li><strong>physical</strong> - a physical stock unit</li>
    <li><strong>digital</strong> - a digital download</li>
  </ul>
  </td>
  </tr>
  <tr>
  <td> sku </td>
  <td> string </td>
  <td> User defined product code/stock keeping unit (SKU). </td>
  </tr>
  <tr>
  <td> description  </td>
  <td> text </td>
  <td> The product description which can include HTML&nbsp;formatting. </td>
  </tr>
  <tr>
  <td> search_keywords </td>
  <td> text </td>
  <td> A comma separated list of keywords that can be used to locate the product when searching the store. </td>
  </tr>
  <tr>
  <td> availability_description </td>
  <td> string </td>
  <td> Availability text displayed on the checkout page under the product title telling the customer how long it will normally take to ship this product, such as "Usually ships in 24 hours". </td>
  </tr>
  <tr class="mandatory">
  <td> price </td>
  <td> decimal </td>
  <td> The price of the product, the price should include or exclude tax based on the store settings. </td>
  </tr>
  <tr>
  <td> cost_price </td>
  <td> decimal  </td>
  <td> The cost price of the product, stored for reference only, it is not used or displayed anywhere on the store. </td>
  </tr>
  <tr>
  <td> retail_price </td>
  <td> decimal  </td>
  <td> The retail cost of the product, if entered the retail cost price will be shown on the product page. </td>
  </tr>
  <tr>
  <td> sale_price </td>
  <td> decimal  </td>
  <td> The sale price will be used instead of value in the price field when calculating the products cost if entered. </td>
  </tr>
  <tr>
  <td> sort_order </td>
  <td> int </td>
  <td> Priority this product will be given when included in product lists on category pages and search results. The lower the number, the closer to the top of the results the product will be. </td>
  </tr>
  <tr>
  <td> is_visible </td>
  <td> boolean </td>
  <td> Flag to determine if the product should be displayed to customers browsing the store or not. If true the product will be displayed, false the product will be hidden from view. </td>
  </tr>
  <tr>
  <td> is_featured </td>
  <td> boolean </td>
  <td> Flag to determine if the product should be included in "featured products" panel when viewing the store. </td>
  </tr>
  <tr>
  <td> related_products </td>
  <td> string </td>
  <td> A list of related products which will be shown on the products page. &nbsp;If not specified related products will be generated automatically by the store. </td>
  </tr>
  <tr>
  <td> inventory_level </td>
  <td> int </td>
  <td> Current inventory level of the product. Simple inventory tracking must be enabled (See the inventory_tracking&nbsp;field) for this to take any effect. </td>
  </tr>
  <tr>
  <td> inventory_warning_level </td>
  <td> int </td>
  <td> Inventory Warning level for the product. When the products inventory level drops below the warning level the store owner will be informed.&nbsp;Simple inventory tracking must be enabled (See the inventory_tracking field) for this to take any effect. </td>
  </tr>
  <tr>
  <td> warranty </td>
  <td> string </td>
  <td> Warranty information displayed on the product page&nbsp;which can include HTML&nbsp;formatting. </td>
  </tr>
  <tr class="mandatory">
  <td> weight </td>
  <td> decimal  </td>
  <td> Weight of the product used which can be used when calculating shipping costs. </td>
  </tr>
  <tr>
  <td> width </td>
  <td> decimal  </td>
  <td> Width of the product used which can be used when calculating shipping costs.  </td>
  </tr>
  <tr>
  <td> height </td>
  <td> decimal  </td>
  <td> Height of the product used which can be used when calculating shipping costs. </td>
  </tr>
  <tr>
  <td> depth </td>
  <td> decimal  </td>
  <td> Depth of the product used which can be used when calculating shipping costs. </td>
  </tr>
  <tr>
  <td> fixed_cost_shipping_price  </td>
  <td> decimal  </td>
  <td> A fixed shipping cost for the product, if defined the value will be used during checkout instead of normal shipping cost calculation. </td>
  </tr>
  <tr>
  <td> is_free_shipping  </td>
  <td> boolean </td>
  <td> Flag used to indicate if the product has free shipping or not. If true the shipping cost for the product will be zero. </td>
  </tr>
  <tr>
  <td> inventory_tracking </td>
  <td> enum </td>
  <td> The type of inventory tracking for the product: </p>
  <ul>
    <li><strong>none</strong> - inventory levels will not be tracked.</li>
    <li><strong>simple</strong> - inventory levels will be tracked using the "inventory_level" and "inventory_warning_level" fields.</li>
    <li><strong>sku</strong> - inventory levels will be tracked based on individual product options which maintain their own warning levels and inventory levels.</li>
  </ul>
  </td>
  </tr>
  <tr>
  <td> rating_total </td>
  <td> int </td>
  <td> The total rating for the product. </td>
  </tr>
  <tr>
  <td> rating_count </td>
  <td> int </td>
  <td> The total number of ratings the product has had. </td>
  </tr>
  <tr>
  <td> number_sold </td>
  <td> int </td>
  <td> The total number of times this product has been sold. </td>
  </tr>
  <tr>
  <td> date_created </td>
  <td> date </td>
  <td> The date of which the product was created. </td>
  </tr>
  <tr>
  <td> product_id </td>
  <td> int </td>
  <td> The ID of the product the product belongs to.&nbsp;See the&nbsp;<a href="/api/products">products</a>&nbsp;resource for information. </td>
  </tr>
  <tr>
  <td> view_count </td>
  <td> int </td>
  <td> The number of times the product has been viewed. </td>
  </tr>
  <tr>
  <td> page_title </td>
  <td> string </td>
  <td> Custom title for the products page, if not defined the product name will be used as the page title. </td>
  </tr>
  <tr>
  <td> meta_keywords </td>
  <td> text </td>
  <td> Custom meta keywords for the product page, if not defined the store default keywords will be used. </td>
  </tr>
  <tr>
  <td> meta_description </td>
  <td> text </td>
  <td> Custom meta description for the product page, if not defined the store default meta description will be used. </td>
  </tr>
  <tr>
  <td> layout_file </td>
  <td> string </td>
  <td> <span style="color: rgb(0,0,0);">The layout template file used to render this category.</span> </td>
  </tr>
  <tr>
  <td> is_price_hidden </td>
  <td> boolean </td>
  <td> Flag used to determine if the price for this product should be hidden on the product page. </td>
  </tr>
  <tr>
  <td> price_hidden_label </td>
  <td> string </td>
  <td> If the product price is hidden (see the "is_price_hidden" field), then a label will be displayed instead with the value of this field if it is defined. </td>
  </tr>
  <tr class="mandatory">
  <td> categories </td>
  <td> array </td>
  <td> An array of IDs for the categories this product belongs to. 
  When updating a product, if an array of categories is supplied all product categories will be over written. </td>
  </tr>
  <tr>
  <td> date_modified </td>
  <td> date </td>
  <td> The date that the product was last modified. </td>
  </tr>
  <tr>
  <td> event_date_field_name </td>
  <td> string </td>
  <td> Name of the field to be displayed on the product page when selecting the "delivery/event" date. </td>
  </tr>
  <tr>
  <td> event_date_type </td>
  <td> enum </td>
  <td><ul>
    <li><strong>none</strong>&nbsp;- If set to none then the event/delivery date&nbsp;requirement&nbsp;and field will be disabled.</li>
    <li><strong>after</strong> - The selected date must fall either on or after the date specified in the "event_date_start" field.</li>
    <li><strong>before</strong> - The selected date must fall either before or on the date specified in the "event_date_end" field.</li>
    <li><strong>range</strong> - The selected date must fall between the "event_date_start" and "event_date_end" dates.</li>
  </ul>
  </td>
  </tr>
  <tr>
  <td> event_date_start </td>
  <td> date </td>
  <td> The date which is used as the "after" date when the product requires the customer to select a delivery/event date. </td>
  </tr>
  <tr>
  <td> event_date_end </td>
  <td> date </td>
  <td> The date which is used as the "before" date when the product requires the&nbsp;customer&nbsp;to select a delivery/event date. </td>
  </tr>
  <tr>
  <td> myob_asset_account </td>
  <td> string(20) </td>
  <td> MYOB Asset Account. </td>
  </tr>
  <tr>
  <td> myob_income_account </td>
  <td> string(20) </td>
  <td> MYOB Income Account. </td>
  </tr>
  <tr>
  <td> myob_expense_account </td>
  <td> string(20) </td>
  <td> MYOB Expense/COS Account. </td>
  </tr>
  <tr>
  <td> peachtree_gl_account </td>
  <td> string(20) </td>
  <td> Peachtree General Ledger Account. </td>
  </tr>
  <tr>
  <td> condition </td>
  <td> enum </td>
  <td> The product condition, will be shown on the product page if the value of the "is_condition_shown" field is true. Possible values: </p>
  <ul>
    <li>New</li>
    <li>Used</li>
    <li>Refurbished</li>
  </ul>
  </td>
  </tr>
  <tr>
  <td> is_condition_shown  </td>
  <td> boolean </td>
  <td> Flag used to determine if the product condition is shown to the customer on the product page. </td>
  </tr>
  <tr>
  <td> preorder_release_date </td>
  <td> date </td>
  <td> Pre-order&nbsp;release date. See availability field for details on setting a products availability to accept pre-orders. </td>
  </tr>
  <tr>
  <td> is_preorder_only </td>
  <td> boolean </td>
  <td> If set to false, the product will not change its availability from preorder to available on the release date. 
  Otherwise on the release date the products availability/status will change to available. </td>
  </tr>
  <tr>
  <td> preorder_message </td>
  <td>string</td>
  <td> Custom expected date message to display on the product page, if undefined the message defaults to the store wide setting. Can contain the&nbsp;%%DATE%%&nbsp;place holder&nbsp;which will be substituted for the release date </td>
  </tr>
  <tr>
  <td> order_quantity_minimum </td>
  <td> int </td>
  <td> The minimum quantity an order has to contain to be able to purchase this product. </td>
  </tr>
  <tr>
  <td> order_quantity_maximum </td>
  <td> int </td>
  <td> The maximum quantity an order can contain when purchasing the product. </td>
  </tr>
  <tr>
  <td> open_graph_type </td>
  <td> enum </td>
  <td> Type of product, valid values are: </p>
  <ul>
    <li>product</li>
    <li>album</li>
    <li>book</li>
    <li>drink</li>
    <li>food</li>
    <li>game</li>
    <li>movie</li>
    <li>song</li>
    <li>tv_show</li>
  </ul>
  </td>
  </tr>
  <tr>
  <td> open_graph_title </td>
  <td> string </td>
  <td> Title of the product, if not specified the product name will be used instead. </td>
  </tr>
  <tr>
  <td> open_graph_description </td>
  <td> text </td>
  <td> Description to use for the product, if not specified then the meta_description will be used instead. </td>
  </tr>
  <tr>
  <td> is_open_graph_thumbnail </td>
  <td> boolean </td>
  <td> If set to true, the product thumbnail image will be used as the open graph image. </td>
  </tr>
  <tr>
  <td> upc </td>
  <td> string(32) </td>
  <td> The product UPC code which is used in feeds for shopping comparison sites.  </td>
  </tr>
  <tr>
  <td> date_last_imported </td>
  <td> date </td>
  <td> The date of which the product was last imported using the bulk importer. </td>
  </tr>
  <tr>
  <td> option_set_id </td>
  <td> int </td>
  <td> The ID of the option set applied to the product. 
  <strong>Note:</strong> To remove the option set off the product, set the value to "null" on update. </td>
  </tr>
  <tr>
  <td> tax_class_id </td>
  <td> int </td>
  <td> The ID of the tax class applied to the product. </td>
  </tr>
  <tr>
  <td> option_set_display </td>
  <td> enum('right', 'below') </td>
  <td> The position the option set options will be displayed on the product page. </td>
  </tr>
  <tr>
  <td> bin_picking_number  </td>
  <td> string </td>
  <td> The BIN picking number for the product. </td>
  </tr>
  <tr class="mandatory">
  <td> availability </td>
  <td> enum('available', 'disabled', 'preorder') </td>
  <td> Availability of the product. availability options: </p>
  <ul>
    <li><strong>available</strong>&nbsp;- The product can be purchased in the store front.</li>
    <li><strong>disabled</strong>&nbsp;- The product is listed in the store front but can not be purchased.</li>
    <li><strong>preorder</strong>&nbsp;- The product is listed for pre-orders.</li>
  </ul>
  </td>
  </tr>
  <tr>
  <td> images </td>
  <td> resource  </td>
  <td> See the&nbsp;<a href="/api/products/images">Images</a>&nbsp;resource for information. </td>
  </tr>
  <tr>
  <td> discount_rules </td>
  <td> resource  </td>
  <td> See the&nbsp;<a href="/api/products/discountrules">Bulk Discount Rules</a>&nbsp;resource for information. </td>
  </tr>
  <tr>
  <td> configurable_fields </td>
  <td> resource  </td>
  <td> See the&nbsp;<a href="/api/products/configurablefields">Configurable Fields</a>&nbsp;resource for information. </td>
  </tr>
  <tr>
  <td> custom_fields </td>
  <td> resource  </td>
  <td> See the&nbsp;<a href="/api/products/customfields">Custom Fields</a>&nbsp;resource for information. </td>
  </tr>
  <tr>
  <td> videos </td>
  <td> resource  </td>
  <td> See the&nbsp;<a href="/api/products/videos">Videos</a>&nbsp;resource for information. </td>
  </tr>
  <tr>
  <td> option_set </td>
  <td> resource  </td>
  <td> See the&nbsp;<a href="/api/optionsets">Option Set</a>&nbsp;resource&nbsp;for information. </td>
  </tr>
  <tr>
  <td> rules </td>
  <td> resource  </td>
  <td> Rules which apply to this product only which are based on the products Option Set. 
  See <a href="/api/products/rules">Rules</a> resource for information. </td>
  </tr>
  <tr>
  <td> skus </td>
  <td> resource  </td>
  <td> Stock Keeping Units for the product. 
  See the <a href="/api/products/skus">SKU</a>&nbsp;resource for the definition of a sku object. </td>
  </tr>
  <tr>
  <td> options </td>
  <td> resource </td>
  <td> Options from the option set applied to the product. 
  See the&nbsp;<a href="/api/options">Product Options</a>&nbsp;resource for information. </td>
  </tr>
  </tbody></table>

#### Response
Creates a product
<pre>
 {
  "id": 30,
  "keyword_filter": null,
  "name": "Xmen Toy",
  "type": "physical",
  "sku": "",
  "description": null,
  "search_keywords": null,
  "availability_description": "",
  "price": "10.9900",
  "cost_price": "0.0000",
  "retail_price": "0.0000",
  "sale_price": "0.0000",
  "sort_order": 0,
  "is_visible": false,
  "is_featured": false,
  "related_products": "",
  "inventory_level": 0,
  "inventory_warning_level": 0,
  "warranty": null,
  "weight": "1.0000",
  "width": "0.0000",
  "height": "0.0000",
  "depth": "0.0000",
  "fixed_cost_shipping_price": "0.0000",
  "is_free_shipping": false,
  "inventory_tracking": "none",
  "rating_total": 0,
  "rating_count": 0,
  "total_sold": 0,
  "date_created": "Fri, 21 Dec 2012 00:02:30 +0000",
  "brand_id": 0,
  "view_count": 0,
  "page_title": "",
  "meta_keywords": null,
  "meta_description": null,
  "layout_file": "",
  "is_price_hidden": false,
  "price_hidden_label": "",
  "categories": [
      2
  ],
  "date_modified": "Fri, 21 Dec 2012 00:02:30 +0000",
  "event_date_field_name": "",
  "event_date_type": "none",
  "event_date_start": "",
  "event_date_end": "",
  "myob_asset_account": "",
  "myob_income_account": "",
  "myob_expense_account": "",
  "peachtree_gl_account": "",
  "condition": "New",
  "is_condition_shown": false,
  "preorder_release_date": "",
  "is_preorder_only": false,
  "preorder_message": "",
  "order_quantity_minimum": 0,
  "order_quantity_maximum": 0,
  "open_graph_type": "product",
  "open_graph_title": "",
  "open_graph_description": "",
  "is_open_graph_thumbnail": true,
  "upc": "",
  "date_last_imported": "",
  "option_set_id": null,
  "tax_class_id": 0,
  "option_set_display": "right",
  "bin_picking_number": "",
  "custom_url": "/xmen-toy/",
  "availability": "available",
  "brand": {
      "url": "https://store-bwvr466.mybigcommerce.com/api/v2/brands/0.json",
      "resource": "/brands/0"
  },
  "images": {
      "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/30/images.json",
      "resource": "/products/30/images"
  },
  "discount_rules": {
      "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/30/discountrules.json",
      "resource": "/products/30/discountrules"
  },
  "configurable_fields": {
      "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/30/configurablefields.json",
      "resource": "/products/30/configurablefields"
  },
  "custom_fields": {
      "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/30/customfields.json",
      "resource": "/products/30/customfields"
  },
  "videos": {
      "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/30/videos.json",
      "resource": "/products/30/videos"
  },
  "skus": {
      "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/30/skus.json",
      "resource": "/products/30/skus"
  },
  "rules": {
      "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/30/rules.json",
      "resource": "/products/30/rules"
  },
  "option_set": null,
  "options": {
      "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/30/options.json",
      "resource": "/products/30/options"
  },
  "tax_class": {
      "url": "https://store-bwvr466.mybigcommerce.com/api/v2/taxclasses/0.json",
      "resource": "/taxclasses/0"
  }
}
</pre>   

### GET products/{id}.json
GET a product from a store

#### Request
This GET request does not take any parameters.

#### Response
product by ID
<pre>
{
    "id": 29,
    "keyword_filter": null,
    "name": "startrek",
    "type": "physical",
    "sku": "",
    "description": null,
    "search_keywords": null,
    "availability_description": "",
    "price": "19.9900",
    "cost_price": "0.0000",
    "retail_price": "0.0000",
    "sale_price": "0.0000",
    "sort_order": 0,
    "is_visible": false,
    "is_featured": false,
    "related_products": "",
    "inventory_level": 0,
    "inventory_warning_level": 0,
    "warranty": null,
    "weight": "0.0000",
    "width": "0.0000",
    "height": "0.0000",
    "depth": "0.0000",
    "fixed_cost_shipping_price": "0.0000",
    "is_free_shipping": false,
    "inventory_tracking": "none",
    "rating_total": 0,
    "rating_count": 0,
    "total_sold": 0,
    "date_created": "Wed, 12 Dec 2012 20:29:45 +0000",
    "brand_id": 0,
    "view_count": 0,
    "page_title": "",
    "meta_keywords": null,
    "meta_description": null,
    "layout_file": "",
    "is_price_hidden": false,
    "price_hidden_label": "",
    "categories": [
        2
    ],
    "date_modified": "Wed, 12 Dec 2012 20:29:45 +0000",
    "event_date_field_name": "",
    "event_date_type": "none",
    "event_date_start": "",
    "event_date_end": "",
    "myob_asset_account": "",
    "myob_income_account": "",
    "myob_expense_account": "",
    "peachtree_gl_account": "",
    "condition": "New",
    "is_condition_shown": false,
    "preorder_release_date": "",
    "is_preorder_only": false,
    "preorder_message": "",
    "order_quantity_minimum": 0,
    "order_quantity_maximum": 0,
    "open_graph_type": "product",
    "open_graph_title": "",
    "open_graph_description": "",
    "is_open_graph_thumbnail": true,
    "upc": "",
    "date_last_imported": "",
    "option_set_id": null,
    "tax_class_id": 0,
    "option_set_display": "right",
    "bin_picking_number": "",
    "custom_url": "/startrek/",
    "availability": "available",
    "brand": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/brands/0.json",
        "resource": "/brands/0"
    },
    "images": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/images.json",
        "resource": "/products/29/images"
    },
    "discount_rules": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/discountrules.json",
        "resource": "/products/29/discountrules"
    },
    "configurable_fields": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/configurablefields.json",
        "resource": "/products/29/configurablefields"
    },
    "custom_fields": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/customfields.json",
        "resource": "/products/29/customfields"
    },
    "videos": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/videos.json",
        "resource": "/products/29/videos"
    },
    "skus": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/skus.json",
        "resource": "/products/29/skus"
    },
    "rules": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/rules.json",
        "resource": "/products/29/rules"
    },
    "option_set": null,
    "options": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/options.json",
        "resource": "/products/29/options"
    },
    "tax_class": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/taxclasses/0.json",
        "resource": "/taxclasses/0"
    }
} 
</pre>    

### PUT products/{id}.json
UPDATE a product from a store

#### Request
Here we will update the above created toy name. The fields here are essentially same as the previous one used for POST request except the read only fields - id, rating_total, rating_count, number_sold, date_created, date_modified, date_last_imported.


#### Response
A successful put udpates a product in the store 
<pre>
 {
    "id": 29,
    "keyword_filter": null,
    "name": "Xmen Mystique",
    "type": "physical",
    "sku": "",
    "description": null,
    "search_keywords": null,
    "availability_description": "",
    "price": "19.9900",
    "cost_price": "0.0000",
    "retail_price": "0.0000",
    "sale_price": "0.0000",
    "sort_order": 0,
    "is_visible": false,
    "is_featured": false,
    "related_products": "",
    "inventory_level": 0,
    "inventory_warning_level": 0,
    "warranty": null,
    "weight": "0.0000",
    "width": "0.0000",
    "height": "0.0000",
    "depth": "0.0000",
    "fixed_cost_shipping_price": "0.0000",
    "is_free_shipping": false,
    "inventory_tracking": "none",
    "rating_total": 0,
    "rating_count": 0,
    "total_sold": 0,
    "date_created": "Wed, 12 Dec 2012 20:29:45 +0000",
    "brand_id": 0,
    "view_count": 0,
    "page_title": "",
    "meta_keywords": null,
    "meta_description": null,
    "layout_file": "",
    "is_price_hidden": false,
    "price_hidden_label": "",
    "categories": [
        2
    ],
    "date_modified": "Fri, 21 Dec 2012 00:26:38 +0000",
    "event_date_field_name": "",
    "event_date_type": "none",
    "event_date_start": "",
    "event_date_end": "",
    "myob_asset_account": "",
    "myob_income_account": "",
    "myob_expense_account": "",
    "peachtree_gl_account": "",
    "condition": "New",
    "is_condition_shown": false,
    "preorder_release_date": "",
    "is_preorder_only": false,
    "preorder_message": "",
    "order_quantity_minimum": 0,
    "order_quantity_maximum": 0,
    "open_graph_type": "product",
    "open_graph_title": "",
    "open_graph_description": "",
    "is_open_graph_thumbnail": false,
    "upc": "",
    "date_last_imported": "",
    "option_set_id": null,
    "tax_class_id": 0,
    "option_set_display": "right",
    "bin_picking_number": "",
    "custom_url": "/startrek/",
    "availability": "available",
    "brand": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/brands/0.json",
        "resource": "/brands/0"
    },
    "images": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/images.json",
        "resource": "/products/29/images"
    },
    "discount_rules": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/discountrules.json",
        "resource": "/products/29/discountrules"
    },
    "configurable_fields": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/configurablefields.json",
        "resource": "/products/29/configurablefields"
    },
    "custom_fields": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/customfields.json",
        "resource": "/products/29/customfields"
    },
    "videos": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/videos.json",
        "resource": "/products/29/videos"
    },
    "skus": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/skus.json",
        "resource": "/products/29/skus"
    },
    "rules": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/rules.json",
        "resource": "/products/29/rules"
    },
    "option_set": null,
    "options": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/products/29/options.json",
        "resource": "/products/29/options"
    },
    "tax_class": {
        "url": "https://store-bwvr466.mybigcommerce.com/api/v2/taxclasses/0.json",
        "resource": "/taxclasses/0"
    }
}
</pre>
### GET products/count.json
Get a total number of products in the store

#### Request
This request does not take any parameters.

#### Response
Returns the number of products in the store 
<pre>
  {
    "count": 100
  }
</pre>
Here are resources to delete products. This is a potentially destrutive operation. Remember that you cannot recover deleted products.

### DELETE products.json
DELETE all products

### DELETE products/{id}.json
DELETE a product

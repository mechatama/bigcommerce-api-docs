## Bigcommerce Webhooks Quickstart

#### Currently in beta
Webhoooks is currently in beta and access is by invite only. If you have a strong use case and require access to webhooks, please get in touch with us.

### Webhooks
Think push notification for the web. Assume you want to track various events that occur in a Bigcommerce store - checkout, order, price change, shipping events, etc. You might have built a kick-ass backend service that can act on these events and run some sort of script and analytics. Webhooks enable you to accomplish this.

In a nutshell, you are telling Bigcommerce to notify you when an event occurs in a Bigcommerce store. For this notification to be successful, you provide a script hosted on your web servers (potentially being part of your existing web app).

#### Endpoint
Currently the beta test endpoint for webhooks is at https://hooks-beta.bigcommerce.com

#### Events/Scopes currently available
1. store/order/* (all events on the order resource)
2. store/order/created
3. store/order/updated
4. store/order/archived
5. store/order/statusUpdated
6. store/product/* (all events on the product resource)
7. store/product/created
8. store/product/updated
9. store/product/deleted
10. store/product/lowStockReached (coming soon)
11. store/product/outOfStock (coming soon)
12. store/product/productBackInStock (coming soon)
13. store/product/stockLevelChanged (coming soon)
14. store/product/addedToCart (coming soon)
15. store/product/removedFromCart (coming soon)
16. store/product/ordered (coming soon)
10. store/customer/* (all events on the customer resource)
10. store/customer/created
11. store/customer/updated
12. store/customer/deleted
13. store/app/uninstalled

<a href="/api/webhooks/event_triggers">This page</a> describes in detail the specific triggers for each of the event scopes.

### Provisioning webhooks
When you navigate to https://devportal.bigcommerce.com/beta/wehooks you will be able to provision webhooks for your account. 

![Image](images/webhooks_provision.png?raw=true) 

A client ID and secret will be created for you in your dashboard as shown in the screenshot above.

Once you have provisioned webhooks, you can start subscribing to events from the above events list. However, before doing that, you will need an 'access_token' for each store you are connecting to. You application will need to manage the access_token to store association by itself.

You can generate the access token via a POST request on the /token endpoint. The POST request will contain the fields - client_id, client_secret, user, token, store_domain. The client_id and client_secret are provided to you by the dev portal where as user, token and store_domain are your API credentials that you have traditionally used to make API requests.

<pre>
   curl -XPOST -d '{"client_id":"client123","client_secret":"client123secret","user":"admin","token":"xxxx","store_domain":"https://store-xxxx.mybigcommerce.com"}' https://hooks-beta.bigcommerce.com/token 
</pre>

This will provide a response that contains the access_token and a producer, which is the same as the store id.

<pre> {"access_token":"12345","producer":"store/foobar123"} </pre>

### Events

To subscribe to events you would make a POST request with the following fields - producer, scope, deliverymethod, destination. You also need to define two header fields <code>X-Auth-Client</code> whose value will be the client_id you generated for your app via the Dev Portal (as described above) and <code>X-Auth-Token</code> which has the above generated access_token's value.

<pre>
    curl -XPOST -d '{"producer":"store/xxxx","scope":"store/product/*","deliverymethod":"HTTP_POST","destination":{"url":"https://requestb.in/nf4nqbnf"}}' -H 'X-Auth-Client: client123' -H 'X-Auth-Token: 12345' https://hooks-beta.bigcommerce.com
</pre>

The above example demonstrates how you can subscribe for product updates. Make a note of the "destination" field in the request. This is a JSON object containing a "url" field. Make sure you point this to the location where Bigcommerce sends you notifications. If everything goes well, you will see the following response -

<pre>
    {"client_id":"client123","created_at":"2013-02-12T17:33:04+00:00","deliverymethod":"HTTP_POST","destination":{"url":"https://requestb.in/nf4nqbnf"},"id":33,"producer":"store/xxxx","scope":"store/product/*","updated_at":"2013-02-12T17:33:04+00:00"}
</pre>

### Things to remember regarding Payload

1. In the postback, we send a light payload with only minimum details regarding the events that got triggered. It's up to you how you want to handle the notification in your application. For instance, we will send you details indicating that a product was updated, and you might want to handle it by fetching the new product via an API call.
2. Bulk data imports will trigger the relevant events for every record affected. For example, if you have a hook on store/product/create and then the merchant imports 2,000 products, then there will be 2,000 event postbacks. 
3. Payloads are serialized per hook per store. We are looking at enabling a replay feature down the road. What this means is, based on the serialized payload IDs, 3rd parties can detect if they've missed certain postbacks and then they, via a future update, you will be able call a replay method to get the missing events.

## API Endpoints

### Operations

<table class="table table-bordered table-striped">
	<thead>
		<tr>
			<th>Verb</th>
			<th>Path</th>
			<th>Param (query string)</th>
			<th>Operation</th>
		</tr>
	</thead>

	<tbody>
		<tr><td>POST</td><td>/</td><td></td><td>Create a new webhook</td></tr>
		<tr><td>GET</td><td>/:id</td><td></td><td>Get a detailed information for a webhook of a given :id</td></tr>
		<tr><td>PUT</td><td>/:id</td><td></td><td>Update a webhook of a given :id</td></tr>
		<tr><td>DELETE</td><td>/:id</td><td></td><td>Delete a webhook of a given :id</td></tr>

		<tr><td>GET</td><td>/producer/:producer</td><td></td><td>List all the webhook you have from a given :producer</td></tr>
		<tr><td>GET</td><td>/producer/:producer</td><td>scope=:scope</td><td>List all the webhook you have from a given :producer, filtered by :scope</td></tr>
	</tbody>
</table>

### Payload Fields

<table class="table table-bordered table-striped">
	<thead>
		<tr>
			<th>Field</th>
			<th>Type</th>
			<th>Example</th>
			<th>Description</th>
		</tr>
	</thead>

	<tbody>
		<tr><td><strong>id</strong></td><td>integer</td><td>101</td><td>The ID of the webhook</td></tr>
		<tr><td><strong>producer</strong></td><td>string</td><td>store/d34db33f</td><td>The identifier of the producer of the event (store)</td></tr>
		<tr><td><strong>scope</strong></td><td>string</td><td>store/product/*</td><td>The event you are subscribing to in a "/" delimited path format. Accepts the * wildcard.</td></tr>
		<tr><td><strong>client_id</strong> (read only)</td><td>string</td><td>a85a54c8fae33b2eb3b9d563a4664992</td><td>The client_id of the subscriber</td></tr>
		<tr><td><strong>delivery_method</strong></td><td>string</td><td>HTTP_POST</td><td>The method of delivery for this webhook. At this moment we only support HTTP_POST.</td></tr>	
		<tr><td><strong>destination</strong></td><td>object</td><td>{
		"headers": {
			"X-Auth-Token": "d34db33f"
		},
		"url": "https://superapp.com/webhook/orders"
	}</td><td>The destination of the subscriber. For HTTP_POST type of delivery we allow a "headers" object to be passed in for additional headers.</td></tr>
	
		<tr><td><strong>created_at</strong> (read only)</td><td>string</td><td>2013-01-17T11:27:50+11:00</td><td>The creation timestamp</td></tr>
	
		<tr><td><strong>updated_at</strong> (read only)</td><td>string</td><td>2013-01-17T11:27:50+11:00</td><td>The update timestamp</td></tr>
	</tbody>
	
</table>

## Create (POST) example

#### Request POST /

<pre>
POST / HTTP/1.1
Host: hooks-beta.bigcommerce.com
Content-Type: application/json
X-Auth-Client: d34db33f
X-Auth-Token: a85a54c8fae33b2eb3b9d563a4664992

{
	"producer": "store/74124",
	"scope": "store/order/*",
	"deliverymethod": "HTTP_POST",
	"destination": {
		"headers": {
			"X-Auth-Token": "d34db33f"
		},
		"url": "https://superapp.com/webhook/orders"
	}
}
</pre>

#### CURL
<pre>
curl -XPOST -d '{"producer":"store/74124","scope":"store/order/*","deliverymethod":"HTTP_POST","destination":{"headers":{"X-Auth-Token":"d34db33f"},"url":"https://superapp.com/webhook/orders"}}' -H 'X-Auth-Client: d34db33f' -H 'X-Auth-Token: a85a54c8fae33b2eb3b9d563a4664992' https://hooks-beta.bigcommerce.com

</pre>

#### Response (success)

<pre>
HTTP/1.1 200 Success
Content-Type: application/json

{
	"id": 101,
	"producer": "store/74124",
	"client_id": "d34db33f",
	"scope": "store/order/*",
	"deliverymethod": "HTTP_POST",
	"destination": {
		"headers": {
			"X-Auth-Token": "d34db33f"
		},
		"url": "https://superapp.com/webhook/orders"
	},
	"created_at": "2013-01-17T11:27:50+11:00",
	"updated_at": "2013-01-17T11:27:50+11:00"
}
</pre>

In the case of failure the API endpoint will return with non 200 OK response code.




## Read (GET) example

#### Request GET /:id

<pre>
GET /101 HTTP/1.1
Host: hooks-beta.bigcommerce.com
Accept: application/json
X-Auth-Client: d34db33f
X-Auth-Token: a85a54c8fae33b2eb3b9d563a4664992
</pre>

#### CURL

<pre>
curl -XGET -H 'X-Auth-Client: d34db33f' -H 'X-Auth-Token: a85a54c8fae33b2eb3b9d563a4664992' https://hooks-beta.bigcommerce.com/1
</pre>

#### Response (success)

<pre>
HTTP/1.1 200 Success
Content-Type: application/json

{
	"id": 101,
	"producer": "store/74124",
	"client_id": "d34db33f",
	"scope": "store/order/*",
	"deliverymethod": "HTTP_POST",
	"destination": {
		"headers": {
			"X-Auth-Token": "d34db33f"
		},
		"url": "https://superapp.com/webhook/orders"
	},
	"created_at": "2013-01-17T11:27:50+11:00",
	"updated_at": "2013-01-17T11:27:50+11:00"
}
</pre>




## Update (PUT) example

#### Request PUT /:id

<pre>
PUT /101 HTTP/1.1
Host: hooks-beta.bigcommerce.com
Content-Type: application/json
X-Auth-Client: d34db33f
X-Auth-Token: a85a54c8fae33b2eb3b9d563a4664992

{
	"producer": "store/74124",
	"scope": "store/order/*",
	"deliverymethod": "HTTP_POST",
	"destination": {
		"headers": {
			"X-Auth-Token": "d34db33f"
		},
		"url": "https://superapp.com/webhook/orders_changed"
	}
}
</pre>

#### CURL
<pre>
curl -XPUT -d '{"producer":"store/74124","scope":"store/order/*","deliverymethod":"HTTP_POST","destination":{"headers":{"X-Auth-Token":"d34db33f"},"url":"https://superapp.com/webhook/orders_changed"}}' -H 'X-Auth-Client: d34db33f' -H 'X-Auth-Token: a85a54c8fae33b2eb3b9d563a4664992' https://hooks-beta.bigcommerce.com

</pre>

#### Response (success)

<pre>
HTTP/1.1 200 Success
Content-Type: application/json

{
	"id": 101,
	"producer": "store/74124",
	"client_id": "d34db33f",
	"scope": "store/order/*",
	"deliverymethod": "HTTP_POST",
	"destination": {
		"headers": {
			"X-Auth-Token": "d34db33f"
		},
		"url": "https://superapp.com/webhook/orders_changed"
	},
	"created_at": "2013-01-17T11:27:50+11:00",
	"updated_at": "2013-01-18T11:27:50+11:00"
}
</pre>



## Delete (DELETE) example

#### Request DELETE /:id

<pre>
DELETE /101 HTTP/1.1
Host: hooks-beta.bigcommerce.com
Accept: application/json
X-Auth-Client: d34db33f
X-Auth-Token: a85a54c8fae33b2eb3b9d563a4664992
</pre>

#### CURL

<pre>
curl -XDELETE -H 'X-Auth-Client: d34db33f' -H 'X-Auth-Token: a85a54c8fae33b2eb3b9d563a4664992' https://hooks-beta.bigcommerce.com/1
</pre>

#### Response (success)

<pre>
HTTP/1.1 200 Success
Content-Type: application/json

{
	"id": 101,
	"producer": "store/74124",
	"client_id": "d34db33f",
	"scope": "store/order/*",
	"deliverymethod": "HTTP_POST",
	"destination": {
		"headers": {
			"X-Auth-Token": "d34db33f"
		},
		"url": "https://superapp.com/webhook/orders"
	},
	"created_at": "2013-01-17T11:27:50+11:00",
	"updated_at": "2013-01-17T11:27:50+11:00"
}
</pre>



## Listing hooks by producer (GET) example

#### Request GET /producer/:producer

<pre>
GET /101 HTTP/1.1
Host: hooks-beta.bigcommerce.com
Accept: application/json	
X-Auth-Client: d34db33f
X-Auth-Token: a85a54c8fae33b2eb3b9d563a4664992
</pre>

#### CURL

<pre>
curl -XGET -H 'X-Auth-Client: d34db33f' -H 'X-Auth-Token: a85a54c8fae33b2eb3b9d563a4664992' https://hooks-beta.bigcommerce.com/producer/store/74124
</pre>

#### Response (success)

<pre>
HTTP/1.1 200 Success
Content-Type: application/json

[{
	"id": 101,
	"producer": "store/74124",
	"client_id": "d34db33f",
	"scope": "store/order/*",
	"deliverymethod": "HTTP_POST",
	"destination": {
		"headers": {
			"X-Auth-Token": "d34db33f"
		},
		"url": "https://superapp.com/webhook/orders"
	},
	"created_at": "2013-01-17T11:27:50+11:00",
	"updated_at": "2013-01-17T11:27:50+11:00"
},
{
	"id": 102,
	"producer": "store/74124",
	"client_id": "d34db33f",
	"scope": "store/product/*",
	"deliverymethod": "HTTP_POST",
	"destination": {
		"headers": {
			"X-Auth-Token": "d34db33f"
		},
		"url": "https://superapp.com/webhook/orders"
	},
	"created_at": "2013-01-17T11:27:50+11:00",
	"updated_at": "2013-01-17T11:27:50+11:00"
}]
</pre>


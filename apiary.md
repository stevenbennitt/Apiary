HOST: https://api.bigcommerce.com/stores

# BigCommerce API
Welcome to our v3 API, where we offer a more-efficient model for creating and handling product variants, options, and modifiers.
This API is OAuth-only, but fully backward-compatible with our v2 API.
##Group Customers API

The customers api returns information on customers subscribed to the store and the actions associated with them. A subscriber can be defined as anyone signed up for a store newsletter. If you are looking to login customers, get a current customer or any other action not associated with newsletter actions please see the [Customers Reference](https://developer.bigcommerce.com/api/v2/#customers-reference).

## Customers [/customers/subscribers]

### getSubscribers [GET]

#### Description
Returns a paginated collection of `Subscriber` objects.

#### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
email|query|string|false|Filter items by `email`.
first_name|query|string|false|Filter items by `first_name`.
last_name|query|string|false|Filter items by `last_name`.
source|query|string|false|Filter items by `source`.
order_id|query|integer|false|Filter items by `order_id`.
date_created|query|string|false|Filter items by `date_created`.
date_modified|query|string|false|Filter items by `date_modified`.
page|query|integer|false| Specifies the page number in a limited (paginated) list of products.
limit|query|integer|false| Controls the number of items per page in a limited (paginated) list of products.

#### Responses

Status|Meaning|Description
---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|An array of [Subscriber](object-models.html#Subscriber) objects and metadata.

+ Response 200 (application/json)

        {
          "data": [
            {
              "id": 0,
              "email": "string",
              "first_name": "string",
              "last_name": "string",
              "source": "string",
              "order_id": 1,
              "date_modified": "2017-03-24T23:49:18Z",
              "date_created": "2017-03-24T23:49:18Z"
            }
          ],
          "meta": {
            "pagination": {
              "total": 0,
              "count": 0,
              "per_page": 0,
              "current_page": 0,
              "total_pages": 0,
              "links": {
                "previous": "string",
                "current": "string",
                "next": "string"
              }
            }
          }
        }

### createSubscriber [POST]

Creates a `Subscriber` object.

#### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
subscriber|body|SubscriberPost|true| A `Subscriber` object.


#### Responses

Status|Meaning|Description
---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A [Subscriber](object-models.html#Subscriber) object.
409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|The [Subscriber](object-models.html#Subscriber) was in conflict with another Subscriber. This is caused by duplicate unique values, such as `email`.
422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|The [Subscriber](object-models.html#Subscriber) was not valid. This is caused either by missing required fields, or by invalid data. See the response for more details.

+ Request (application/json)

        {
          "id": 0,
          "email": "string",
          "first_name": "string",
          "last_name": "string",
          "source": "string",
          "order_id": 1
        }

+ Response 200 (application/json)

    + Headers

            Location: /orders/123456/transaction

    + Body
        
            {
              "data": {
                "id": 0,
                "email": "string",
                "first_name": "string",
                "last_name": "string",
                "source": "string",
                "order_id": 1,
                "date_modified": "2017-03-24T23:49:18Z",
                "date_created": "2017-03-24T23:49:18Z"
              },
              "meta": {}
            }

### deleteSubscribers [DELETE]

Deletes one or more `Subscriber` objects from BigCommerce Customers.

#### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
email|query|string|false|Filter items by email.
first_name|query|string|false|Filter items by first_name.
last_name|query|string|false|Filter items by last_name.
source|query|string|false|Filter items by source.
order_id|query|integer|false|Filter items by order_id.
date_created|query|string|false|Filter items by date_created.
date_modified|query|string|false|Filter items by date_modified.


#### Responses

Status|Meaning|Description
---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|An empty response.

## Customer by ID [/customers/subscribers/{subscriber_id}]

### getSubscriberById [GET]

Gets a `Subscriber` object.

#### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
subscriber_id|path|number|true|The ID of the [Subscriber](object-models.html#Subscriber) requested.


#### Responses

Status|Meaning|Description
---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A [Subscriber](object-models.html#Subscriber) object.
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The resource was not found.

+ Response 200 (application/json)

        {
          "data": {
            "id": 0,
            "email": "string",
            "first_name": "string",
            "last_name": "string",
            "source": "string",
            "order_id": 1,
            "date_modified": "2017-03-24T23:49:18Z",
            "date_created": "2017-03-24T23:49:18Z"
          },
          "meta": {}
        }

### updateSubscriber [PUT]

Updates a [Subscriber](object-models.html#Subscriber) object.

#### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
subscriber_id|path|number|true|The ID of the [Subscriber](object-models.html#Subscriber) requested.
subscriber|body|SubscriberPut|true|Returns a [Subscriber](object-models.html#Subscriber) object.



#### Responses

Status|Meaning|Description
---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A [Subscriber](object-models.html#Subscriber) object.
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The resource was not found.
409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|The [Subscriber](object-models.html#Subscriber) was in conflict with another subscriber. This is the result of duplicate unique values, such as `email`.
422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|The [Subscriber](object-models.html#Subscriber) was not valid. This is caused either by missing required fields, or by invalid data. See the response for more details.

+ Request (application/json)

        {
          "id": 0,
          "email": "string",
          "first_name": "string",
          "last_name": "string",
          "source": "string",
          "order_id": 1
        }

+ Response 200 (application/json)

    + Headers

            Location: /orders/123456/transaction

    + Body
           
            {
              "data": {
                "id": 0,
                "email": "string",
                "first_name": "string",
                "last_name": "string",
                "source": "string",
                "order_id": 1,
                "date_modified": "2017-03-24T23:49:18Z",
                "date_created": "2017-03-24T23:49:18Z"
              },
              "meta": {}
            }

### deleteSubscriberById [DELETE]

Deletes a [Subscriber](object-models.html#Subscriber) object.

#### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
subscriber_id|path|number|true|The ID of the [Subscriber](object-models.html#Subscriber) requested.


#### Responses

Status|Meaning|Description
---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|An empty response.


##Group Orders API
You can do lots of things with the Orders API.

## Orders [/stores/{store_id}/v3/orders/{order_id}/transaction]
Orders Transactions By Order Id


### getTransactions [GET]
Returns a collection of `Transaction` objects related to a BigCommerce Order.

#### Parameters 

Parameter|In|Type|Required|Description
---|---|---|---|---|
order_id|path|number|true|The ID of the <a href="/api/v2/#order-object-properties" target="_blank">Order</a> to which the transactions belong.


#### Responses

Status|Meaning|Description
---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|An array of [Transaction](object-models.html#Transaction) objects.
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No content found to fulfill the request.
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The resource was not found.

+ Response 200 (application/json)

        {
          "data": [
            {
              "event": "purchase",
              "method": "credit_card",
              "amount": 0,
              "currency": "string",
              "gateway": "2checkout",
              "gateway_transaction_id": "string",
              "date_created": "2018-02-22T23:20:23.203Z",
              "test": true,
              "status": "ok",
              "fraud_review": true,
              "reference_transaction_id": 0,
              "offline": {
                "display_name": "string"
              },
              "custom": {
                "payment_method": "string"
              },
              "id": 0,
              "order_id": "string",
              "avs_result": {
                "code": "string",
                "message": "string",
                "street_match": "string",
                "postal_match": "string"
              },
              "cvv_result": {
                "code": "string",
                "message": "string"
              },
              "credit_card": {
                "card_type": "string",
                "card_iin": "string",
                "card_last4": "string"
              },
              "gift_certificate": {
                "code": "string",
                "original_balance": 0,
                "starting_balance": 0,
                "remaining_balance": 0,
                "status": "active"
              },
              "store_credit": {
                "remaining_balance": "string"
              }
            }
          ],
          "meta": {
            "pagination": {
              "total": 0,
              "count": 0,
              "per_page": 0,
              "current_page": 0,
              "total_pages": 0,
              "links": {
                "previous": "string",
                "current": "string",
                "next": "string"
              }
            }
          }
        }

### createTransactions [POST]
Creates a new `Transaction` related to a BigCommerce Order.

#### Parameters

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[TransactionPost](object-models.html#Transaction)|true|A BigCommerce `Transaction` object.|
|order_id|path|integer|true|The ID of the `Order` to which the transactions belong.|

#### Responses

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful transaction object created call|[TransactionResponse](#schematransactionresponse)|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No content found to fulfill request.|[NoContent](#schemanocontent)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The resource was not found.|[NotFound](#schemanotfound)|

+ Request (application/json)

        {
          "event": "purchase",
          "method": "credit_card",
          "amount": 0,
          "currency": "string",
          "gateway": "2checkout",
          "gateway_transaction_id": "string",
          "date_created": "2018-02-23T00:54:11.259Z",
          "test": true,
          "status": "ok",
          "fraud_review": true,
          "reference_transaction_id": 0,
          "offline": {
            "display_name": "string"
          },
          "custom": {
            "payment_method": "string"
          }
        }
        
+ Response 200 (application/json)

    + Headers

            Location: /orders/123456/transaction

    + Body

            {
              "data": {
                "event": "purchase",
                "method": "credit_card",
                "amount": 0,
                "currency": "string",
                "gateway": "2checkout",
                "gateway_transaction_id": "string",
                "date_created": "2018-02-23T00:54:11.949Z",
                "test": true,
                "status": "ok",
                "fraud_review": true,
                "reference_transaction_id": 0,
                "offline": {
                  "display_name": "string"
                },
                "custom": {
                  "payment_method": "string"
                },
                "id": 0,
                "order_id": "string",
                "avs_result": {
                  "code": "string",
                  "message": "string",
                  "street_match": "string",
                  "postal_match": "string"
                },
                "cvv_result": {
                  "code": "string",
                  "message": "string"
                },
                "credit_card": {
                  "card_type": "string",
                  "card_iin": "string",
                  "card_last4": "string"
                },
                "gift_certificate": {
                  "code": "string",
                  "original_balance": 0,
                  "starting_balance": 0,
                  "remaining_balance": 0,
                  "status": "active"
                },
                "store_credit": {
                  "remaining_balance": "string"
                }
              },
              "meta": {}
            }
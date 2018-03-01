FORMAT: 1A
HOST: https://api.bigcommerce.com/stores/store_id/v3

# BigCommerce API
Documentation for the Bigcommerce API(should add something here)

# Group Catalog
Bigcommerce Catalog 

## Products [/catalog/products]
`/catalog/products`

### getProducts [GET /catalog/products{?id,name,sku,upc,price,weight,condition,brand_id,date_modified,date_last_imported,is_visible,is_featured,is_free_shipping,inventory_level,inventory_low,out_of_stock,total_sold,type,categories,keyword,keyword_context,status,include,include_fields,exclude_fields,availability,price_list_id,page,limit,direction,sort}]
Returns a paginated collection of `Products` objects from the BigCommerce Catalog.
The results can be filtered. 
An example of a filtered request: 
`https://api.bigcommerce.com/stores/{{store_id}}/v3/catalog/products?id={{id}}&name={{name}}&sku={{sku}}&upc={{upc}}&price={{price}}&weight={{weight}}&condition={{condition}}&brand_id={{brand_id}}&date_modified={{date_modified}}&date_last_imported={{date_last_imported}}&is_visible={{is_visible}}&is_featured={{is_featured}}&is_free_shipping={{is_free_shipping}}&inventory_level={{inventory_level}}&inventory_low={{inventory_low}}&out_of_stock={{out_of_stock}}&total_sold={{total_sold}}&type={{type}}&categories={{categories}}&keyword={{keyword}}&keyword_context={{keyword_context}}&status={{status}}&include={{include}}&include_fields={{include_fields}}&exclude_fields={{exclude_fields}}&availability={{availability}}&price_list_id={{price_list_id}}&page={{page}}&limit={{limit}}&direction={{direction}}&sort={{sort}}`

<div class="test"></div>

+ Parameters
    + id (number, optional)

        Filter items by id.

    + name (string, optional)

        Filter items by name.

    + sku (string, optional)

        Filter items by sku.

    + upc (string, optional)

        Filter items by upc.

    + price (number, optional)

        Filter items by price.

    + weight (number, optional)

        Filter items by weight.

    + condition (number, optional)

        Filter items by condition.

    + brand_id (number, optional)

        Filter items by brand_id.

    + date_modified (string, optional)

        Filter items by date_modified.

    + date_last_imported (string, optional)

        Filter items by date_last_imported.

    + is_visible (number, optional)

        Filter items by is_visible.

    + is_featured (number, optional)

        Filter items by is_featured.

    + is_free_shipping (number, optional)

        Filter items by is_free_shipping.

    + inventory_level (number, optional)

        Filter items by inventory_level.

    + inventory_low (number, optional)

        Filter items by inventory_low. Values: 1, 0.

    + out_of_stock (number, optional)

        Filter items by out_of_stock. To enable the filter, pass `out_of_stock`=`1`.

    + total_sold (number, optional)

        Filter items by total_sold.

    + type (string, optional)

        Filter items by type: `physical` or `digital`.

    + categories (number, optional)

        Filter items by categories.

    + keyword (string, optional)

        Filter items by keywords found in the `name`, `description`, or `sku` fields, or in the brand name.

    + keyword_context (enum[string], optional)

        Set context for a product search.

        + Members
            + `shopper` 
            + `merchant` 

    + status (number, optional)

        Filter items by status.

    + include (enum[string], optional)

        Sub-resources to include on a product, in a comma-separated list. Valid expansions currently include `variants`, `images`, 'primary_image`, `custom_fields`, and `bulk_pricing_rules`.

        + Members
            + `variants` 
            + `images` 
            + `custom_fields` 
            + `bulk_pricing_rules` 
            + `primary_image` 

    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.

    + availability (enum[string], optional)

        Filter items by availability. Values are: available, disabled, preorder.

        + Members
            + `available` 
            + `disabled` 
            + `preorder` 

    + price_list_id (number, optional)

        The ID of the `Price List`.

    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + direction (enum[string], optional)

        Sort direction. Acceptable values are: `asc`, `desc`.

        + Members
            + `asc` 
            + `desc` 

    + sort (enum[string], optional)

        Field name to sort by.

        + Members
            + `id` 
            + `name` 
            + `sku` 
            + `price` 
            + `date_modified` 
            + `date_last_imported` 
            + `inventory_level` 
            + `is_visible` 
            + `total_sold` 


+ Response 200 (application/json)

        An array of products and metadata.



    + Attributes (ProductCollectionResponse)


### createProduct [POST /catalog/products]

Creates a `Product` in the BigCommerce Catalog.

+ Request (application/json)
    + Attributes (ProductPost)


+ Response 200 (application/json)

        A product.



    + Attributes (ProductResponse)


+ Response 409 

        `Product` was in conflict with another product. This is the result of duplicate unique values, such as name or SKU; a missing or invalid `category_id`, `brand_id`, or `tax_class id`; or a conflicting `bulk_pricing_rule`.






+ Response 422 

        `Product` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.


### deleteProducts [DELETE /catalog/products{?name,sku,price,weight,condition,brand_id,date_modified,date_last_imported,is_visible,is_featured,inventory_level,total_sold,type,categories,keyword}]
Deletes one or more `Product` objects from the BigCommerce Catalog.
+ Parameters
    + name (string, optional)

        Filter items by name.

    + sku (string, optional)

        Filter items by sku.

    + price (number, optional)

        Filter items by price.

    + weight (number, optional)

        Filter items by weight.

    + condition (number, optional)

        Filter items by condition.

    + brand_id (number, optional)

        Filter items by brand_id.

    + date_modified (string, optional)

        Filter items by date_modified.

    + date_last_imported (string, optional)

        Filter items by date_last_imported.

    + is_visible (number, optional)

        Filter items by is_visible.

    + is_featured (number, optional)

        Filter items by is_featured.

    + inventory_level (number, optional)

        Filter items by inventory_level.

    + total_sold (number, optional)

        Filter items by total_sold.

    + type (string, optional)

        Filter items by type: `physical` or `digital`.

    + categories (number, optional)

        Filter items by categories.

    + keyword (string, optional)

        Filter items by keywords found in the `name`, `description`, or `sku` fields, or in the brand name.


+ Response 204 

    Returns blank response


## Product by ProductId [/catalog/products/{product_id}]
`/catalog/products/{product_id}`

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.

### getProductById [GET /catalog/products/{product_id}{?include,include_fields,exclude_fields,price_list_id}]
Returns a `Product` from the BigCommerce Catalog.

+ Parameters        
    + include (enum[string], optional)

        Sub-resources to include on a product, in a comma-separated list. Valid expansions currently include `variants`, `images`, 'primary_image`, `custom_fields`, and `bulk_pricing_rules`.

        + Members
            + `variants` 
            + `images` 
            + `custom_fields` 
            + `bulk_pricing_rules` 
            + `primary_image` 

    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.

    + price_list_id (number, optional)

        The ID of the `Price List`.


+ Response 200 (application/json)

        A product.



    + Attributes (ProductResponse)


+ Response 404 

        The resource was not found.


### updateProduct [PUT /catalog/products/{product_id}]
Updates a `Product` in the BigCommerce Catalog.

+ Request (application/json)
    + Attributes (ProductPut)


+ Response 200 (application/json)

        A product.



    + Attributes (ProductResponse)


+ Response 404 

        The resource was not found.

+ Response 409 

        `Product` was in conflict with another product. This is caused by: duplicate unique values, such as name or SKU; a missing category, brand, or tax_class with which the product is being associated; or a conflicting bulk pricing rule.


+ Response 422 

        `Product` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.


### deleteProductById [DELETE /catalog/products/{product_id}]
Deletes a `Product` object from the BigCommerce Catalog.


+ Response 204 

    Blank Response

## Product Images By Product Id [/catalog/products/{product_id}/images]
`/catalog/products/{product_id}/images`

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.

### getProductImages [GET /catalog/products/{product_id}/images{?page,limit,include_fields,exclude_fields}]
Gets all images on a product.

+ Parameters

    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 204 (application/json)

        List of product images and metadata.



    + Attributes (ProductImageCollectionResponse)


+ Response 404 

        The product ID does not exist.


### createProductImage [POST /catalog/products/{product_id}/images]
Creates an image on a product. Publicly accessible URLs and files (form post) are valid parameters.

+ Request (application/json)
    + Attributes (ProductImagePost)


+ Response 200 (application/json)

        A product image.



    + Attributes (ProductImageResponse)


+ Response 404 

        The product ID does not exist.


## Product Images with ImageId [/catalog/products/{product_id}/images/{image_id}]
`/catalog/products/{product_id}/images/{image_id}`

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.

    + image_id (number, required)

        The ID of the `Image` that is being operated on.


### getProductImageById [GET /catalog/products/{product_id}/images/{image_id}{?include_fields,exclude_fields}]
Gets image on a product.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of product images and metadata.



    + Attributes (ProductImageResponse)


+ Response 404 

        The resource was not found.


### updateProductImage [PUT /catalog/products/{product_id}/images/{image_id}]
Updates an image on a product. Publicly accessible URLs and files (form post) are valid parameters.

+ Request (application/json)
    + Attributes (ProductImageBase)


+ Response 200 (application/json)

        A product image.



    + Attributes (ProductImageResponse)


+ Response 404 

        The resource was not found.


### deleteProductImage [DELETE /catalog/products/{product_id}/images/{image_id}]
Deletes a `ProductImage` in the BigCommerce Catalog.

+ Response 204 


## Products Videos By Product Id [/catalog/products/{product_id}/videos]
`/catalog/products/{product_id}/videos`

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.


### getProductVideos [GET /catalog/products/{product_id}/videos{?include_fields,exclude_fields}]
Gets all videos on a product.

+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        List of product videos and metadata.



    + Attributes (ProductVideoCollectionResponse)


### createProductVideo [POST /catalog/products/{product_id}/videos]
Creates a video on a product, using a video ID from a host site.

+ Request (application/json)
    + Attributes (ProductVideoPost)


+ Response 200 (application/json)

        A product video.



    + Attributes (ProductVideoResponse)


+ Response 404 

        The resource was not found.



## Products Videos with VideoId [/catalog/products/{product_id}/videos/{video_id}]
`/catalog/products/{product_id}/videos/{video_id}`

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + video_id (string, required)

        The ID of the `Video` that is being operated on.


### getProductVideoById [GET /catalog/products/{product_id}/videos/{video_id}{?include_fields,exclude_fields}]
Gets video on a product.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of product videos and metadata.



    + Attributes (ProductVideoResponse)


+ Response 404 

        The resource was not found.


### updateProductVideo [PUT /catalog/products/{product_id}/videos/{video_id}]
Updates a video on a product.

+ Request (application/json)
    + Attributes (ProductVideoPut)


+ Response 200 (application/json)

        A product video.



    + Attributes (ProductVideoResponse)


+ Response 404 

        The resource was not found.





### deleteProductVideo [DELETE /catalog/products/{product_id}/videos/{video_id}]
Deletes a `ProductVideo` in the BigCommerce Catalog.

+ Response 204 




## Catalog Products Variants By Product Id [/catalog/products/{product_id}/variants]
`/catalog/products/{product_id}/variants`

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### getVariantsByProductId [GET /catalog/products/{product_id}/variants]
Returns a `Variant` object list from the BigCommerce Catalog.

+ Parameters
    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of variants and metadata.



    + Attributes (VariantCollectionResponse)


+ Response 404 

        The resource was not found.



### createVariant [POST /catalog/products/{product_id}/variants]
Creates a `Variant` object.

+ Request (application/json)
    + Attributes (VariantPost)


+ Response 200 (application/json)

        A variant and metadata.



    + Attributes (VariantResponse)


+ Response 404 

        The resource was not found.



## Catalog Products Variants By Product Id [/catalog/products/{product_id}/variants/{variant_id}]
`/catalog/products/{product_id}/variants/{variant_id}`

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + variant_id (number, required)

        ID of the variant on a product, or on an associated Price List Record.{INT}


### getVariantById [GET /catalog/products/{product_id}/variants/{variant_id}]
Gets a `Variant` object.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        A variant and metadata.



    + Attributes (VariantResponse)


+ Response 404 

        The resource was not found.


### updateVariant [PUT /catalog/products/{product_id}/variants/{variant_id}]
Updates a `Variant` object.

+ Request (application/json)
    + Attributes (VariantPut)


+ Response 200 (application/json)

        A variant and metadata.



    + Attributes (VariantResponse)


+ Response 404 

        The resource was not found.



### deleteVariantById [DELETE /catalog/products/{product_id}/variants/{variant_id}]
Deletes a `Variant`.

+ Response 204 

        A blank response



## Catalog Products Variants Metafields [/catalog/products/{product_id}/variants/{variant_id}/metafields]
`/catalog/products/{product_id}/variants/{variant_id}/metafields`

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + variant_id (number, required)

        ID of the variant on a product, or on an associated Price List Record.{INT}


### getVariantMetafieldsByProductIdAndVariantId [GET /catalog/products/{product_id}/variants/{variant_id}/metafields{?page,limit,key,namespace,include_fields,exclude_fields}]
Gets a `Metafield` object list, by `product_id` and `variant_id`.
+ Parameters
    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + key (string, optional)

        Filter based on a metafield's key.

    + namespace (string, optional)

        Filter based on a metafield's key.

    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of metafields and metadata.



    + Attributes (MetaFieldCollectionResponse)


+ Response 404 

        The resource was not found.



### createVariantMetafield [POST /catalog/products/{product_id}/variants/{variant_id}/metafields]
Creates a variant `Metafield`.

+ Request (application/json)
    + Attributes (MetafieldBase)


+ Response 200 (application/json)

        A `Metafield` object.



    + Attributes (MetafieldResponse)


+ Response 409 

        The `Metafield` was in conflict with another `Metafield`. This can be the result of duplicate unique-key combinations of the app's client id, namespace, key, resource_type, and resource_id.






+ Response 422 

        The `Metafield` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.





## Catalog Products Variants Metafields Metafield Id [/catalog/products/{product_id}/variants/{variant_id}/metafields/{metafield_id}]

+ Parameters
    + metafield_id (number, required)

        The ID of the `Metafield`.{INT}

    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + variant_id (number, required)

        ID of the variant on a product, or on an associated Price List Record.{INT}


### getVariantMetafieldByProductIdAndVariantId [GET /catalog/products/{product_id}/variants/{variant_id}/metafields/{metafield_id}{?include_fields,exclude_fields}]
Gets a `Metafield`, by `product_id` and `variant_id`.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        A `Metafield` object.



    + Attributes (MetafieldResponse)


+ Response 404 

        The resource was not found.



### updateVariantMetafield [PUT /catalog/products/{product_id}/variants/{variant_id}/metafields/{metafield_id}]
Updates a `Metafield` object.

+ Request (application/json)
    + Attributes (MetafieldPut)


+ Response 200 (application/json)

        A metafield and metadata.



    + Attributes (MetafieldResponse)


+ Response 404 

        The resource was not found.






### deleteVariantMetafieldById [DELETE /catalog/products/{product_id}/variants/{variant_id}/metafields/{metafield_id}]
Deletes a `Metafield`.

+ Response 204 




## Catalog Products Variants Image [/catalog/products/{product_id}/variants/{variant_id}/image]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + variant_id (number, required)

        ID of the variant on a product, or on an associated Price List Record.{INT}


### createVariantImage [POST /catalog/products/{product_id}/variants/{variant_id}/image]
+ Attributes
    + image_file (string, required)

        An image file. Supported MIME types include GIF, JPEG, and PNG.


+ Request (application/x-www-form-urlencoded)



+ Response 200 (application/json)

        A ResourceImage and metadata.



    + Attributes (ImageResponse)


+ Response 404 

        The resource was not found.



+ Response 422 

        Image was not valid. This is the result of a missing `image_file` field or of an incorrect file type. See the response for more details.



## Catalog Products Options By Product Id [/catalog/products/{product_id}/options]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### getOptions [GET /catalog/products/{product_id}/options{?page,limit,include_fields,exclude_fields}]
Gets an array of `Option` objects.
+ Parameters
    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of options and metadata.



    + Attributes (OptionCollectionResponse)


+ Response 404 

        The resource was not found.


### createOption [POST /catalog/products/{product_id}/options]
Creates an `Option`.

+ Request (application/json)
    + Attributes (OptionBase)


+ Response 200 (application/json)

        An `Option` object.



    + Attributes (OptionResponse)


+ Response 409 

        Option was in conflict with another option. This is the result of duplicate unique fields, such as `name`.



+ Response 422 

        Option was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.



## Catalog Products Options By Product Id [/catalog/products/{product_id}/options/{option_id}]
`/catalog/products/{product_id}/options/{option_id}`

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.

    + option_id (number, required)

        The ID of the `Option`.


### getOptionById [GET /catalog/products/{product_id}/options/{option_id}{?include_fields,exclude_fields}]
Gets `Option` object by product ID and option ID.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An `Option` object.



    + Attributes (OptionResponse)


+ Response 404 

        The resource was not found.


### updateOption [PUT /catalog/products/{product_id}/options/{option_id}]
Updates a Product's `Option`, based on the `product_id` and `option_id`.

+ Request (application/json)
    + Attributes (OptionBase)


+ Response 200 (application/json)

        An `Option` object.



    + Attributes (OptionResponse)


+ Response 409 

        The `Option` was in conflict with another option. This is the result of duplicate unique fields, such as `name`.


+ Response 422 

        The `Option` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.






### deleteOptionById [DELETE]
Deletes a Product's `Option`, based on the `product_id` and `option_id`.

+ Response 204 




## Catalog Products Options Values [/catalog/products/{product_id}/options/{option_id}/values]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.

    + option_id (number, required)

        The ID of the `Option`.


### getOptionValues [GET /catalog/products/{product_id}/options/{option_id}/values{?include_fields,exclude_fields}]
Gets an array of `OptionValue` objects.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of option values and metadata.



    + Attributes (OptionValueCollectionResponse)



### createOptionValue [POST /catalog/products/{product_id}/options/{option_id}/values]
Creates a `OptionValue`.

+ Request (application/json)
    + Attributes (OptionValueBase)


+ Response 200 (application/json)

        A `OptionValue` object.



    + Attributes (OptionValueResponse)


+ Response 422 

        The `OptionValue` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.



## Catalog Products Options Values Value Id [/catalog/products/{product_id}/options/{option_id}/values/{value_id}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.

    + option_id (number, required)

        The ID of the `Option`.{INT}

    + value_id (number, required)

        The ID of the `Modifier/Option Value`.


### getOptionValueById [GET /catalog/products/{product_id}/options/{option_id}/values/{value_id}{?include_fields,exclude_fields}]
Gets a `OptionValue` by `product_id`, `option_id`, and `value_id`.

+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        A `OptionValue` object.



    + Attributes (OptionValueResponse)


+ Response 404 

        The resource was not found.



### updateOptionValue [PUT /catalog/products/{product_id}/options/{option_id}/values/{value_id}]
Updates a Product's `OptionValue` based on the `product_id`, `option_id`, and `value_id`.

+ Request (application/json)
    + Attributes (OptionValuePut)


+ Response 200 (application/json)

        A `OptionValue` object.



    + Attributes (OptionValueResponse)


+ Response 422 

        The `OptionValue` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.



### deleteOptionValueById [DELETE /catalog/products/{product_id}/options/{option_id}/values/{value_id}]
Deletes a Product's `OptionValue` based on the `product_id`, `option_id`, and `value_id`.

+ Response 204 


## Catalog Products Modifiers By Product Id [/catalog/products/{product_id}/modifiers]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### getModifiers [GET /catalog/products/{product_id}/modifiers{?page,limit,include_fields,exclude_fields}]
Gets an array of `Modifier` objects.
+ Parameters
    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of modifiers and metadata.



    + Attributes (ModifierCollectionResponse)


### createModifier [POST /catalog/products/{product_id}/modifiers]
Creates a `Modifier`.

+ Request (application/json)
    + Attributes (ModifierPost)


+ Response 200 (application/json)

        A `Modifier` object.



    + Attributes (ModifierResponse)


+ Response 409 

        The `Modifier` was in conflict with another option. This is the result of duplicate unique fields, such as `name`.



+ Response 422 

        The `Modifier` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.




## Catalog Products Modifiers By Product Id [/catalog/products/{product_id}/modifiers/{modifier_id}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + modifier_id (number, required)

        The ID of the `Modifier`.{INT}


### getModifierById [GET /catalog/products/{product_id}/modifiers/{modifier_id}{?include_fields,exclude_fields}]
Gets a `Modifier` by product_id and modifier_id.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        A `Modifier` object.



    + Attributes (ModifierResponse)


+ Response 404 

        The resource was not found.


### updateModifier [PUT /catalog/products/{product_id}/modifiers/{modifier_id}]
Updates a Product's `Modifier` based on the `product_id` and `modifier_id`.

+ Request (application/json)
    + Attributes (ModifierBase)


+ Response 200 (application/json)

        A `Modifier` object.



    + Attributes (ModifierResponse)


+ Response 409 

        The `Modifier` was in conflict with another modifier or option. This is the result of duplicate unique fields, such as `name`.


+ Response 422 

        The `Modifier` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.






### deleteModifierById [DELETE /catalog/products/{product_id}/modifiers/{modifier_id}]
Deletes a Product's `Modifier` based on the `product_id` and `modifier_id`.

+ Response 204 



## Catalog Products Modifiers Values [/catalog/products/{product_id}/modifiers/{modifier_id}/values]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + modifier_id (number, required)

        The ID of the `Modifier`.{INT}


### getModifierValues [GET /catalog/products/{product_id}/modifiers/{modifier_id}/values{?include_fields,exclude_fields}]
Gets an array of `ModifierValue` objects.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of modifier values and metadata.



    + Attributes (ModifierValueCollectionResponse)


### createModifierValue [POST /catalog/products/{product_id}/modifiers/{modifier_id}/values]
Creates a `ModifierValue`.

+ Request (application/json)
    + Attributes (ModifierValueBase)


+ Response 200 (application/json)

        A `ModifierValue` object.



    + Attributes (ModifierValueResponse)


+ Response 422 

        The `ModifierValue` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.



## Catalog Products Modifiers Values Value Id [/catalog/products/{product_id}/modifiers/{modifier_id}/values/{value_id}{?include_fields,exclude_fields}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + modifier_id (number, required)

        The ID of the `Modifier`.{INT}

    + value_id (number, required)

        The ID of the `Modifier/Option Value`.{INT}


### getModifierValueById [GET]
Gets a `ModifierValue` by `product_id`, `modifier_id`, and `value_id`.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        A `ModifierValue` object.



    + Attributes (ModifierValueResponse)


+ Response 404 

        The resource was not found.







## Catalog Products Modifiers Values Value Id [/catalog/products/{product_id}/modifiers/{modifier_id}/values/{value_id}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + modifier_id (number, required)

        The ID of the `Modifier`.{INT}

    + value_id (number, required)

        The ID of the `Modifier/Option Value`.{INT}


### updateModifierValue [PUT]
Updates a Product's `ModifierValue` based on the `product_id`, `modifier_id`, and `value_id`.

+ Request (application/json)
    + Attributes (ModifierValuePut)


+ Response 200 (application/json)

        A `ModifierValue` object.



    + Attributes (ModifierValueResponse)


+ Response 422 

        The `ModifierValue` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.






### deleteModifierValueById [DELETE]
Deletes a Product's `ModifierValue` based on the `product_id`, `modifier_id`, and `value_id`.

+ Response 204 




## Catalog Products Modifiers Values Value Id Image [/catalog/products/{product_id}/modifiers/{modifier_id}/values/{value_id}/image]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + modifier_id (number, required)

        The ID of the `Modifier`.{INT}

    + value_id (number, required)

        The ID of the `Modifier`.{INT}


### createModifierImage [POST]
Adds an image to a modifier value; the image will show on the storefront when the value is selected.
+ Attributes
    + image_file (string, required)

        An image file. Supported MIME types include GIF, JPEG, and PNG.


+ Request (application/x-www-form-urlencoded)



+ Response 200 (application/json)

        A ResourceImage and metadata.



    + Attributes (ImageResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        Modifier image was not valid. This is the result of missing `image_file` fields, or of a non-URL value for the `image_file` field. See the response for more details.






### deleteModifierImage [DELETE]
Deletes the image that was set to show when the modifier value is selected.

+ Response 204 




## Catalog Products Complex Rules [/catalog/products/{product_id}/complex-rules{?include_fields,exclude_fields}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### getComplexRules [GET]
Gets an array of `ComplexRule` objects.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of `ComplexRule` objects and metadata.



    + Attributes (ComplexRuleCollectionResponse)



## Catalog Products Complex Rules [/catalog/products/{product_id}/complex-rules]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### createComplexRule [POST]
Creates a `ComplexRule`.

+ Request (application/json)
    + Attributes (ComplexRulePost)


+ Response 200 (application/json)

        A `ComplexRule` object.



    + Attributes (ComplexRuleResponse)


+ Response 409 

        The `ComplexRule` was in conflict with another `ComplexRule`. This is the result of duplicate conditions.






+ Response 422 

        The `ComplexRule` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.







## Catalog Products Complex Rules [/catalog/products/{product_id}/complex-rules/{complex_rule_id}{?include_fields,exclude_fields}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + complex_rule_id (number, required)

        The ID of the `ComplexRule`.{INT}


### getComplexRuleById [GET]
Gets a `ComplexRule` by product_id.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        A `Modifier` object.



    + Attributes (ComplexRuleResponse)


+ Response 404 

        The resource was not found.







## Catalog Products Complex Rules [/catalog/products/{product_id}/complex-rules/{complex_rule_id}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + complex_rule_id (number, required)

        The ID of the `ComplexRule`.{INT}


### updateComplexRule [PUT]
Updates a Product's `ComplexRule`, based on the `product_id` and `complex_rule_id`.

+ Request (application/json)
    + Attributes (ComplexRulePut)


+ Response 200 (application/json)

        A `ComplexRule` object.



    + Attributes (ComplexRuleResponse)


+ Response 409 

        The `ComplexRule` was in conflict with another `ComplexRule`. This is the result of duplicate conditions.






+ Response 422 

        The `ComplexRule` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.






### deleteComplexRuleById [DELETE]
Deletes a Product's `ComplexRule`, based on the `product_id` and `complex_rule_id`.

+ Response 204 




## Catalog Products Configurable Fields [/catalog/products/{product_id}/configurable-fields{?include_fields,exclude_fields,page,limit}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### getConfigurableFields [GET]
Gets an array of `ConfigurableField` objects.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.

    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.


+ Response 200 (application/json)

        An array of `ConfigurableField` objects and metadata.



    + Attributes (ConfigurableFieldCollectionResponse)



## Catalog Products Configurable Fields [/catalog/products/{product_id}/configurable-fields]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### createConfigurableField [POST]
Creates a `ConfigurableField`.

+ Request (application/json)
    + Attributes (ConfigurableFieldBase)


+ Response 200 (application/json)

        A `ConfigurableField` object.



    + Attributes (ConfigurableFieldResponse)


+ Response 404 

        The parent resource was not found.






+ Response 422 

        The `ConfigurableField` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.







## Catalog Products Configurable Fields [/catalog/products/{product_id}/configurable-fields/{configurable_field_id}{?include_fields,exclude_fields}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + configurable_field_id (number, required)

        The ID of the `ConfigurableField`.{INT}


### getConfigurableFieldById [GET]
Gets a `ConfigurableField` by `product_id` and `configurable_field_id`.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        A `ConfigurableField` object.



    + Attributes (ConfigurableFieldResponse)


+ Response 404 

        The resource was not found.







## Catalog Products Configurable Fields [/catalog/products/{product_id}/configurable-fields/{configurable_field_id}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + configurable_field_id (number, required)

        The ID of the `ConfigurableField`.{INT}


### updateConfigurableField [PUT]
Updates a Product's `ConfigurableField`, based on the `product_id` and `configurable_field_id`.

+ Request (application/json)
    + Attributes (ConfigurableField)


+ Response 200 (application/json)

        A `ConfigurableField` object.



    + Attributes (ConfigurableFieldResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        The `ConfigurableField` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.






### deleteConfigurableFieldById [DELETE]
Deletes a Product's `ConfigurableField`, based on the `product_id` and `configurable_field_id`.

+ Response 204 



+ Response 404 

        The resource was not found.







## Catalog Products Custom Fields [/catalog/products/{product_id}/custom-fields{?include_fields,exclude_fields,page,limit}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### getCustomFields [GET]
Gets an array of `CustomField` objects.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.

    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.


+ Response 200 (application/json)

        An array of `CustomField` objects and metadata.



    + Attributes (CustomFieldCollectionResponse)



## Catalog Products Custom Fields [/catalog/products/{product_id}/custom-fields]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### createCustomField [POST]
Creates a `CustomField`.

+ Request (application/json)
    + Attributes (CustomFieldBase)


+ Response 200 (application/json)

        A `CustomField` object.



    + Attributes (CustomFieldResponse)


+ Response 404 

        The parent resource was not found.






+ Response 422 

        The `CustomField` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.







## Catalog Products Custom Fields [/catalog/products/{product_id}/custom-fields/{custom_field_id}{?include_fields,exclude_fields}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + custom_field_id (number, required)

        The ID of the `CustomField`.{INT}


### getCustomFieldById [GET]
Gets a `CustomField` by `product_id` and `custom_field_id`.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        A `CustomField` object.



    + Attributes (CustomFieldResponse)


+ Response 404 

        The resource was not found.







## Catalog Products Custom Fields [/catalog/products/{product_id}/custom-fields/{custom_field_id}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + custom_field_id (number, required)

        The ID of the `CustomField`.{INT}


### updateCustomField [PUT]
Updates a Product's `CustomField`, based on the `product_id` and `custom_field_id`.

+ Request (application/json)
    + Attributes (CustomField)


+ Response 200 (application/json)

        A `CustomField` object.



    + Attributes (CustomFieldResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        The `CustomField` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.






### deleteCustomFieldById [DELETE]
Deletes a Product's `CustomField`, based on the `product_id` and `custom_field_id`.

+ Response 204 



+ Response 404 

        The resource was not found.







## Catalog Products Bulk Pricing Rules [/catalog/products/{product_id}/bulk-pricing-rules{?include_fields,exclude_fields,page,limit}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### getBulkPricingRules [GET]
Gets an array of `BulkPricingRule` objects.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.

    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.


+ Response 200 (application/json)

        An array of `BulkPricingRule` objects and metadata.



    + Attributes (BulkPricingRuleCollectionResponse)


+ Response 404 

        The parent resource was not found.







## Catalog Products Bulk Pricing Rules [/catalog/products/{product_id}/bulk-pricing-rules{?page,limit}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### createBulkPricingRule [POST]
Creates a `BulkPricingRule`.
+ Parameters
    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.


+ Request (application/json)
    + Attributes (BulkPricingRuleBase)


+ Response 200 (application/json)

        A `BulkPricingRule` object.



    + Attributes (BulkPricingRuleResponse)


+ Response 404 

        The parent resource was not found.






+ Response 409 

        The `BulkPricingRule` was in conflict with another bulk pricing rule. This is the result of quantity range overlapping with existing bulk pricing rules.






+ Response 422 

        The `BulkPricingRule` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.







## Catalog Products Bulk Pricing Rules [/catalog/products/{product_id}/bulk-pricing-rules/{bulk_pricing_rule_id}{?include_fields,exclude_fields}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + bulk_pricing_rule_id (number, required)

        The ID of the `BulkPricingRule`.{INT}


### getBulkPricingRuleById [GET]
Gets a `BulkPricingRule` by `product_id` and `bulk_pricing_rule_id`.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        A `BulkPricingRule` object.



    + Attributes (BulkPricingRuleResponse)


+ Response 404 

        The resource or parent resource was not found.







## Catalog Products Bulk Pricing Rules [/catalog/products/{product_id}/bulk-pricing-rules/{bulk_pricing_rule_id}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + bulk_pricing_rule_id (number, required)

        The ID of the `BulkPricingRule`.{INT}


### updateBulkPricingRule [PUT]
Updates a Product's `BulkPricingRule`, based on the `product_id` and `bulk_pricing_rule_id`.

+ Request (application/json)
    + Attributes (BulkPricingRule)


+ Response 200 (application/json)

        A `BulkPricingRule` object.



    + Attributes (BulkPricingRuleResponse)


+ Response 404 

        The resource or parent resource was not found.






+ Response 409 

        The `BulkPricingRule` was in conflict with another bulk pricing rule. This is the result of quantity range overlapping with existing bulk pricing rules.






+ Response 422 

        The `BulkPricingRule` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.






### deleteBulkPricingRuleById [DELETE]
Deletes a Product's `BulkPricingRule`, based on the `product_id` and `bulk_pricing_rule_id`.

+ Response 204 



+ Response 404 

        The resource or parent resource was not found.







## Catalog Products Metafields [/catalog/products/{product_id}/metafields{?page,limit,key,namespace,include_fields,exclude_fields}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### getProductMetafieldsByProductId [GET]
Gets a `Metafield` object list, by `product_id`.
+ Parameters
    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + key (string, optional)

        Filter based on a metafield's key.

    + namespace (string, optional)

        Filter based on a metafield's key.

    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of metafields and metadata.



    + Attributes (MetaFieldCollectionResponse)


+ Response 404 

        The resource was not found.







## Catalog Products Metafields [/catalog/products/{product_id}/metafields]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### createProductMetafield [POST]
Creates a product `Metafield`.

+ Request (application/json)
    + Attributes (MetafieldBase)


+ Response 200 (application/json)

        A `Metafield` object.



    + Attributes (MetafieldResponse)


+ Response 409 

        The `Metafield` was in conflict with another `Metafield`. This can be the result of duplicate unique key combinations of the app's client id, namespace, key, resource_type, and resource_id.






+ Response 422 

        The `Metafield` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.







## Catalog Products Metafields [/catalog/products/{product_id}/metafields/{metafield_id}{?include_fields,exclude_fields}]

+ Parameters
    + metafield_id (number, required)

        The ID of the `Metafield`.{INT}

    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### getProductMetafieldByProductId [GET]
Gets a `Metafield`, by `product_id`.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        A `Metafield` object.



    + Attributes (MetafieldResponse)


+ Response 404 

        The resource was not found.







## Catalog Products Metafields [/catalog/products/{product_id}/metafields/{metafield_id}]

+ Parameters
    + metafield_id (number, required)

        The ID of the `Metafield`.{INT}

    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### updateProductMetafield [PUT]
Updates a `Metafield` object.

+ Request (application/json)
    + Attributes (MetafieldPut)


+ Response 200 (application/json)

        A metafield and metadata.



    + Attributes (MetafieldResponse)


+ Response 404 

        The resource was not found.






### deleteProductMetafieldById [DELETE]
Deletes a `Metafield`.

+ Response 204 




## Catalog Products Reviews By Product Id [/catalog/products/{product_id}/reviews{?include_fields,exclude_fields,page,limit}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### getProductReviews [GET]
Gets all reviews on a product.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.

    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.


+ Response 204 (application/json)

        List of product reviews and metadata.



    + Attributes (ProductReviewCollectionResponse)


+ Response 404 

        The product ID does not exist.







## Catalog Products Reviews By Product Id [/catalog/products/{product_id}/reviews]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}


### createProductReview [POST]
Creates a product review.

+ Request (application/json)
    + Attributes (ProductReviewBase)


+ Response 200 (application/json)

        A product review.



    + Attributes (ProductReviewResponse)


+ Response 404 

        The product ID does not exist.







## Catalog Products Reviews By Product Id [/catalog/products/{product_id}/reviews/{review_id}{?include_fields,exclude_fields}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + review_id (number, required)

        The ID of the `review` that is being operated on.{INT}


### getProductReviewById [GET]
Gets a product review.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of product reviews and metadata.



    + Attributes (ProductReviewResponse)


+ Response 404 

        The resource was not found.







## Catalog Products Reviews By Product Id [/catalog/products/{product_id}/reviews/{review_id}]

+ Parameters
    + product_id (number, required)

        The ID of the `Product` to which the resource belongs.{INT}

    + review_id (number, required)

        The ID of the `review` that is being operated on.{INT}


### updateProductReview [PUT]
Updates a product review.

+ Request (application/json)
    + Attributes (ProductReviewBase)


+ Response 200 (application/json)

        A product review.



    + Attributes (ProductReviewResponse)


+ Response 404 

        The resource was not found.






### deleteProductReview [DELETE]
Deletes a `ProductReview` in the BigCommerce Catalog.

+ Response 204 




## Catalog Categories [/catalog/categories{?name,parent_id,page_title,keyword,is_visible,page,limit,include_fields,exclude_fields}]

### getCategories [GET]
Returns a paginated categories collection from the BigCommerce Catalog.
+ Parameters
    + name (string, optional)

        Filter items by name.

    + parent_id (number, optional)

        Filter items by parent_id.

    + page_title (string, optional)

        Filter items by page_title.

    + keyword (string, optional)

        Filter items by keywords.

    + is_visible (number, optional)

        Filter items by is_visible.

    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of category objects and metadata.



    + Attributes (CategoryCollectionResponse)



## Catalog Categories [/catalog/categories]

### createCategory [POST]
Creates a `Category` in the BigCommerce Catalog.

+ Request (application/json)
    + Attributes (CategoryBase)


+ Response 200 (application/json)

        A category object.



    + Attributes (CategoryResponse)


+ Response 409 

        The `Category` was in conflict with another category. This is the result of duplicate unique values, such as `name` or `custom_url`.






+ Response 422 

        The `Category` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.







## Catalog Categories [/catalog/categories{?name,parent_id,page_title,keyword,is_visible}]

### deleteCategories [DELETE]
Deletes one or more `Category` objects from the BigCommerce Catalog.
+ Parameters
    + name (string, optional)

        Filter items by name.

    + parent_id (number, optional)

        Filter items by parent_id.

    + page_title (string, optional)

        Filter items by page_title.

    + keyword (string, optional)

        Filter items by keywords.

    + is_visible (number, optional)

        Filter items by is_visible.


+ Response 204 




## Catalog Categories By Category Id [/catalog/categories/{category_id}{?include_fields,exclude_fields}]

+ Parameters
    + category_id (number, required)

        The ID of the `Category` to which the resource belongs.{INT}


### getCategoryById [GET]
Returns a `Category` from the BigCommerce Catalog.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        A category object.



    + Attributes (CategoryResponse)


+ Response 404 

        The resource was not found.







## Catalog Categories By Category Id [/catalog/categories/{category_id}]

+ Parameters
    + category_id (number, required)

        The ID of the `Category` to which the resource belongs.{INT}


### updateCategory [PUT]
Updates a `Category` in the BigCommerce Catalog.

+ Request (application/json)
    + Attributes (CategoryBase)


+ Response 200 (application/json)

        A category object.



    + Attributes (CategoryResponse)


+ Response 404 

        The resource was not found.






+ Response 409 

        The `Category` was in conflict with another category. This is the result of duplicate unique values, such as `name` or `custom_url`.






+ Response 422 

        The `Category` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.






### deleteCategoryById [DELETE]
Deletes one or more `Category` objects from the BigCommerce catalog.

+ Response 204 




## Catalog Categories Metafields [/catalog/categories/{category_id}/metafields{?page,limit,key,namespace,include_fields,exclude_fields}]

+ Parameters
    + category_id (number, required)

        The ID of the `Category` to which the resource belongs.{INT}


### getCategoryMetafieldsByCategoryId [GET]
Gets a `Metafield` object list, by category_id.
+ Parameters
    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + key (string, optional)

        Filter based on a metafield's key.

    + namespace (string, optional)

        Filter based on a metafield's key.

    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of metafields and metadata.



    + Attributes (MetaFieldCollectionResponse)


+ Response 404 

        The resource was not found.







## Catalog Categories Metafields [/catalog/categories/{category_id}/metafields]

+ Parameters
    + category_id (number, required)

        The ID of the `Category` to which the resource belongs.{INT}


### createCategoryMetafield [POST]
Creates a product `Metafield`.

+ Request (application/json)
    + Attributes (MetafieldBase)


+ Response 200 (application/json)

        A `Metafield` object.



    + Attributes (MetafieldResponse)


+ Response 409 

        The `Metafield` was in conflict with another `Metafield`. This can be the result of duplicate, unique key combinations of the app's client id, namespace, key, resource_type, and resource_id.






+ Response 422 

        The `Metafield` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.







## Catalog Categories Metafields [/catalog/categories/{category_id}/metafields/{metafield_id}{?include_fields,exclude_fields}]

+ Parameters
    + metafield_id (number, required)

        The ID of the `Metafield`.{INT}

    + category_id (number, required)

        The ID of the `Category` to which the resource belongs.{INT}


### getCategoryMetafieldByCategoryId [GET]
Gets a `Metafield` by category_id.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        A `Metafield` object.



    + Attributes (MetafieldResponse)


+ Response 404 

        The resource was not found.







## Catalog Categories Metafields [/catalog/categories/{category_id}/metafields/{metafield_id}]

+ Parameters
    + metafield_id (number, required)

        The ID of the `Metafield`.{INT}

    + category_id (number, required)

        The ID of the `Category` to which the resource belongs.{INT}


### updateCategoryMetafield [PUT]
Updates a `Metafield` object.

+ Request (application/json)
    + Attributes (MetafieldPut)


+ Response 200 (application/json)

        A metafield and metadata.



    + Attributes (MetafieldResponse)


+ Response 404 

        The resource was not found.






### deleteCategoryMetafieldById [DELETE]
Deletes a `Metafield`.

+ Response 204 




## Catalog Categories Image By Category Id [/catalog/categories/{category_id}/image]

+ Parameters
    + category_id (number, required)

        The ID of the `Category` to which the resource belongs.{INT}


### createCategoryImage [POST]
Creates an image on a category. Publicly accessible URLs and files (form post) are valid parameters.
+ Attributes
    + image_file (string, required)

        An image file. Supported MIME types include GIF, JPEG, and PNG.


+ Request (application/x-www-form-urlencoded)



+ Response 200 (application/json)

        A ResourceImage and metadata.



    + Attributes (ImageResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        Image was not valid. This is the result of a missing `image_file` field or an incorrect file type. See the response for more details.






### deleteCategoryImage [DELETE]
Deletes a `Category` image from the BigCommerce Catalog.

+ Response 204 




## Catalog Categories Tree [/catalog/categories/tree]

### getCategoryTree [GET]
Returns the categories tree, a nested lineage of the categories with parent->child relationship. The `Category` objects returned are simplified versions of the category objects returned in the rest of this API.

+ Response 200 (application/json)

        A array of nested category tree objects and metadata.



    + Attributes (CategoryTreeCollectionResponse)



## Catalog Brands [/catalog/brands{?name,page_title,page,limit,include_fields,exclude_fields}]

### getBrands [GET]
Gets `Brand` objects.
+ Parameters
    + name (string, optional)

        Filter items by name.

    + page_title (string, optional)

        Filter items by page_title.

    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of brand objects and metadata.



    + Attributes (BrandCollectionResponse)



## Catalog Brands [/catalog/brands]

### createBrand [POST]
Creates a `Brand` object.

+ Request (application/json)
    + Attributes (BrandBase)


+ Response 200 (application/json)

        A `Brand` object.



    + Attributes (BrandResponse)


+ Response 409 

        Brand was in conflict with another brand. This is the result of duplicate unique fields such as name.






+ Response 422 

        Brand was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.







## Catalog Brands [/catalog/brands{?name,page_title}]

### deleteBrands [DELETE]
Deletes one or more `Brand` objects from the BigCommerce Catalog.
+ Parameters
    + name (string, optional)

        Filter items by name.

    + page_title (string, optional)

        Filter items by page_title.


+ Response 204 




## Catalog Brands By Brand Id [/catalog/brands/{brand_id}{?include_fields,exclude_fields}]

+ Parameters
    + brand_id (number, required)

        The ID of the `Brand` to which the resource belongs.{INT}


### getBrandById [GET]
Gets a `Brand` object.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        A `Brand` object.



    + Attributes (BrandResponse)


+ Response 404 

        The resource was not found.







## Catalog Brands By Brand Id [/catalog/brands/{brand_id}]

+ Parameters
    + brand_id (number, required)

        The ID of the `Brand` to which the resource belongs.{INT}


### updateBrand [PUT]
Updates a `Brand` in the BigCommerce Catalog.

+ Request (application/json)
    + Attributes (BrandPut)


+ Response 200 (application/json)

        A `Brand` object.



    + Attributes (BrandResponse)


+ Response 404 

        The resource was not found.






+ Response 409 

        The `Brand` was in conflict with another product. This is the result of duplicate unique values, such as `name`.






+ Response 422 

        The `Brand` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.






### deleteBrandById [DELETE]
Deletes a `Brand` from the BigCommerce Catalog.

+ Response 204 




## Catalog Brands Metafields By Brand Id [/catalog/brands/{brand_id}/metafields{?page,limit,key,namespace,include_fields,exclude_fields}]

+ Parameters
    + brand_id (number, required)

        The ID of the `Brand` to which the resource belongs.{INT}


### getBrandMetafieldsByBrandId [GET]
Gets a `Metafield` object list, by `brand_id`.
+ Parameters
    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + key (string, optional)

        Filter based on a metafield's key.

    + namespace (string, optional)

        Filter based on a metafield's key.

    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of metafields and metadata.



    + Attributes (MetaFieldCollectionResponse)


+ Response 404 

        The resource was not found.







## Catalog Brands Metafields By Brand Id [/catalog/brands/{brand_id}/metafields]

+ Parameters
    + brand_id (number, required)

        The ID of the `Brand` to which the resource belongs.{INT}


### createBrandMetafield [POST]
Creates a product `Metafield`.

+ Request (application/json)
    + Attributes (MetafieldBase)


+ Response 200 (application/json)

        A `Metafield` object.



    + Attributes (MetafieldResponse)


+ Response 409 

        The `Metafield` was in conflict with another `Metafield`. This can be the result of duplicate unique key combination of the app's client id, namespace, key, resource_type, and resource_id.






+ Response 422 

        The `Metafield` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.







## Catalog Brands Metafields By Brand Id [/catalog/brands/{brand_id}/metafields/{metafield_id}{?include_fields,exclude_fields}]

+ Parameters
    + metafield_id (number, required)

        The ID of the `Metafield`.{INT}

    + brand_id (number, required)

        The ID of the `Brand` to which the resource belongs.{INT}


### getBrandMetafieldByBrandId [GET]
Gets a `Metafield`, by `category_id`.
+ Parameters
    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        A `Metafield` object.



    + Attributes (MetafieldResponse)


+ Response 404 

        The resource was not found.







## Catalog Brands Metafields By Brand Id [/catalog/brands/{brand_id}/metafields/{metafield_id}]

+ Parameters
    + metafield_id (number, required)

        The ID of the `Metafield`.{INT}

    + brand_id (number, required)

        The ID of the `Brand` to which the resource belongs.{INT}


### updateBrandMetafield [PUT]
Updates a `Metafield` object.

+ Request (application/json)
    + Attributes (MetafieldPut)


+ Response 200 (application/json)

        A metafield and metadata.



    + Attributes (MetafieldResponse)


+ Response 404 

        The resource was not found.






### deleteBrandMetafieldById [DELETE]
Deletes a `Metafield`.

+ Response 204 




## Catalog Brands Image By Brand Id [/catalog/brands/{brand_id}/image]

+ Parameters
    + brand_id (number, required)

        The ID of the `Brand` to which the resource belongs.{INT}


### createBrandImage [POST]
Creates an image on a `Brand`. Publicly accessible URLs and files (form post) are valid parameters.
+ Attributes
    + image_file (string, required)

        An image file. Supported MIME types include GIF, JPEG, and PNG.


+ Request (application/x-www-form-urlencoded)



+ Response 200 (application/json)

        A ResourceImage and metadata.



    + Attributes (ImageResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        Image was not valid. This is the result of a missing `image_file` field, or of an incorrect file type. See the response for more details.






### deleteBrandImage [DELETE]
Deletes a `Brand` image from the BigCommerce Catalog.

+ Response 204 




## Catalog Variants [/catalog/variants{?id,sku,page,limit,include_fields,exclude_fields}]

### getVariants [GET]
Returns a `Variant` object list from the BigCommerce Catalog.
+ Parameters
    + id (number, optional)

        Filter items by id.

    + sku (string, optional)

        Filter items by sku.

    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + include_fields (string, optional)

        Fields to include, in a comma-separated list. The ID and the specified fields will be returned.

    + exclude_fields (string, optional)

        Fields to exclude, in a comma-separated list. The specified fields will be excluded from a response. The ID cannot be excluded.


+ Response 200 (application/json)

        An array of variants and metadata.



    + Attributes (VariantCollectionResponse)


+ Response 404 

        The resource was not found.







## Catalog Summary [/catalog/summary]

### CatalogSummary [GET]
Returns a lightweight inventory summary from the BigCommerce Catalog.

+ Response 200 (application/json)

        An array of catalog summary and metadata.



    + Attributes (CatalogSummaryResponse)




# Group Customers

## Customers Subscribers [/customers/subscribers{?email,first_name,last_name,source,order_id,date_created,date_modified,page,limit}]

### getSubscribers [GET]
Returns a paginated Subscribers collection.
+ Parameters
    + email (string, optional)

        Filter items by email.

    + first_name (string, optional)

        Filter items by first_name.

    + last_name (string, optional)

        Filter items by last_name.

    + source (string, optional)

        Filter items by source.

    + order_id (number, optional)

        Filter items by order_id.

    + date_created (string, optional)

        Filter items by date_created.

    + date_modified (string, optional)

        Filter items by date_modified.

    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.


+ Response 200 (application/json)

        An array of subscriber objects and metadata.



    + Attributes (SubscriberCollectionResponse)



## Customers Subscribers [/customers/subscribers]

### createSubscriber [POST]
Creates a `Subscriber` object.

+ Request (application/json)
    + Attributes (SubscriberBase)


+ Response 200 (application/json)

        A `Subscriber` object.



    + Attributes (SubscriberResponse)


+ Response 409 

        The `Subscriber` was in conflict with another subscriber. This is the result of duplicate unique values, such as email.






+ Response 422 

        The `Subscriber` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.







## Customers Subscribers [/customers/subscribers{?email,first_name,last_name,source,order_id,date_created,date_modified}]

### deleteSubscribers [DELETE]
Deletes a Subscriber or Subscribers from BigCommerce Customers.
+ Parameters
    + email (string, optional)

        Filter items by email.

    + first_name (string, optional)

        Filter items by first_name.

    + last_name (string, optional)

        Filter items by last_name.

    + source (string, optional)

        Filter items by source.

    + order_id (number, optional)

        Filter items by order_id.

    + date_created (string, optional)

        Filter items by date_created.

    + date_modified (string, optional)

        Filter items by date_modified.


+ Response 204 




## Customers Subscribers By Subscriber Id [/customers/subscribers/{subscriber_id}]

+ Parameters
    + subscriber_id (number, required)

        The ID of the `Subscriber` requested.{INT}


### getSubscriberById [GET]
Gets `Subscriber` object.

+ Response 200 (application/json)

        A `Subscriber` object.



    + Attributes (SubscriberResponse)


+ Response 404 

        The resource was not found.






### updateSubscriber [PUT]
Updates a `Subscriber` object.

+ Request (application/json)
    + Attributes (SubscriberBase)


+ Response 200 (application/json)

        A `Subscriber` object.



    + Attributes (SubscriberResponse)


+ Response 404 

        The resource was not found.






+ Response 409 

        The `Subscriber` was in conflict with another subscriber. This is the result of duplicate unique values, such as `email`.






+ Response 422 

        The `Subscriber` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.






### deleteSubscriberById [DELETE]
Deletes a `Subscriber` object.

+ Response 204 





# Group Orders

## Orders Transactions By Order Id [/orders/{order_id}/transactions]

+ Parameters
    + order_id (number, required)

        The ID of the `Order` to which the transactions belong.{INT}


### getTransactions [GET]
Returns a collection of `Transaction` objects related to a BigCommerce Order.

+ Response 204 (application/json)

        An array of transactions.



    + Attributes (TransactionCollectionResponse)


+ Response 404 

        The resource was not found.






### createTransaction [POST]
Creates a new `Transaction` related to a BigCommerce Order.

+ Request (application/json)
    + Attributes (TransactionPost)


+ Response 204 (application/json)

        Successful transaction object created call



    + Attributes (TransactionResponse)


+ Response 404 

        The resource was not found.








# Group Themes

## Themes [/themes]

### getStoreThemes [GET]
Gets all store themes.

+ Response 200 (application/json)

        Returns all themes associated with the BigCommerce store.

    + Attributes (ThemesCollectionResponse)


+ Response 0 

        Error message.




### uploadTheme [POST]
Uploads a new theme to a BigCommerce store.
+ Attributes
    + file (string, required)

        The file.


+ Request (application/x-www-form-urlencoded)



+ Response 201 (application/json)

        Job ID for the background job processing the theme upload.

    + Attributes (JobId)


+ Response 0 

        Error message.





## Themes By Theme Id [/themes/{theme_id}]

+ Parameters
    + theme_id (string, required)

        The theme identifier.


### getStoreTheme [GET]
Gets a specified store theme.

+ Response 200 (application/json)

        The theme.

    + Attributes (ThemeResponse)


+ Response 0 

        Error message.




### deleteStoreTheme [DELETE]
Deletes a specified store theme.

+ Response 204 (application/json)

        No content found to fulfill the request.



    + Attributes (NoContent)


+ Response 0 

        Error message.





## Themes Actions Download By Theme Id [/themes/{theme_id}/actions/download]

+ Parameters
    + theme_id (string, required)

        The theme identifier.


### downloadTheme [POST]
Downloads a specified store theme.

+ Request (application/json)
    + Attributes (WhichThemeToDownload)


+ Response 200 (application/json)

        Job ID for the background job processing the download.



    + Attributes (JobId)


+ Response 0 

        Error message.





## Themes Actions Activate [/themes/actions/activate]

### activateStoreTheme [POST]
Activates a store theme.

+ Request (application/json)
    + Attributes (Activate)


+ Response 204 (application/json)

        No content found to fulfill the request.



    + Attributes (NoContent)


+ Response 0 

        Error message.





## Themes Jobs By Job Id [/themes/jobs/{job_id}]

+ Parameters
    + job_id (string, required)

        The job identifier.


### getJob [GET]
Gets a specified job.

+ Response 200 (application/json)

        The job.

    + Attributes (JobResponse)


+ Response 0 

        Error message.






# Group PriceLists

## Pricelists [/pricelists{?id,name,date_created,date_modified,page,limit}]

### getPriceListCollection [GET]
Returns a paginated collection of `Price List` objects from BigCommerce.
+ Parameters
    + id (number, optional)

        Filter items by id.

    + name (string, optional)

        Filter items by name.

    + date_created (string, optional)

        Filter items by date_created.

    + date_modified (string, optional)

        Filter items by date_modified.

    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.


+ Response 200 (application/json)

        An array of Price Lists and metadata.



    + Attributes (PriceListCollectionResponse)



## Pricelists [/pricelists]

### createPriceList [POST]
Creates a `Price List` in BigCommerce.

+ Request (application/json)
    + Attributes (PriceListBase)


+ Response 200 (application/json)

        A Price List.



    + Attributes (PriceListResponse)


+ Response 409 

        `Price List` was in conflict with another Price List. This is the result of duplicate unique values, such as `name`.






+ Response 422 

        `Price List` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.







## Pricelists [/pricelists{?id,name}]

### deletePriceListsByFilter [DELETE]
Deletes a set of `Price List` objects from BigCommerce using a filter. Also removes all associated Price Recordss.
+ Parameters
    + id (number, optional)

        Filter items by id.

    + name (string, optional)

        Filter items by name.


+ Response 204 




## Pricelists By Price List Id [/pricelists/{price_list_id}]

+ Parameters
    + price_list_id (number, required)

        The ID of the `Price List` requested.{INT}


### getPriceList [GET]
Returns a `Price List` object from BigCommerce.

+ Response 200 (application/json)

        An array of Price Lists and metadata.



    + Attributes (PriceListResponse)


### updatePriceList [PUT]
Updates a single `Price List` object.

+ Request (application/json)
    + Attributes (PriceListBase)


+ Response 200 (application/json)

        A Price List.



    + Attributes (PriceListResponse)


+ Response 404 

        The resource was not found.






+ Response 409 

        `Price List` was in conflict with another Price List. This is the result of duplicate unique values, such as `name`.






+ Response 422 

        `Price List` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.






### deletePriceList [DELETE]
Deletes one `Price List` object from BigCommerce by its ID. Also removes all associated Price Records.

+ Response 204 




## Pricelists Records By Price List Id [/pricelists/{price_list_id}/records{?variant_id,product_id,currency,page,limit,include,price,sale_price,retail_price,map_price,calculated_price,date_created,date_modified}]

+ Parameters
    + price_list_id (number, required)

        The ID of the `Price List` requested.{INT}


### getPriceListRecordCollection [GET]
Fetches the `Price Records` associated with a particular Price List, using a filter.
+ Parameters
    + variant_id (number, optional)

        The ID of the `Variant` whose prices were requested.

    + product_id (string, optional)

        A comma-separated list of ids of `Product`s whose prices were requested.

    + currency (string, optional)

        Filter items by currency.

    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + include (enum[string], optional)

        Sub-resources to include on a price record, in a comma-separated list. Valid expansions currently include `bulk_pricing_tiers` and `sku`.  Other valies will be ignored.

        + Members
            + `bulk_pricing_tiers` 
            + `sku` 

    + price (number, optional)

        Filter items by price.

    + sale_price (number, optional)

        Filter items by sale_price.

    + retail_price (number, optional)

        Filter items by retail_price.

    + map_price (number, optional)

        Filter items by map_price.

    + calculated_price (number, optional)

        Filter items by calculated_price.

    + date_created (string, optional)

        Filter items by date_created.

    + date_modified (string, optional)

        Filter items by date_modified.


+ Response 200 (application/json)

        An array of prices and metadata.



    + Attributes (PriceRecordCollectionResponse)



## Pricelists Records By Price List Id [/pricelists/{price_list_id}/records]

+ Parameters
    + price_list_id (number, required)

        The ID of the `Price List` requested.{INT}


### setPriceListRecordCollection [PUT]
Creates or updates a batch of `Price Records` associated with a particular Price List.

+ Request (application/json)
    + Attributes (PriceRecordBatchItem)


+ Response 200 

        Success response for batch PUT of `Price Records`.



    + Attributes (object)


+ Response 422 

        Error response for batch PUT of `Price Records`.  May include errors during partial update in non-strict mode.







## Pricelists Records By Price List Id [/pricelists/{price_list_id}/records{?variant_id}]

+ Parameters
    + price_list_id (number, required)

        The ID of the `Price List` requested.{INT}


### deletePriceListRecordsByFilter [DELETE]
Deletes one or more `Price Record` objects from BigCommerce using a filter.
+ Parameters
    + variant_id (number, optional)

        The ID of the `Variant` whose prices were requested.


+ Response 204 (application/json)

        An empty response.



    + Attributes (NoContent)



## Pricelists Records By Price List Id [/pricelists/{price_list_id}/records/{variant_id}]

+ Parameters
    + price_list_id (number, required)

        The ID of the `Price List` requested.{INT}

    + variant_id (number, required)

        ID of the variant on a product, or on an associated Price List Record.{INT}


### getPriceListRecordsByVariantId [GET]
Fetches an array of `Price Records` matching a particular Price List and Variant ID. Will contain any set price records by currency.

+ Response 200 (application/json)

        An array of prices and metadata.



    + Attributes (PriceRecordCollectionResponse)


### deletePriceListRecordsByVariantId [DELETE]
Deletes the collection of `Price Record` objects associated with a certain price list and variant ID.

+ Response 204 




## Pricelists Records Currency Code [/pricelists/{price_list_id}/records/{variant_id}/{currency_code}{?include}]

+ Parameters
    + price_list_id (number, required)

        The ID of the `Price List` requested.{INT}

    + variant_id (number, required)

        ID of the variant on a product, or on an associated Price List Record.{INT}

    + currency_code (string, required)

        The currency code associated with the price record being acted upon.


### getPriceListRecord [GET]
Returns a `Price Record` object from BigCommerce.
+ Parameters
    + include (enum[string], optional)

        Sub-resources to include on a price record, in a comma-separated list. Valid expansions currently include `bulk_pricing_tiers` and `sku`.  Other valies will be ignored.

        + Members
            + `bulk_pricing_tiers` 
            + `sku` 


+ Response 200 (application/json)

        An array of prices and metadata.



    + Attributes (PriceRecordResponse)



## Pricelists Records Currency Code [/pricelists/{price_list_id}/records/{variant_id}/{currency_code}]

+ Parameters
    + price_list_id (number, required)

        The ID of the `Price List` requested.{INT}

    + variant_id (number, required)

        ID of the variant on a product, or on an associated Price List Record.{INT}

    + currency_code (string, required)

        The currency code associated with the price record being acted upon.


### setPriceListRecord [PUT]
Creates or updates a single `Price Record` object.

+ Request (application/json)
    + Attributes (PriceRecordBase)


+ Response 200 (application/json)

        A price record.



    + Attributes (PriceRecordResponse)


+ Response 404 

        The resource was not found.






+ Response 409 

        `Price Record` was in conflict with another price record. This is the result of duplicate unique values.






+ Response 422 

        `Price Record` was not valid. This is the result of missing required fields, or of invalid data. See the response for more details.






### deletePriceListRecord [DELETE]
Deletes one `Price Record` object from BigCommerce, by `variant_id`.

+ Response 204 





# Group Widget Template

## Content Widget Templates [/content/widget-templates{?page,limit,widget_template_kind}]

### getWidgetTemplates [GET]
Gets all widget templates.
+ Parameters
    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + widget_template_kind (string, optional)

        The kind of widget template.


+ Response 200 (application/json)

        Success

    + Attributes (WidgetTemplatesResponse)


+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.







## Content Widget Templates [/content/widget-templates]

### createWidgetTemplate [POST]
Creates a widget template.

+ Request (application/json)
    + Attributes (WidgetTemplatePost)


+ Response 201 (application/json)

        A widget template.



    + Attributes (WidgetTemplateResponse)


+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.







## Content Widget Templates By Uuid [/content/widget-templates/{uuid}]

+ Parameters
    + uuid (string, required)

        The identifier for a specific template.


### getWidgetTemplate [GET]
Gets a widget template.

+ Response 200 (application/json)

        Success

    + Attributes (WidgetTemplateResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.






### updateWidgetTemplate [PUT]
Updates a widget template.

+ Request (application/json)
    + Attributes (WidgetTemplatePut)


+ Response 200 (application/json)

        Success

    + Attributes (WidgetTemplateResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.






### deleteWidgetTemplate [DELETE]
Deletes a widget template.

+ Response 204 



+ Response 404 

        The resource was not found.






+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.







## Content Widget Templates Preview By Uuid [/content/widget-templates/{uuid}/preview]

+ Parameters
    + uuid (string, required)

        The identifier for a specific template.


### previewWidget [POST]
Render a widget template and return the widget html.

+ Request (application/json)
    + Attributes (WidgetTemplatePreview)


+ Response 200 (application/json)

        Success

    + Attributes (WidgetTemplatePreviewResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.








# Group Widget

## Content Widgets [/content/widgets{?page,limit,widget_template_kind,widget_template_uuid}]

### getWidgets [GET]
Gets all widgets.
+ Parameters
    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + widget_template_kind (string, optional)

        The kind of widget template.

    + widget_template_uuid (string, optional)

        The identifier for a specific widget template.


+ Response 200 (application/json)

        Success

    + Attributes (WidgetsResponse)


+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.







## Content Widgets [/content/widgets]

### createWidget [POST]
Creates a widget.

+ Request (application/json)
    + Attributes (WidgetPost)


+ Response 200 (application/json)

        Success

    + Attributes (WidgetResponse)


+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.







## Content Widgets By Uuid [/content/widgets/{uuid}]

+ Parameters
    + uuid (string, required)

        The identifier for a specific widget.


### getWidget [GET]
Gets a widget.

+ Response 200 (application/json)

        Success

    + Attributes (WidgetResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.






### updateWidget [PUT]
Updates a widget.

+ Request (application/json)
    + Attributes (WidgetPut)


+ Response 200 (application/json)

        Success

    + Attributes (WidgetResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.






### deleteWidget [DELETE]
Deletes a widget.

+ Response 204 



+ Response 404 

        The resource was not found.






+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.







## Content Widgets Search [/content/widgets/search{?page,limit,query}]

### searchWidgets [GET]
Gets all widgets by search.
+ Parameters
    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + query (string, optional)

        The query string associated with a widget's name and description.


+ Response 200 (application/json)

        Success

    + Attributes (WidgetsResponse)


+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.








# Group Placement

## Content Placements [/content/placements{?page,limit,widget_template_kind,template_file,widget_uuid,widget_template_uuid}]

### getPlacements [GET]
Gets all placements.
+ Parameters
    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.

    + widget_template_kind (string, optional)

        The kind of widget template.

    + template_file (string, optional)

        The template file, for example: `pages/home`.

    + widget_uuid (string, optional)

        The identifier for a specific widget.

    + widget_template_uuid (string, optional)

        The identifier for a specific widget template.


+ Response 200 (application/json)

        Success

    + Attributes (PlacementsResponse)


+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.







## Content Placements [/content/placements]

### createPlacement [POST]
Creates a placement.

+ Request (application/json)
    + Attributes (PlacementPost)


+ Response 201 (application/json)

        A placement.



    + Attributes (PlacementResponse)


+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.







## Content Placements By Uuid [/content/placements/{uuid}]

+ Parameters
    + uuid (string, required)

        The identifier for a specific placement.


### getPlacement [GET]
Gets a placement.

+ Response 200 (application/json)

        Success

    + Attributes (PlacementResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.






### updatePlacement [PUT]
Updates a placement.

+ Request (application/json)
    + Attributes (PlacementPut)


+ Response 200 (application/json)

        Success

    + Attributes (PlacementResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.






### deletePlacement [DELETE]
Deletes a placement.

+ Response 204 



+ Response 404 

        The resource was not found.






+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.








# Group Script

## Content Scripts [/content/scripts{?page,limit}]

### getScripts [GET]
Gets all scripts.
+ Parameters
    + page (number, optional)

        Specifies the page number in a limited (paginated) list of products.

    + limit (number, optional)

        Controls the number of items per page in a limited (paginated) list of products.


+ Response 201 (application/json)

        Success.



    + Attributes (ScriptsResponse)


+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.







## Content Scripts [/content/scripts]

### createScript [POST]
Creates a script.

+ Request (application/json)
    + Attributes (ScriptPost)


+ Response 201 (application/json)

        Success.



    + Attributes (ScriptResponse)


+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.







## Content Scripts By Uuid [/content/scripts/{uuid}]

+ Parameters
    + uuid (string, required)

        The identifier for a specific script.


### getScript [GET]
Gets a script.

+ Response 200 (application/json)

        Success

    + Attributes (ScriptResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.






### updateScript [PUT]
Updates a script.

+ Request (application/json)
    + Attributes (ScriptPut)


+ Response 200 (application/json)

        Success

    + Attributes (ScriptResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.






### deleteScript [DELETE]
Deletes a script.

+ Response 204 



+ Response 404 

        The resource was not found.






+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.








# Group Theme Regions

## Content Regions [/content/regions{?templateFile}]

### getRegions [GET]
Get an ordered list of unique regions defined in a template file.
+ Parameters
    + templateFile (string, required)

        The template file, for example: `pages/home`.


+ Response 200 (application/json)

        Success

    + Attributes (ThemeRegionsResponse)


+ Response 404 

        The resource was not found.






+ Response 422 

        This is the result of missing required fields, or of invalid data. See the response for more details.








# Data Structures

## WidgetTemplatePreview (object)


### Properties
+ `widget_configuration` (object, optional) - The JSON data that populates the template.


## WidgetTemplatePut (object)


### Properties
+ `name` (string, optional) - User-friendly name.
+ `schema` (object, optional) - The schema for this template. Describes how to build dynamic forms for widget configurations.
+ `template` (string, optional) - Handlebars HTML content. Also has access to Stencil Paper helpers.


## WidgetTemplatePost (object)


### Properties
+ `name` (string, required) - User friendly name.
+ `template` (string, required) - Handlebars HTML content. Also has access to Stencil Paper helpers.
+ `schema` (object, optional) - The JSON schema of data for this template. Used to validate a configuration.


## WidgetTemplateResponse (object)


### Properties
+ `data` (WidgetTemplate, optional) 


## WidgetTemplate (object)


### Properties
+ `uuid` (string, optional) - The primary identifier.
+ `name` (string, optional) - The user-friendly name.
+ `kind` (string, optional) - The kind of widget template.
+ `schema` (object, optional) - The JSON schema of data for this template. Used to validate a configuration.
+ `template` (string, optional) - The widget template HTML. Supports Handlebars and Paper helpers.
+ `date_created` (string, optional) - The date on which this object was initially created.
+ `date_modified` (string, optional) - The date on which this object was last updated.


## WidgetTemplatePreviewResponse (object)


### Properties
+ `data` (Data, optional) 


## Data (object)


### Properties
+ `html` (string, optional) - The HTML render of the widget template.


## WidgetTemplatesResponse (object)


### Properties
+ `data` (array[WidgetTemplate], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## CollectionMeta (object)
Data about the response, including pagination and collection totals.



### Properties
+ `pagination` (Pagination, optional) - Data about the response, including pagination and collection totals.


## Pagination (object)
Data about the response, including pagination and collection totals.



### Properties
+ `total` (number, optional) - Total number of items in the result set.
+ `count` (number, optional) - Total number of items in the collection response.
+ `per_page` (number, optional) - The amount of items returned in the collection per page, controlled by the limit parameter.
+ `current_page` (number, optional) - The page you are currently on within the collection.
+ `total_pages` (number, optional) - The total number of pages in the collection.
+ `links` (Links, optional) - Pagination links for the previous and next parts of the whole collection.


## Links (object)


### Properties
+ `previous` (string, optional) - Link to the previous page returned in the response.
+ `current` (string, optional) - Link to the current page returned in the response.
+ `next` (string, optional) - Link to the next page returned in the response.


## Widget (object)


### Properties
+ `uuid` (string, optional) - The primary identifier.
+ `name` (string, optional) - The user-friendly name.
+ `description` (string, optional) - The user-friendly description.
+ `widget_configuration` (object, optional) - The JSON data that populates the template.
+ `widget_template` (WidgetTemplate, optional) 
+ `date_created` (string, optional) - The date on which this object was initially created.
+ `date_modified` (string, optional) - The date on which this object was last updated.


## WidgetPost (object)


### Properties
+ `name` (string, required) - User friendly name.
+ `widget_template_uuid` (string, required) - The widget template UUID.
+ `description` (string, optional) - The user-friendly description.
+ `widget_configuration` (object, optional) - The JSON data that populates the template.


## WidgetPut (object)


### Properties
+ `name` (string, optional) - User-friendly name.
+ `description` (string, optional) - The user-friendly description.
+ `widget_configuration` (object, optional) - The JSON data that populates the template.
+ `widget_template_uuid` (string, optional) - The widget template UUID.


## WidgetResponse (object)


### Properties
+ `data` (Widget, optional) 


## WidgetsResponse (object)


### Properties
+ `data` (array[Widget], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## PlacementPost (object)


### Properties
+ `widget_uuid` (string, required) - A widget identifier.
+ `region` (string, required) - The name of the region in which to insert content widgets.
+ `template_file` (string, required) - The template file that you would like to target.
+ `entity_id` (string, optional) - The specific instance of a page that you would like to target.
+ `sort_order` (number, optional) - The sort order to control the position of a content widget in a region.
+ `status` (enum[string], optional) - Sets the placement as either inactive or active.
    + `inactive`
    + `active`


## PlacementPut (object)


### Properties
+ `entity_id` (string, optional) - Optional. The specific instance of a page that you would like to target.
+ `template_file` (string, optional) - The template file that you would like to target.
+ `region` (string, optional) - The name of the region in which to insert content widgets.
+ `sort_order` (number, optional) - The sort order to control the position of a content widget in a region.
+ `widget_uuid` (string, optional) - A widget identifier.
+ `status` (enum[string], optional) - Sets the placement as either inactive or active.
    + `inactive`
    + `active`


## PlacementResponse (object)


### Properties
+ `data` (Placement, optional) 


## Placement (object)


### Properties
+ `uuid` (string, optional) - The primary identifier.
+ `entity_id` (string, optional) - The specific instance of a page
+ `status` (enum[string], optional) - Determines whether this placement is `active` or `inactive`.
    + `inactive`
    + `active`
+ `template_file` (string, optional) - The page template name.
+ `region` (string, optional) - The user-friendly name.
+ `sort_order` (number, optional) - The sort order to control position of a content widget in a region.
+ `widget` (Widget, optional) 
+ `date_created` (string, optional) - The date on which this object was initially created.
+ `date_modified` (string, optional) - The date on which this object was last updated.


## PlacementsResponse (object)


### Properties
+ `data` (array[Placement], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## Script (object)


### Properties
+ `uuid` (string, optional) - The primary identifier.
+ `name` (string, optional) - The user-friendly name.
+ `description` (string, optional) - The user-friendly description.
+ `html` (string, optional) - An html string containing exactly one `script` tag. Only present if `kind` is `script_tag`
+ `src` (string, optional) - The `src` attribute of the script to load. Only present if `kind` is `src`.
+ `auto_uninstall` (boolean, optional) - Whether to uninstall this script when the app associated with it is removed.
+ `load_method` (enum[string], optional) - The load method to use for the script. Values are `default`, `async`, or `defer`.
    + `default`
    + `async`
    + `defer`
+ `location` (enum[string], optional) - Where on the page to place the script. Values are `head` or `footer`.
    + `head`
    + `footer`
+ `visibility`: `storefront` (string, optional) - Which set of pages the script should load on. Currently the only possible value is `storefront`.
+ `kind`: `storefront` (enum[string], optional) - What type of script this is. Values are `src` - a `script` tag will be generated with its `src` attribute set to the value of `src`; `script_tag` - The value of `html` will be injected directly onto the page.
    + `src`
    + `script_tag`
+ `api_client_id` (string, optional) - The client id of the API user that created this script, or blank if created by other means.
+ `date_created` (string, optional) - The date on which this object was initially created.
+ `date_modified` (string, optional) - The date on which this object was last updated.


## ScriptPost (object)


### Properties
+ `name` (string, required) - The user-friendly name.
+ `description` (string, optional) - The user-friendly description.
+ `html` (string, optional) - An html string containing exactly one `script` tag. Required if `kind` is `script_tag`.
+ `src` (string, optional) - The `src` attribute of the script to load. Required if `kind` is `src`. Must be in `https` format.
+ `auto_uninstall`: `true` (boolean, optional) - Whether to uninstall this script when the app associated with it is removed.
+ `load_method`: `true` (enum[string], optional) - The load method to use for the script. Acceptable values are `default`, `async`, or `defer`.
    + `default`
    + `async`
    + `defer`
+ `location`: `true` (enum[string], optional) - Where on the page to place the script. Acceptable values are `head` or `footer`.
    + `head`
    + `footer`
+ `visibility`: `storefront` (string, optional) - Which set of pages the script should load on. Currently the only supported value is `storefront`.
+ `kind`: `storefront` (enum[string], optional) - What type of script this is. Acceptable values are `src` - a `script` tag will be generated with its `src` attribute set to the value of `src`; `script_tag` - The value of `html` (which must contain a single `script` tag) will be injected directly onto the page.
    + `src`
    + `html`


## ScriptPut (object)


### Properties
+ `name` (string, optional) - The user-friendly name.
+ `description` (string, optional) - The user-friendly description.
+ `html` (string, optional) - An html string containing exactly one `script` tag. Required if `kind` is included and equal to `script_tag`.
+ `src` (string, optional) - The `src` attribute of the script to load. Required if `kind` is included and equal to `src`. Must be in `https` format.
+ `auto_uninstall`: `true` (boolean, optional) - Whether to uninstall this script when the app associated with it is removed.
+ `load_method`: `true` (enum[string], optional) - The load method to use for the script. Acceptable values are `default`, `async`, or `defer`.
    + `default`
    + `async`
    + `defer`
+ `location`: `true` (enum[string], optional) - Where on the page to place the script. Acceptable values are `head` or `footer`.
    + `head`
    + `footer`
+ `visibility`: `storefront` (string, optional) - Which set of pages the script should load on. Currently the only supported value is `storefront`.
+ `kind`: `storefront` (enum[string], optional) - What type of script this is. Acceptable values are `src` - a `script` tag will be generated with its `src` attribute set to the value of `src`; `script_tag` - The value of `html` (which must contain a single `script` tag) will be injected directly onto the page.
    + `src`
    + `html`


## ScriptResponse (object)


### Properties
+ `data` (Script, optional) 


## ScriptsResponse (object)


### Properties
+ `data` (array[Script], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## ThemeRegion (object)


### Properties
+ `name` (string, optional) - The region name.


## ThemeRegionsResponse (object)


### Properties
+ `data` (array[ThemeRegion], optional) 
+ `meta` (object, optional) - Empty meta object; may be used later.


## ModifierCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[Modifier], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## Modifier (object)


### Properties
+ `type` (enum[string], optional) - BigCommerce API, which determines how it will display on the storefront. Acceptable values: `date`, `checkbox`, `file`, `text`, `multi_line_text`, `numbers_only_text`, `radio_buttons`, `rectangles`, `dropdown`, `product_list`, `product_list_with_images`, `swatch`. For reference, the former v2 API values are: D = date, C = checkbox, F = file, T = text, MT = multi_line_text, N = numbers_only_text, RB = radio_buttons, RT = rectangles, S = dropdown, P = product_list, PI = product_list_with_images, CS = swatch.
    + `date`
    + `checkbox`
    + `file`
    + `text`
    + `multi_line_text`
    + `numbers_only_text`
    + `radio_buttons`
    + `rectangles`
    + `dropdown`
    + `product_list`
    + `product_list_with_images`
    + `swatch`
+ `required` (boolean, optional) - Whether or not this modifer is required or not at checkout.
+ `config` (OptionConfig, optional) 
+ `option_values` (array[ModifierValue], optional) 
+ `id` (number, optional) - The unique numeric ID of the modifier; increments sequentially.
+ `product_id` (number, optional) - The unique numeric ID of the product to which the option belongs.
+ `name` (string, optional) - The unique option name. Auto-generated from the display name, a timestamp, and the product ID.
+ `display_name` (string, optional) - The name of the option shown on the storefront.


## OptionConfig (object)


### Properties
+ `default_value` (string, optional) - (date, text, multi_line_text, numbers_only_text) The default value. Shown on a date option as an ISO-8601–formatted string, or on a text option as a string.
+ `checked_by_default` (boolean, optional) - (checkbox) Flag for setting the checkbox to be checked by default.
+ `checkbox_label` (string, optional) - (checkbox) Label displayed for the checkbox option.
+ `date_limited` (boolean, optional) - (date) Flag to limit the dates allowed to be entered on a date option.
+ `date_limit_mode` (enum[string], optional) - (date) The type of limit that is allowed to be entered on a date option.
    + `earliest`
    + `range`
    + `latest`
+ `date_earliest_value` (string, optional) - (date) The earliest date allowed to be entered on the date option, as an ISO-8601 formatted string.
+ `date_latest_value` (string, optional) - (date) The latest date allowed to be entered on the date option, as an ISO-8601 formatted string.
+ `file_types_mode` (enum[string], optional) - (file) The kind of restriction on the file types that can be uploaded with a file upload option. Values: `specific` - restricts uploads to particular file types; `all` - allows all file types.
    + `specific`
    + `all`
+ `file_types_supported` (array[string], optional)

    (file) The type of files allowed to be uploaded if the `file_type_option` is set to `specific`. Values:
    
      `images` - Allows upload of image MIME types (`bmp`, `gif`, `jpg`, `jpeg`, `jpe`, `jif`, `jfif`, `jfi`, `png`, `wbmp`, `xbm`, `tiff`). `documents` - Allows upload of document MIME types (`txt`, `pdf`, `rtf`, `doc`, `docx`, `xls`, `xlsx`, `accdb`, `mdb`, `one`, `pps`, `ppsx`, `ppt`, `pptx`, `pub`, `odt`, `ods`, `odp`, `odg`, `odf`).
    
      `other` - Allows file types defined in the `file_types_other` array.

+ `file_types_other` (array[string], optional) - (file) A list of other file types allowed with the file upload option.
+ `file_max_size` (number, optional) - (file) The maximum size for a file that can be used with the file upload option.
+ `text_characters_limited` (boolean, optional) - (text, multi_line_text) Flag to validate the length of a text or multi-line text input.
+ `text_min_length` (number, optional) - (text, multi_line_text) The minimum length allowed for a text or multi-line text option.
+ `text_max_length` (number, optional) - (text, multi_line_text) The maximum length allowed for a text or multi line text option.
+ `text_lines_limited` (boolean, optional) - (multi_line_text) Flag to validate the maximum number of lines allowed on a multi-line text input.
+ `text_max_lines` (number, optional) - (multi_line_text) The maximum number of lines allowed on a multi-line text input.
+ `number_limited` (boolean, optional) - (numbers_only_text) Flag to limit the value of a number option.
+ `number_limit_mode` (enum[string], optional) - (numbers_only_text) The type of limit on values entered for a number option.
    + `lowest`
    + `highest`
    + `range`
+ `number_lowest_value` (number, optional) - (numbers_only_text) The lowest allowed value for a number option if `number_limited` is true.
+ `number_highest_value` (number, optional) - (numbers_only_text) The highest allowed value for a number option if `number_limited` is true.
+ `number_integers_only` (boolean, optional) - (numbers_only_text) Flag to limit the input on a number option to whole numbers only.
+ `product_list_adjusts_inventory` (boolean, optional) - (product_list, product_list_with_images) Flag for automatically adjusting inventory on a product included in the list.
+ `product_list_adjusts_pricing` (boolean, optional) - (product_list, product_list_with_images) Flag to add the optional product's price to the main product's price.
+ `product_list_shipping_calc` (enum[string], optional) - (product_list, product_list_with_images) How to factor the optional product's weight and package dimensions into the shipping quote. Values: `none` - don't adjust; `weight` - use shipping weight only; `package` - use weight and dimensions.
    + `none`
    + `weight`
    + `package`


## ModifierValue (object)


### Properties
+ `id` (number, optional) - The unique numeric ID of the value; increments sequentially.


## ModifierResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (Modifier, optional) 
+ `meta` (object, optional) - Empty meta object; may be used later.


## ModifierBase (object)
Common Modifier properties.



### Properties
+ `type` (enum[string], optional) - BigCommerce API, which determines how it will display on the storefront. Acceptable values: `date`, `checkbox`, `file`, `text`, `multi_line_text`, `numbers_only_text`, `radio_buttons`, `rectangles`, `dropdown`, `product_list`, `product_list_with_images`, `swatch`. For reference, the former v2 API values are: D = date, C = checkbox, F = file, T = text, MT = multi_line_text, N = numbers_only_text, RB = radio_buttons, RT = rectangles, S = dropdown, P = product_list, PI = product_list_with_images, CS = swatch.
    + `date`
    + `checkbox`
    + `file`
    + `text`
    + `multi_line_text`
    + `numbers_only_text`
    + `radio_buttons`
    + `rectangles`
    + `dropdown`
    + `product_list`
    + `product_list_with_images`
    + `swatch`
+ `required` (boolean, optional) - Whether or not this modifer is required or not at checkout.
+ `config` (OptionConfig, optional) 
+ `option_values` (array[ModifierValue], optional) 


## ModifierPost (object)
The model for a POST to create a modifier on a product.



### Properties
+ `type` (enum[string], optional) - BigCommerce API, which determines how it will display on the storefront. Acceptable values: `date`, `checkbox`, `file`, `text`, `multi_line_text`, `numbers_only_text`, `radio_buttons`, `rectangles`, `dropdown`, `product_list`, `product_list_with_images`, `swatch`. For reference, the former v2 API values are: D = date, C = checkbox, F = file, T = text, MT = multi_line_text, N = numbers_only_text, RB = radio_buttons, RT = rectangles, S = dropdown, P = product_list, PI = product_list_with_images, CS = swatch.
    + `date`
    + `checkbox`
    + `file`
    + `text`
    + `multi_line_text`
    + `numbers_only_text`
    + `radio_buttons`
    + `rectangles`
    + `dropdown`
    + `product_list`
    + `product_list_with_images`
    + `swatch`
+ `required` (boolean, optional) - Whether or not this modifer is required or not at checkout.
+ `config` (OptionConfig, optional) 
+ `option_values` (array[ModifierValue], optional) 
+ `display_name` (string, optional) - The name of the option shown on the storefront.


## ModifierValueCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[ModifierValue], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## ModifierValueResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (ModifierValue, optional) 
+ `meta` (object, optional) - Empty meta object; may be used later.


## ModifierValueBase (object)


### Properties
+ `is_default` (boolean, optional) - The flag for preselecting a value as the default on the storefront. This field is not supported for swatch options/modifiers.
+ `label` (string, optional) - The text display identifying the value on the storefront.
+ `sort_order` (number, optional) - The order in which the value will be displayed on the product page.
+ `value_data` (object, optional) - Extra data describing the value, based on the type of option or modifier with which the value is associated. The `swatch` type option can accept an array of `colors`, with up to three hexidecimal color keys; or an `image_url`, which is a full image URL path including protocol. The `product list` type option requires a `product_id`. The `checkbox` type option requires a boolean flag, called `checked_value`, to determine which value is considered to be the checked state.
+ `adjusters` (Adjusters, optional) 


## Adjusters (object)


### Properties
+ `price` (Adjuster, optional) 
+ `weight` (Adjuster, optional) 
+ `image_url` (string, optional) - The URL for an image displayed on the storefront when the modifier value is selected.
+ `purchasing_disabled` (PurchasingDisabled, optional) 


## Adjuster (object)


### Properties
+ `adjuster` (enum[string], optional) - The type of adjuster for either the price or the weight of the variant, when the modifier value is selected on the storefront.
    + `relative`
    + `percentage`
+ `adjuster_value` (number, optional) - The numeric amount by which the adjuster will change either the price or the weight of the variant, when the modifier value is selected on the storefront.


## PurchasingDisabled (object)


### Properties
+ `status` (boolean, optional) - Flag for whether the modifier value disables purchasing when selected on the storefront. This can be used for temporarily disabling a particular modifier value.
+ `message` (string, optional) - The message displayed on the storefront when the purchasing disabled status is `true`.


## ModifierValuePut (object)
The model for a PUT to update a modifier value on a product.



### Properties
+ `id` (number, optional) - The unique numeric ID of the value; increments sequentially.


## OptionCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[Option], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## Option (object)


### Properties
+ `id` (number, optional) - The unique numerical ID of the option, increments sequentially.
+ `product_id` (number, optional) - The unique numerical ID of the product to which the option belongs.
+ `display_name` (string, optional) - The name of the option shown on the storefront.
+ `type` (enum[string], optional) - The type of option, which determines how it will display on the storefront. Acceptable values: `radio_buttons`, `rectangles`, `dropdown`, `product_list`, `product_list_with_images`, `swatch`. For reference, the former v2 API values are: RB = radio_buttons, RT = rectangles, S = dropdown, P = product_list, PI = product_list_with_images, CS = swatch.
    + `radio_buttons`
    + `rectangles`
    + `dropdown`
    + `product_list`
    + `product_list_with_images`
    + `swatch`
+ `config` (OptionConfig, optional) 
+ `option_values` (array[OptionValue], optional) 
+ `name` (string, optional) - The unique option name, auto-generated from the display name, a timestamp, and the product ID.


## OptionValue (object)


### Properties
+ `is_default` (boolean, optional) - The flag for preselecting a value as the default on the storefront. This field is not supported for swatch options/modifiers.
+ `label` (string, optional) - The text display identifying the value on the storefront.
+ `sort_order` (number, optional) - The order in which the value will be displayed on the product page.
+ `value_data` (object, optional) - Extra data describing the value, based on the type of option or modifier with which the value is associated. The `swatch` type option can accept an array of `colors`, with up to three hexidecimal color keys; or an `image_url`, which is a full image URL path including protocol. The `product list` type option requires a `product_id`. The `checkbox` type option requires a boolean flag, called `checked_value`, to determine which value is considered to be the checked state.
+ `id` (number, optional) - The unique numeric ID of the value; increments sequentially.


## OptionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (Option, optional) 
+ `meta` (object, optional) - Empty meta object; may be used later.


## OptionBase (object)
Common Option properties.

### Properties
+ `id` (number, optional) - The unique numerical ID of the option, increments sequentially.
+ `product_id` (number, optional) - The unique numerical ID of the product to which the option belongs.
+ `display_name` (string, optional) - The name of the option shown on the storefront.
+ `type` (enum[string], optional) - The type of option, which determines how it will display on the storefront. Acceptable values: `radio_buttons`, `rectangles`, `dropdown`, `product_list`, `product_list_with_images`, `swatch`. For reference, the former v2 API values are: RB = radio_buttons, RT = rectangles, S = dropdown, P = product_list, PI = product_list_with_images, CS = swatch.
    + `radio_buttons`
    + `rectangles`
    + `dropdown`
    + `product_list`
    + `product_list_with_images`
    + `swatch`
+ `config` (OptionConfig, optional) 
+ `option_values` (array[OptionValue], optional) 


## CategoryTreeCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[CategoryNode], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## CategoryNode (object)
A BigCommerce category node object. Used to reflect parent <> child category relationships.



### Properties
+ `id` (number, optional) - The unique numeric ID of the category; increments sequentially.
+ `parent_id` (number, optional) - The unique numeric ID of the category's parent. This field controls where the category sits in the tree of categories that organize the catalog.
+ `name` (string, optional) - The name displayed for the category. Name is unique with respect to the category's siblings.
+ `is_visible` (boolean, optional) - Flag to determine whether the product should be displayed to customers browsing the store. If `true`, the category will be displayed. If `false`, the category will be hidden from view.
+ `url` (string, optional) - The custom URL for the category on the storefront.


## CategoryCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[Category], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## Category (object)
A BigCommerce category object.



### Properties
+ `parent_id` (number, optional) - The unique numeric ID of the category's parent. This field controls where the category sits in the tree of categories that organize the catalog.
+ `name` (string, optional) - The name displayed for the category. Name is unique with respect to the category's siblings.
+ `description` (string, optional) - The product description, which can include HTML formatting.
+ `views` (number, optional) - Number of views the category has on the storefront.
+ `sort_order` (number, optional) - Priority this category will be given when included in the menu and category pages. The lower the number, the closer to the top of the results the category will be.
+ `page_title` (string, optional) - Custom title for the category page. If not defined, the category name will be used as the meta title.
+ `search_keywords` (string, optional) - A comma-separated list of keywords that can be used to locate the category when searching the store.
+ `meta_keywords` (array[string], optional) - Custom meta keywords for the category page. If not defined, the store's default keywords will be used. Must post as an array like: ["awesome","sauce"].
+ `meta_description` (string, optional) - Custom meta description for the category page. If not defined, the store's default meta description will be used.
+ `layout_file` (string, optional) - The layout template file used to render this category.
+ `is_visible` (boolean, optional) - Flag to determine whether the product should be displayed to customers browsing the store. If `true`, the category will be displayed. If `false`, the category will be hidden from view.
+ `default_product_sort` (enum[string], optional) - Determines how the products are sorted on category page load.
    + `use_store_settings`
    + `featured`
    + `newest`
    + `best_selling`
    + `alpha_asc`
    + `alpha_desc`
    + `avg_customer_review`
    + `price_asc`
    + `price_desc`
+ `image_url` (string, optional) - Image URL used for this category on the storefront. Images can be uploaded via form file post to `/categories/{categoryId}/image`, or by providing a publicly accessible URL in this field.
+ `custom_url` (CustomUrlCategory, optional) - The custom URL for the category on the storefront.
+ `id` (number, optional) - The unique numeric ID of the category; increments sequentially.


## CustomUrlCategory (object)
The custom URL for the category on the storefront.



### Properties
+ `url` (string, optional) - Category URL on the storefront.
+ `is_customized` (boolean, optional) - Returns `true` if the URL has been changed from its default state (the auto-assigned URL that BigCommerce provides).


## CategoryResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (Category, optional) - A BigCommerce category object.
+ `meta` (object, optional) - Empty meta object; may be used later.


## CategoryBase (object)
Common Category properties.



### Properties
+ `parent_id` (number, optional) - The unique numeric ID of the category's parent. This field controls where the category sits in the tree of categories that organize the catalog.
+ `name` (string, optional) - The name displayed for the category. Name is unique with respect to the category's siblings.
+ `description` (string, optional) - The product description, which can include HTML formatting.
+ `views` (number, optional) - Number of views the category has on the storefront.
+ `sort_order` (number, optional) - Priority this category will be given when included in the menu and category pages. The lower the number, the closer to the top of the results the category will be.
+ `page_title` (string, optional) - Custom title for the category page. If not defined, the category name will be used as the meta title.
+ `search_keywords` (string, optional) - A comma-separated list of keywords that can be used to locate the category when searching the store.
+ `meta_keywords` (array[string], optional) - Custom meta keywords for the category page. If not defined, the store's default keywords will be used. Must post as an array like: ["awesome","sauce"].
+ `meta_description` (string, optional) - Custom meta description for the category page. If not defined, the store's default meta description will be used.
+ `layout_file` (string, optional) - The layout template file used to render this category.
+ `is_visible` (boolean, optional) - Flag to determine whether the product should be displayed to customers browsing the store. If `true`, the category will be displayed. If `false`, the category will be hidden from view.
+ `default_product_sort` (enum[string], optional) - Determines how the products are sorted on category page load.
    + `use_store_settings`
    + `featured`
    + `newest`
    + `best_selling`
    + `alpha_asc`
    + `alpha_desc`
    + `avg_customer_review`
    + `price_asc`
    + `price_desc`
+ `image_url` (string, optional) - Image URL used for this category on the storefront. Images can be uploaded via form file post to `/categories/{categoryId}/image`, or by providing a publicly accessible URL in this field.
+ `custom_url` (CustomUrlCategory, optional) - The custom URL for the category on the storefront.


## BrandCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[Brand], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## Brand (object)


### Properties
+ `name` (string, optional) - The name of the brand. Must be unique.
+ `page_title` (string, optional) - The title shown in the browser while viewing the brand.
+ `meta_keywords` (array[string], optional) - Comma-separated list of meta keywords to include in the HTML.
+ `meta_description` (string, optional) - A meta description to include.
+ `search_keywords` (string, optional) - A comma-separated list of keywords that can be used to locate this brand.
+ `image_url` (string, optional) - Image URL used for this category on the storefront. Images can be uploaded via form file post to `/brands/{brandId}/image`, or by providing a publicly accessible URL in this field.
+ `custom_url` (CustomUrlBrand, optional) - The custom URL for the brand on the storefront.
+ `id` (number, optional) - The unique numeric ID of the brand; increments sequentially.


## CustomUrlBrand (object)
The custom URL for the brand on the storefront.



### Properties
+ `url` (string, optional) - Brand URL on the storefront.
+ `is_customized` (boolean, optional) - Returns `true` if the URL has been changed from its default state (the auto-assigned URL that BigCommerce provides).


## BrandResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (Brand, optional) 
+ `meta` (object, optional) - Empty meta object; may be used later.


## BrandBase (object)
Common Brand properties.



### Properties
+ `name` (string, optional) - The name of the brand. Must be unique.
+ `page_title` (string, optional) - The title shown in the browser while viewing the brand.
+ `meta_keywords` (array[string], optional) - Comma-separated list of meta keywords to include in the HTML.
+ `meta_description` (string, optional) - A meta description to include.
+ `search_keywords` (string, optional) - A comma-separated list of keywords that can be used to locate this brand.
+ `image_url` (string, optional) - Image URL used for this category on the storefront. Images can be uploaded via form file post to `/brands/{brandId}/image`, or by providing a publicly accessible URL in this field.
+ `custom_url` (CustomUrlBrand, optional) - The custom URL for the brand on the storefront.


## BrandPut (object)
The model for a PUT to update brand.



### Properties
+ `name` (string, optional) - The name of the brand. Must be unique.
+ `page_title` (string, optional) - The title shown in the browser while viewing the brand.
+ `meta_keywords` (array[string], optional) - Comma-separated list of meta keywords to include in the HTML.
+ `meta_description` (string, optional) - A meta description to include.
+ `search_keywords` (string, optional) - A comma-separated list of keywords that can be used to locate this brand.
+ `image_url` (string, optional) - Image URL used for this category on the storefront. Images can be uploaded via form file post to `/brands/{brandId}/image`, or by providing a publicly accessible URL in this field.
+ `custom_url` (CustomUrlBrand, optional) - The custom URL for the brand on the storefront.
+ `id` (number, optional) - The unique numeric ID of the brand; increments sequentially.


## SubscriberCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[Subscriber], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## Subscriber (object)


### Properties
+ `id` (number, optional) - The unique numeric ID of the subscriber; increments sequentially.
+ `email` (string, optional) - The email of the subscriber. Must be unique.
+ `first_name` (string, optional) - The first name of the subscriber.
+ `last_name` (string, optional) - The last name of the subscriber.
+ `source` (string, optional) - The source of the subscriber. Values are: `storefront`, `order`, or `custom`.
+ `order_id` (number, optional) - The ID of the source order, if source was an order.
+ `date_modified` (string, optional) - The date on which the subscriber was modified.
+ `date_created` (string, optional) - The date of which the subscriber was created.


## SubscriberResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (Subscriber, optional) 
+ `meta` (object, optional) - Empty meta object; may be used later.


## SubscriberBase (object)
Common Subscriber properties.

### Properties
+ `id` (number, optional) - The unique numeric ID of the subscriber; increments sequentially.
+ `email` (string, optional) - The email of the subscriber. Must be unique.
+ `first_name` (string, optional) - The first name of the subscriber.
+ `last_name` (string, optional) - The last name of the subscriber.
+ `source` (string, optional) - The source of the subscriber. Values are: `storefront`, `order`, or `custom`.
+ `order_id` (number, optional) - The ID of the source order, if source was an order.


## VariantCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[Variant], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## Variant (object)


### Properties
+ `cost_price` (number, optional) - The cost price of the variant. Not affected by Price List prices.
+ `price` (number, optional) - This variant's base price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is `null`, the product's default price (set in the Product resource's `price` field) will be used as the base price.
+ `sale_price` (number, optional) - This variant's sale price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is null, the product's sale price (set in the Product resource's `price` field) will be used as the sale price.
+ `retail_price` (number, optional) - This variant's retail price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is null, the product's retail price (set in the Product resource's `price` field) will be used as the retail price.
+ `weight` (number, optional) - This variant's base weight on the storefront. If this value is null, the product's default weight (set in the Product resource's weight field) will be used as the base weight.
+ `width` (number, optional) - Width of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default width (set in the Product resource's `width` field) will be used as the base width.
+ `height` (number, optional) - Height of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default height (set in the Product resource's `height` field) will be used as the base height.
+ `depth` (number, optional) - Depth of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default depth (set in the Product resource's `depth` field) will be used as the base depth.
+ `is_free_shipping` (boolean, optional) - Flag used to indicate whether the variant has free shipping. If `true`, the shipping cost for the variant will be zero.
+ `fixed_cost_shipping_price` (number, optional) - A fixed shipping cost for the variant. If defined, this value will be used during checkout instead of normal shipping-cost calculation.
+ `purchasing_disabled` (boolean, optional) - If `true`, this variant will not be purchasable on the storefront.
+ `purchasing_disabled_message` (string, optional) - If `purchasing_disabled` is `true`, this message should show on the storefront when the variant is selected.
+ `image_url` (string, optional) - The image that will be displayed when this variant is selected on the storefront. When updating a SKU image, send the publicly accessible URL. Supported image formats are JPEG, PNG, and GIF. Generic product images not specific to the variant should be stored on the product.
+ `upc` (string, optional) - The UPC code used in feeds for shopping comparison sites and external channel integrations.
+ `inventory_level` (number, optional) - Inventory level for the variant, which is used when the product's inventory_tracking is set to `variant`.
+ `inventory_warning_level` (number, optional) - When the variant hits this inventory level, it is considered low stock.
+ `bin_picking_number` (string, optional) - Identifies where in a warehouse the variant is located.
+ `id` (number, optional) 
+ `product_id` (number, optional) 
+ `sku` (string, optional) 
+ `sku_id` (number, optional) - Read-only reference to v2 API's SKU ID. Null if it is a base variant.
+ `option_values` (array[OptionValueVariant], optional) - Array of option and option values IDs that make up this variant. Will be empty if the variant is the product's base variant.
+ `calculated_price` (number, optional) - The price of the variant as seen on the storefront. This price takes into account `sale_price` and any price adjustment rules that are applicable to this variant.


## OptionValueVariant (object)


### Properties
+ `option_display_name` (string, optional) - The name of the option.
+ `label` (string, optional) - The label of the option value.
+ `id` (number, optional) 
+ `option_id` (number, optional) 


## VariantResponse (object)
Successful response.



### Properties
+ `data` (Variant, optional) 
+ `meta` (object, optional) - Empty meta object; may be used later.


## VariantBase (object)
Common Variant properties.

### Properties
+ `cost_price` (number, optional) - The cost price of the variant. Not affected by Price List prices.
+ `price` (number, optional) - This variant's base price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is `null`, the product's default price (set in the Product resource's `price` field) will be used as the base price.
+ `sale_price` (number, optional) - This variant's sale price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is null, the product's sale price (set in the Product resource's `price` field) will be used as the sale price.
+ `retail_price` (number, optional) - This variant's retail price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is null, the product's retail price (set in the Product resource's `price` field) will be used as the retail price.
+ `weight` (number, optional) - This variant's base weight on the storefront. If this value is null, the product's default weight (set in the Product resource's weight field) will be used as the base weight.
+ `width` (number, optional) - Width of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default width (set in the Product resource's `width` field) will be used as the base width.
+ `height` (number, optional) - Height of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default height (set in the Product resource's `height` field) will be used as the base height.
+ `depth` (number, optional) - Depth of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default depth (set in the Product resource's `depth` field) will be used as the base depth.
+ `is_free_shipping` (boolean, optional) - Flag used to indicate whether the variant has free shipping. If `true`, the shipping cost for the variant will be zero.
+ `fixed_cost_shipping_price` (number, optional) - A fixed shipping cost for the variant. If defined, this value will be used during checkout instead of normal shipping-cost calculation.
+ `purchasing_disabled` (boolean, optional) - If `true`, this variant will not be purchasable on the storefront.
+ `purchasing_disabled_message` (string, optional) - If `purchasing_disabled` is `true`, this message should show on the storefront when the variant is selected.
+ `image_url` (string, optional) - The image that will be displayed when this variant is selected on the storefront. When updating a SKU image, send the publicly accessible URL. Supported image formats are JPEG, PNG, and GIF. Generic product images not specific to the variant should be stored on the product.
+ `upc` (string, optional) - The UPC code used in feeds for shopping comparison sites and external channel integrations.
+ `inventory_level` (number, optional) - Inventory level for the variant, which is used when the product's inventory_tracking is set to `variant`.
+ `inventory_warning_level` (number, optional) - When the variant hits this inventory level, it is considered low stock.
+ `bin_picking_number` (string, optional) - Identifies where in a warehouse the variant is located.


## VariantPost (object)
The model for a POST to create variants on a product.



### Properties
+ `cost_price` (number, optional) - The cost price of the variant. Not affected by Price List prices.
+ `price` (number, optional) - This variant's base price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is `null`, the product's default price (set in the Product resource's `price` field) will be used as the base price.
+ `sale_price` (number, optional) - This variant's sale price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is null, the product's sale price (set in the Product resource's `price` field) will be used as the sale price.
+ `retail_price` (number, optional) - This variant's retail price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is null, the product's retail price (set in the Product resource's `price` field) will be used as the retail price.
+ `weight` (number, optional) - This variant's base weight on the storefront. If this value is null, the product's default weight (set in the Product resource's weight field) will be used as the base weight.
+ `width` (number, optional) - Width of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default width (set in the Product resource's `width` field) will be used as the base width.
+ `height` (number, optional) - Height of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default height (set in the Product resource's `height` field) will be used as the base height.
+ `depth` (number, optional) - Depth of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default depth (set in the Product resource's `depth` field) will be used as the base depth.
+ `is_free_shipping` (boolean, optional) - Flag used to indicate whether the variant has free shipping. If `true`, the shipping cost for the variant will be zero.
+ `fixed_cost_shipping_price` (number, optional) - A fixed shipping cost for the variant. If defined, this value will be used during checkout instead of normal shipping-cost calculation.
+ `purchasing_disabled` (boolean, optional) - If `true`, this variant will not be purchasable on the storefront.
+ `purchasing_disabled_message` (string, optional) - If `purchasing_disabled` is `true`, this message should show on the storefront when the variant is selected.
+ `image_url` (string, optional) - The image that will be displayed when this variant is selected on the storefront. When updating a SKU image, send the publicly accessible URL. Supported image formats are JPEG, PNG, and GIF. Generic product images not specific to the variant should be stored on the product.
+ `upc` (string, optional) - The UPC code used in feeds for shopping comparison sites and external channel integrations.
+ `inventory_level` (number, optional) - Inventory level for the variant, which is used when the product's inventory_tracking is set to `variant`.
+ `inventory_warning_level` (number, optional) - When the variant hits this inventory level, it is considered low stock.
+ `bin_picking_number` (string, optional) - Identifies where in a warehouse the variant is located.
+ `product_id` (number, optional) 
+ `sku` (string, optional) 
+ `option_values` (array[OptionValueVariantPost], optional) - Array of option and option values IDs that make up this variant. Will be empty if the variant is the product's base variant.


## OptionValueVariantPost (object)
The model for a POST to create option values on a variant.



### Properties
+ `id` (number, optional) 
+ `option_id` (number, optional) 


## VariantPut (object)
The model for a PUT to update variants on a product.



### Properties
+ `cost_price` (number, optional) - The cost price of the variant. Not affected by Price List prices.
+ `price` (number, optional) - This variant's base price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is `null`, the product's default price (set in the Product resource's `price` field) will be used as the base price.
+ `sale_price` (number, optional) - This variant's sale price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is null, the product's sale price (set in the Product resource's `price` field) will be used as the sale price.
+ `retail_price` (number, optional) - This variant's retail price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is null, the product's retail price (set in the Product resource's `price` field) will be used as the retail price.
+ `weight` (number, optional) - This variant's base weight on the storefront. If this value is null, the product's default weight (set in the Product resource's weight field) will be used as the base weight.
+ `width` (number, optional) - Width of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default width (set in the Product resource's `width` field) will be used as the base width.
+ `height` (number, optional) - Height of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default height (set in the Product resource's `height` field) will be used as the base height.
+ `depth` (number, optional) - Depth of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default depth (set in the Product resource's `depth` field) will be used as the base depth.
+ `is_free_shipping` (boolean, optional) - Flag used to indicate whether the variant has free shipping. If `true`, the shipping cost for the variant will be zero.
+ `fixed_cost_shipping_price` (number, optional) - A fixed shipping cost for the variant. If defined, this value will be used during checkout instead of normal shipping-cost calculation.
+ `purchasing_disabled` (boolean, optional) - If `true`, this variant will not be purchasable on the storefront.
+ `purchasing_disabled_message` (string, optional) - If `purchasing_disabled` is `true`, this message should show on the storefront when the variant is selected.
+ `image_url` (string, optional) - The image that will be displayed when this variant is selected on the storefront. When updating a SKU image, send the publicly accessible URL. Supported image formats are JPEG, PNG, and GIF. Generic product images not specific to the variant should be stored on the product.
+ `upc` (string, optional) - The UPC code used in feeds for shopping comparison sites and external channel integrations.
+ `inventory_level` (number, optional) - Inventory level for the variant, which is used when the product's inventory_tracking is set to `variant`.
+ `inventory_warning_level` (number, optional) - When the variant hits this inventory level, it is considered low stock.
+ `bin_picking_number` (string, optional) - Identifies where in a warehouse the variant is located.
+ `id` (number, optional) 


## VariantProductPost (object)
The model for a POST to create variants on a product.



### Properties
+ `cost_price` (number, optional) - The cost price of the variant. Not affected by Price List prices.
+ `price` (number, optional) - This variant's base price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is `null`, the product's default price (set in the Product resource's `price` field) will be used as the base price.
+ `sale_price` (number, optional) - This variant's sale price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is null, the product's sale price (set in the Product resource's `price` field) will be used as the sale price.
+ `retail_price` (number, optional) - This variant's retail price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is null, the product's retail price (set in the Product resource's `price` field) will be used as the retail price.
+ `weight` (number, optional) - This variant's base weight on the storefront. If this value is null, the product's default weight (set in the Product resource's weight field) will be used as the base weight.
+ `width` (number, optional) - Width of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default width (set in the Product resource's `width` field) will be used as the base width.
+ `height` (number, optional) - Height of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default height (set in the Product resource's `height` field) will be used as the base height.
+ `depth` (number, optional) - Depth of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default depth (set in the Product resource's `depth` field) will be used as the base depth.
+ `is_free_shipping` (boolean, optional) - Flag used to indicate whether the variant has free shipping. If `true`, the shipping cost for the variant will be zero.
+ `fixed_cost_shipping_price` (number, optional) - A fixed shipping cost for the variant. If defined, this value will be used during checkout instead of normal shipping-cost calculation.
+ `purchasing_disabled` (boolean, optional) - If `true`, this variant will not be purchasable on the storefront.
+ `purchasing_disabled_message` (string, optional) - If `purchasing_disabled` is `true`, this message should show on the storefront when the variant is selected.
+ `image_url` (string, optional) - The image that will be displayed when this variant is selected on the storefront. When updating a SKU image, send the publicly accessible URL. Supported image formats are JPEG, PNG, and GIF. Generic product images not specific to the variant should be stored on the product.
+ `upc` (string, optional) - The UPC code used in feeds for shopping comparison sites and external channel integrations.
+ `inventory_level` (number, optional) - Inventory level for the variant, which is used when the product's inventory_tracking is set to `variant`.
+ `inventory_warning_level` (number, optional) - When the variant hits this inventory level, it is considered low stock.
+ `bin_picking_number` (string, optional) - Identifies where in a warehouse the variant is located.
+ `product_id` (number, optional) 
+ `sku` (string, optional) 
+ `option_values` (array[OptionValueProductBase], optional) 


## OptionValueProductBase (object)
Common OptionValueProduct properties.

### Properties
+ `option_display_name` (string, optional) - The name of the option.
+ `label` (string, optional) - The label of the option value.


## VariantProductPut (object)
The model for a PUT to update variants on a product.


### Properties
+ `cost_price` (number, optional) - The cost price of the variant. Not affected by Price List prices.
+ `price` (number, optional) - This variant's base price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is `null`, the product's default price (set in the Product resource's `price` field) will be used as the base price.
+ `sale_price` (number, optional) - This variant's sale price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is null, the product's sale price (set in the Product resource's `price` field) will be used as the sale price.
+ `retail_price` (number, optional) - This variant's retail price on the storefront. If a Price List ID is used, the Price List value will be used. If a Price List ID is not used, and this value is null, the product's retail price (set in the Product resource's `price` field) will be used as the retail price.
+ `weight` (number, optional) - This variant's base weight on the storefront. If this value is null, the product's default weight (set in the Product resource's weight field) will be used as the base weight.
+ `width` (number, optional) - Width of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default width (set in the Product resource's `width` field) will be used as the base width.
+ `height` (number, optional) - Height of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default height (set in the Product resource's `height` field) will be used as the base height.
+ `depth` (number, optional) - Depth of the variant, which can be used when calculating shipping costs. If this value is `null`, the product's default depth (set in the Product resource's `depth` field) will be used as the base depth.
+ `is_free_shipping` (boolean, optional) - Flag used to indicate whether the variant has free shipping. If `true`, the shipping cost for the variant will be zero.
+ `fixed_cost_shipping_price` (number, optional) - A fixed shipping cost for the variant. If defined, this value will be used during checkout instead of normal shipping-cost calculation.
+ `purchasing_disabled` (boolean, optional) - If `true`, this variant will not be purchasable on the storefront.
+ `purchasing_disabled_message` (string, optional) - If `purchasing_disabled` is `true`, this message should show on the storefront when the variant is selected.
+ `image_url` (string, optional) - The image that will be displayed when this variant is selected on the storefront. When updating a SKU image, send the publicly accessible URL. Supported image formats are JPEG, PNG, and GIF. Generic product images not specific to the variant should be stored on the product.
+ `upc` (string, optional) - The UPC code used in feeds for shopping comparison sites and external channel integrations.
+ `inventory_level` (number, optional) - Inventory level for the variant, which is used when the product's inventory_tracking is set to `variant`.
+ `inventory_warning_level` (number, optional) - When the variant hits this inventory level, it is considered low stock.
+ `bin_picking_number` (string, optional) - Identifies where in a warehouse the variant is located.
+ `product_id` (number, optional) 
+ `sku` (string, optional) 


## OptionValueCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[OptionValue], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## OptionValueResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (OptionValue, optional) 
+ `meta` (object, optional) - Empty meta object; may be used later.


## OptionValueBase (object)
Common OptionValue properties.

### Properties
+ `is_default` (boolean, optional) - The flag for preselecting a value as the default on the storefront. This field is not supported for swatch options/modifiers.
+ `label` (string, optional) - The text display identifying the value on the storefront.
+ `sort_order` (number, optional) - The order in which the value will be displayed on the product page.
+ `value_data` (object, optional) - Extra data describing the value, based on the type of option or modifier with which the value is associated. The `swatch` type option can accept an array of `colors`, with up to three hexidecimal color keys; or an `image_url`, which is a full image URL path including protocol. The `product list` type option requires a `product_id`. The `checkbox` type option requires a boolean flag, called `checked_value`, to determine which value is considered to be the checked state.


## OptionValuePut (object)
The model for a PUT to update option values on a product.



### Properties
+ `is_default` (boolean, optional) - The flag for preselecting a value as the default on the storefront. This field is not supported for swatch options/modifiers.
+ `label` (string, optional) - The text display identifying the value on the storefront.
+ `sort_order` (number, optional) - The order in which the value will be displayed on the product page.
+ `value_data` (object, optional) - Extra data describing the value, based on the type of option or modifier with which the value is associated. The `swatch` type option can accept an array of `colors`, with up to three hexidecimal color keys; or an `image_url`, which is a full image URL path including protocol. The `product list` type option requires a `product_id`. The `checkbox` type option requires a boolean flag, called `checked_value`, to determine which value is considered to be the checked state.
+ `id` (number, optional) - The unique numeric ID of the value; increments sequentially.


## ProductImageCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[ProductImage], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## ProductImage (object)
The full ProductImage model.



### Properties
+ `is_thumbnail` (boolean, optional) - Flag for identifying whether the image is used as the product's thumbnail.
+ `sort_order` (number, optional) - The order in which the image will be displayed on the product page. Higher integers give the image a lower priority. When updating, if the image is given a lower priority, all images with a `sort_order` the same as or greater than the image's new `sort_order` value will have their `sort_order`s reordered.
+ `description` (string, optional) - The description for the image.
+ `id` (number, optional) - The unique numeric ID of the image; increments sequentially.
+ `product_id` (number, optional) - The unique numeric identifier for the product with which the image is associated.
+ `image_file` (string, optional) - The local path to the original image file uploaded to BigCommerce.
+ `url_zoom` (string, optional) - The zoom URL for this image. By default, this is used as the zoom image on product pages when zoom images are enabled.
+ `url_standard` (string, optional) - The standard URL for this image. By default, this is used for product-page images.
+ `url_thumbnail` (string, optional) - The thumbnail URL for this image. By default, this is the image size used on the category page and in side panels.
+ `url_tiny` (string, optional) - The tiny URL for this image. By default, this is the image size used for thumbnails beneath the product image on a product page.
+ `date_modified` (string, optional) - The date on which the product image was modified.


## ProductImageResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (ProductImage, optional) - The full ProductImage model.
+ `meta` (object, optional) - Empty meta object; may be used later.


## ProductImageBase (object)
Common ProductImage properties.



### Properties
+ `is_thumbnail` (boolean, optional) - Flag for identifying whether the image is used as the product's thumbnail.
+ `sort_order` (number, optional) - The order in which the image will be displayed on the product page. Higher integers give the image a lower priority. When updating, if the image is given a lower priority, all images with a `sort_order` the same as or greater than the image's new `sort_order` value will have their `sort_order`s reordered.
+ `description` (string, optional) - The description for the image.


## ProductImagePost (object)
The model for a POST to create an image on a product.



### Properties
+ `is_thumbnail` (boolean, optional) - Flag for identifying whether the image is used as the product's thumbnail.
+ `sort_order` (number, optional) - The order in which the image will be displayed on the product page. Higher integers give the image a lower priority. When updating, if the image is given a lower priority, all images with a `sort_order` the same as or greater than the image's new `sort_order` value will have their `sort_order`s reordered.
+ `description` (string, optional) - The description for the image.
+ `image_url` (string, optional) - Must be a fully qualified URL path, including protocol.
+ `image_file` (string, optional) - Must be sent as a multipart/form-data field in the request body.


## ProductVideoCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[ProductVideo], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## ProductVideo (object)
A product video model.



### Properties
+ `title` (string, optional) - The title for the video. If left blank, this will be filled in according to data on a host site.
+ `description` (string, optional) - The description for the video. If left blank, this will be filled in according to data on a host site.
+ `sort_order` (number, optional) - The order in which the video will be displayed on the product page. Higher integers give the video a lower priority. When updating, if the video is given a lower priority, all videos with a `sort_order` the same as or greater than the video's new `sort_order` value will have their `sort_order`s reordered.
+ `type`: `youtube` (string, optional) - The video type (a short name of a host site).
+ `id` (number, optional) - The unique numeric ID of the product video; increments sequentially.
+ `video_id` (string, optional) - The ID of the video on a host site.
+ `product_id` (number, optional) - The unique numeric identifier for the product with which the image is associated.
+ `length` (string, optional) - Length of the video. This will be filled in according to data on a host site.


## ProductVideoResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (ProductVideo, optional) - A product video model.
+ `meta` (object, optional) - Empty meta object; may be used later.


## ProductVideoBase (object)
Common ProductVideo properties.

### Properties
+ `title` (string, optional) - The title for the video. If left blank, this will be filled in according to data on a host site.
+ `description` (string, optional) - The description for the video. If left blank, this will be filled in according to data on a host site.
+ `sort_order` (number, optional) - The order in which the video will be displayed on the product page. Higher integers give the video a lower priority. When updating, if the video is given a lower priority, all videos with a `sort_order` the same as or greater than the video's new `sort_order` value will have their `sort_order`s reordered.
+ `type`: `youtube` (string, optional) - The video type (a short name of a host site).


## ProductVideoPost (object)
The model for a POST to create a video on a product.



### Properties
+ `title` (string, optional) - The title for the video. If left blank, this will be filled in according to data on a host site.
+ `description` (string, optional) - The description for the video. If left blank, this will be filled in according to data on a host site.
+ `sort_order` (number, optional) - The order in which the video will be displayed on the product page. Higher integers give the video a lower priority. When updating, if the video is given a lower priority, all videos with a `sort_order` the same as or greater than the video's new `sort_order` value will have their `sort_order`s reordered.
+ `type`: `youtube` (string, optional) - The video type (a short name of a host site).
+ `video_id` (string, optional) - The ID of the video on a host site.


## ProductVideoPut (object)
The model for a PUT to update a video on a product.



### Properties
+ `title` (string, optional) - The title for the video. If left blank, this will be filled in according to data on a host site.
+ `description` (string, optional) - The description for the video. If left blank, this will be filled in according to data on a host site.
+ `sort_order` (number, optional) - The order in which the video will be displayed on the product page. Higher integers give the video a lower priority. When updating, if the video is given a lower priority, all videos with a `sort_order` the same as or greater than the video's new `sort_order` value will have their `sort_order`s reordered.
+ `type`: `youtube` (string, optional) - The video type (a short name of a host site).
+ `id` (number, optional) - The unique numeric ID of the product video; increments sequentially.


## ProductReviewCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[ProductReview], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## ProductReview (object)
A product review model.



### Properties
+ `title` (string, optional) - The title for the product review.
+ `text` (string, optional) - The text for the product review.
+ `status` (string, optional) - The status of the product review. Must be one of `approved`, `disapproved` or `pending`.
+ `rating` (number, optional) - The rating of the product review. Must be one of 0, 1, 2, 3, 4, 5.
+ `email` (string, optional) - The email of the reviewer. Must be a valid email, or an empty string.
+ `name` (string, optional) - The name of the reviewer.
+ `date_reviewed` (string, optional) - Date the product was reviewed.
+ `id` (number, optional) - The unique numeric ID of the product review; increments sequentially.
+ `product_id` (number, optional) - The unique numeric identifier for the product with which the review is associated.
+ `date_created` (string, optional) - Date the product review was created.
+ `date_modified` (string, optional) - Date the product review was modified.


## ProductReviewResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (ProductReview, optional) - A product review model.
+ `meta` (object, optional) - Empty meta object; may be used later.


## ProductReviewBase (object)
Common ProductReview properties.

### Properties
+ `title` (string, optional) - The title for the product review.
+ `text` (string, optional) - The text for the product review.
+ `status` (string, optional) - The status of the product review. Must be one of `approved`, `disapproved` or `pending`.
+ `rating` (number, optional) - The rating of the product review. Must be one of 0, 1, 2, 3, 4, 5.
+ `email` (string, optional) - The email of the reviewer. Must be a valid email, or an empty string.
+ `name` (string, optional) - The name of the reviewer.
+ `date_reviewed` (string, optional) - Date the product was reviewed.


## ImageResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (ResourceImage, optional) - An object containing a publicly accessible image URL, or a form post that contains an image file.
+ `meta` (object, optional) - Empty meta object; may be used later.


## ResourceImage (object)
An object containing a publicly accessible image URL, or a form post that contains an image file.



### Properties
+ `image_url` (string, optional) - A public URL for a GIF, JPEG, or PNG image.


## ProductCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[Product], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## Product (object)
A BigCommerce Product object describes a single purchasable unit or a collection of purchasable units.



### Properties
+ `name` (string, optional) - The product name.
+ `type` (enum[string], optional) - The product type. One of: `physical` - a physical stock unit, `digital` - a digital download.
    + `physical`
    + `digital`
+ `sku` (string, optional) - User defined product code/stock keeping unit (SKU).
+ `description` (string, optional) - The product description, which can include HTML formatting.
+ `weight` (number, optional) - Weight of the product, which can be used when calculating shipping costs.
+ `width` (number, optional) - Width of the product, which can be used when calculating shipping costs.
+ `depth` (number, optional) - Depth of the product, which can be used when calculating shipping costs.
+ `height` (number, optional) - Height of the product, which can be used when calculating shipping costs.
+ `price` (number, optional) - The price of the product. The price should include or exclude tax, based on the store settings.
+ `cost_price` (number, optional) - The cost price of the product. Stored for reference only; it is not used or displayed anywhere on the store.
+ `retail_price` (number, optional) - The retail cost of the product. If entered, the retail cost price will be shown on the product page.
+ `sale_price` (number, optional) - If entered, the sale price will be used instead of value in the price field when calculating the product's cost.
+ `tax_class_id` (number, optional) - The ID of the tax class applied to the product. (NOTE: Value ignored if automatic tax is enabled.)
+ `product_tax_code` (string, optional) - Accepts AvaTax System Tax Codes, which identify products and services that fall into special sales-tax categories. By using these codes, merchants who subscribe to BigCommerce's Avalara Premium integration can calculate sales taxes more accurately. Stores without Avalara Premium will ignore the code when calculating sales tax. Do not pass more than one code. The codes are case-sensitive. For details, please see Avalara's documentation.
+ `categories` (array[number], optional) - An array of IDs for the categories to which this product belongs. When updating a product, if an array of categories is supplied, all product categories will be overwritten. Does not accept more than 1,000 ID values.
+ `brand_id` (number, optional) - The ID associated with the product's brand.
+ `inventory_level` (number, optional) - Current inventory level of the product. Simple inventory tracking must be enabled (See the `inventory_tracking` field) for this to take any effect.
+ `inventory_warning_level` (number, optional) - Inventory warning level for the product. When the product's inventory level drops below the warning level, the store owner will be informed. Simple inventory tracking must be enabled (see the `inventory_tracking` field) for this to take any effect.
+ `inventory_tracking` (enum[string], optional) - The type of inventory tracking for the product. Values are: `none` - inventory levels will not be tracked; `product` - inventory levels will be tracked using the `inventory_level` and `inventory_warning_level` fields; `variant` - inventory levels will be tracked based on variants, which maintain their own warning levels and inventory levels.
    + `none`
    + `product`
    + `variant`
+ `fixed_cost_shipping_price` (number, optional) - A fixed shipping cost for the product. If defined, this value will be used during checkout instead of normal shipping-cost calculation.
+ `is_free_shipping` (boolean, optional) - Flag used to indicate whether the product has free shipping. If `true`, the shipping cost for the product will be zero.
+ `is_visible` (boolean, optional) - Flag to determine whether the product should be displayed to customers browsing the store. If `true`, the product will be displayed. If `false`, the product will be hidden from view.
+ `is_featured` (boolean, optional) - Flag to determine whether the product should be included in the `featured products` panel when viewing the store.
+ `related_products` (array[number], optional) - An array of IDs for the related products.
+ `warranty` (string, optional) - Warranty information displayed on the product page. Can include HTML formatting.
+ `bin_picking_number` (string, optional) - The BIN picking number for the product.
+ `layout_file` (string, optional) - The layout template file used to render this product.
+ `upc` (string, optional) - The product UPC code, which is used in feeds for shopping comparison sites and external channel integrations.
+ `search_keywords` (string, optional) - A comma-separated list of keywords that can be used to locate the product when searching the store.
+ `availability` (enum[string], optional) - Availability of the product. Availability options are: `available` - the product can be purchased on the storefront; `disabled` - the product is listed in the storefront, but cannot be purchased; `preorder` - the product is listed for pre-orders.
    + `available`
    + `disabled`
    + `preorder`
+ `availability_description` (string, optional) - Availability text displayed on the checkout page, under the product title. Tells the customer how long it will normally take to ship this product, such as: 'Usually ships in 24 hours.'
+ `gift_wrapping_options_type` (enum[string], optional) - Type of gift-wrapping options. Values: `any` - allow any gift-wrapping options in the store; `none` - disallow gift-wrapping on the product; `list` – provide a list of IDs in the `gift_wrapping_options_list` field.
    + `any`
    + `none`
    + `list`
+ `gift_wrapping_options_list` (array[number], optional) - A list of gift-wrapping option IDs.
+ `sort_order` (number, optional) - Priority to give this product when included in product lists on category pages and in search results. Lower integers will place the product closer to the top of the results.
+ `condition` (enum[string], optional) - The product condition. Will be shown on the product page if the `is_condition_shown` field's value is `true`. Possible values: `New`, `Used`, `Refurbished`.
    + `New`
    + `Used`
    + `Refurbished`
+ `is_condition_shown` (boolean, optional) - Flag used to determine whether the product condition is shown to the customer on the product page.
+ `order_quantity_minimum` (number, optional) - The minimum quantity an order must contain, to be eligible to purchase this product.
+ `order_quantity_maximum` (number, optional) - The maximum quantity an order can contain when purchasing the product.
+ `page_title` (string, optional) - Custom title for the product page. If not defined, the product name will be used as the meta title.
+ `meta_keywords` (array[string], optional) - Custom meta keywords for the product page. If not defined, the store's default keywords will be used.
+ `meta_description` (string, optional) - Custom meta description for the product page. If not defined, the store's default meta description will be used.
+ `view_count` (number, optional) - The number of times the product has been viewed.
+ `preorder_release_date` (string, optional) - Pre-order release date. See the `availability` field for details on setting a product's availability to accept pre-orders.
+ `preorder_message` (string, optional) - Custom expected-date message to display on the product page. If undefined, the message defaults to the storewide setting. Can contain the `%%DATE%%` placeholder, which will be substituted for the release date.
+ `is_preorder_only` (boolean, optional) - If set to `false`, the product will not change its availability from `preorder` to `available` on the release date. Otherwise, on the release date the product's availability/status will change to `available`.
+ `is_price_hidden` (boolean, optional) - False by default, indicating that this product's price should be shown on the product page. If set to `true`, the price is hidden. (NOTE: To successfully set `is_price_hidden` to `true`, the `availability` value must be `disabled`.)
+ `price_hidden_label` (string, optional) - By default, an empty string. If `is_price_hidden` is `true`, the value of `price_hidden_label` is displayed instead of the price. (NOTE: To successfully set a non-empty string value with `is_price_hidden` set to `true`, the `availability` value must be `disabled`.)
+ `custom_url` (CustomUrlProduct, optional) - The custom URL for the product on the storefront.
+ `open_graph_type` (enum[string], optional) - Type of product, defaults to `product`.
    + `product`
    + `album`
    + `book`
    + `drink`
    + `food`
    + `game`
    + `movie`
    + `song`
    + `tv_show`
+ `open_graph_title` (string, optional) - Title of the product, if not specified the product name will be used instead.
+ `open_graph_description` (string, optional) - Description to use for the product, if not specified then the meta_description will be used instead.
+ `open_graph_use_meta_description` (boolean, optional) - Flag to determine if product description or open graph description is used.
+ `open_graph_use_product_name` (boolean, optional) - Flag to determine if product name or open graph name is used.
+ `open_graph_use_image` (boolean, optional) - Flag to determine if product image or open graph image is used.
+ `id` (number, optional) - The unique numeric ID of the product; increments sequentially.
+ `calculated_price` (number, optional) - The price of the product as seen on the storefront. It will be equal to the `sale_price`, if set, and the `price` if there is not a `sale_price`.
+ `reviews_rating_sum` (number, optional) - The total rating for the product.
+ `reviews_count` (number, optional) - The number of times the product has been rated.
+ `total_sold` (number, optional) - The total quantity of this product sold.
+ `custom_fields` (array[CustomField], optional) 
+ `bulk_pricing_rules` (array[BulkPricingRule], optional) 
+ `date_created` (string, optional) - The date on which the product was created.
+ `date_modified` (string, optional) - The date on which the product was modified.
+ `images` (array[ProductImage], optional) 
+ `videos` (array[ProductVideo], optional) 
+ `variants` (array[Variant], optional) 
+ `base_variant_id` (number, optional) - The unique identifier of the base variant associated with a simple product. This value is null for complex products.


## CustomUrlProduct (object)
The custom URL for the product on the storefront.



### Properties
+ `url` (string, optional) - Product URL on the storefront.
+ `is_customized` (boolean, optional) - Returns `true` if the URL has been changed from its default state (the auto-assigned URL that BigCommerce provides).


## CustomField (object)
Gets custom fields associated with a product. These allow you to specify additional information that will appear on the product's page, such as a book's ISBN or a DVD's release date.



### Properties
+ `name` (string, optional) - The name of the field, shown on the storefront, orders, etc.
+ `value` (string, optional) - The name of the field, shown on the storefront, orders, etc.
+ `id` (number, optional) - The unique numeric ID of the custom field; increments sequentially.


## BulkPricingRule (object)
Rules that offer price discounts based on quantity breaks.



### Properties
+ `quantity_min` (number, optional) - The minimum inclusive quantity of a product to satisfy this rule. Must be greater than or equal to zero.
+ `quantity_max` (number, optional) - The maximum inclusive quantity of a product to satisfy this rule. Must be greater than the `quantity_min` value – unless this field has a value of 0 (zero), in which case there will be no maximum bound for this rule.
+ `type` (enum[string], optional) - The type of adjustment that is made. Values: `price` - the adjustment amount per product; `percent` - the adjustment as a percentage of the original price; `fixed` - the adjusted absolute price of the product.
    + `price`
    + `percent`
    + `fixed`
+ `amount` (number, optional) - The value of the adjustment by the bulk pricing rule.
+ `id` (number, optional) - The ID of the bulk pricing rule.


## ProductResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (Product, optional) - A BigCommerce Product object describes a single purchasable unit or a collection of purchasable units.
+ `meta` (object, optional) - Empty meta object; may be used later.


## ProductBase (object)
Common Product properties.

### Properties
+ `name` (string, optional) - The product name.
+ `type` (enum[string], optional) - The product type. One of: `physical` - a physical stock unit, `digital` - a digital download.
    + `physical`
    + `digital`
+ `sku` (string, optional) - User defined product code/stock keeping unit (SKU).
+ `description` (string, optional) - The product description, which can include HTML formatting.
+ `weight` (number, optional) - Weight of the product, which can be used when calculating shipping costs.
+ `width` (number, optional) - Width of the product, which can be used when calculating shipping costs.
+ `depth` (number, optional) - Depth of the product, which can be used when calculating shipping costs.
+ `height` (number, optional) - Height of the product, which can be used when calculating shipping costs.
+ `price` (number, optional) - The price of the product. The price should include or exclude tax, based on the store settings.
+ `cost_price` (number, optional) - The cost price of the product. Stored for reference only; it is not used or displayed anywhere on the store.
+ `retail_price` (number, optional) - The retail cost of the product. If entered, the retail cost price will be shown on the product page.
+ `sale_price` (number, optional) - If entered, the sale price will be used instead of value in the price field when calculating the product's cost.
+ `tax_class_id` (number, optional) - The ID of the tax class applied to the product. (NOTE: Value ignored if automatic tax is enabled.)
+ `product_tax_code` (string, optional) - Accepts AvaTax System Tax Codes, which identify products and services that fall into special sales-tax categories. By using these codes, merchants who subscribe to BigCommerce's Avalara Premium integration can calculate sales taxes more accurately. Stores without Avalara Premium will ignore the code when calculating sales tax. Do not pass more than one code. The codes are case-sensitive. For details, please see Avalara's documentation.
+ `categories` (array[number], optional) - An array of IDs for the categories to which this product belongs. When updating a product, if an array of categories is supplied, all product categories will be overwritten. Does not accept more than 1,000 ID values.
+ `brand_id` (number, optional) - The ID associated with the product's brand.
+ `inventory_level` (number, optional) - Current inventory level of the product. Simple inventory tracking must be enabled (See the `inventory_tracking` field) for this to take any effect.
+ `inventory_warning_level` (number, optional) - Inventory warning level for the product. When the product's inventory level drops below the warning level, the store owner will be informed. Simple inventory tracking must be enabled (see the `inventory_tracking` field) for this to take any effect.
+ `inventory_tracking` (enum[string], optional) - The type of inventory tracking for the product. Values are: `none` - inventory levels will not be tracked; `product` - inventory levels will be tracked using the `inventory_level` and `inventory_warning_level` fields; `variant` - inventory levels will be tracked based on variants, which maintain their own warning levels and inventory levels.
    + `none`
    + `product`
    + `variant`
+ `fixed_cost_shipping_price` (number, optional) - A fixed shipping cost for the product. If defined, this value will be used during checkout instead of normal shipping-cost calculation.
+ `is_free_shipping` (boolean, optional) - Flag used to indicate whether the product has free shipping. If `true`, the shipping cost for the product will be zero.
+ `is_visible` (boolean, optional) - Flag to determine whether the product should be displayed to customers browsing the store. If `true`, the product will be displayed. If `false`, the product will be hidden from view.
+ `is_featured` (boolean, optional) - Flag to determine whether the product should be included in the `featured products` panel when viewing the store.
+ `related_products` (array[number], optional) - An array of IDs for the related products.
+ `warranty` (string, optional) - Warranty information displayed on the product page. Can include HTML formatting.
+ `bin_picking_number` (string, optional) - The BIN picking number for the product.
+ `layout_file` (string, optional) - The layout template file used to render this product.
+ `upc` (string, optional) - The product UPC code, which is used in feeds for shopping comparison sites and external channel integrations.
+ `search_keywords` (string, optional) - A comma-separated list of keywords that can be used to locate the product when searching the store.
+ `availability` (enum[string], optional) - Availability of the product. Availability options are: `available` - the product can be purchased on the storefront; `disabled` - the product is listed in the storefront, but cannot be purchased; `preorder` - the product is listed for pre-orders.
    + `available`
    + `disabled`
    + `preorder`
+ `availability_description` (string, optional) - Availability text displayed on the checkout page, under the product title. Tells the customer how long it will normally take to ship this product, such as: 'Usually ships in 24 hours.'
+ `gift_wrapping_options_type` (enum[string], optional) - Type of gift-wrapping options. Values: `any` - allow any gift-wrapping options in the store; `none` - disallow gift-wrapping on the product; `list` – provide a list of IDs in the `gift_wrapping_options_list` field.
    + `any`
    + `none`
    + `list`
+ `gift_wrapping_options_list` (array[number], optional) - A list of gift-wrapping option IDs.
+ `sort_order` (number, optional) - Priority to give this product when included in product lists on category pages and in search results. Lower integers will place the product closer to the top of the results.
+ `condition` (enum[string], optional) - The product condition. Will be shown on the product page if the `is_condition_shown` field's value is `true`. Possible values: `New`, `Used`, `Refurbished`.
    + `New`
    + `Used`
    + `Refurbished`
+ `is_condition_shown` (boolean, optional) - Flag used to determine whether the product condition is shown to the customer on the product page.
+ `order_quantity_minimum` (number, optional) - The minimum quantity an order must contain, to be eligible to purchase this product.
+ `order_quantity_maximum` (number, optional) - The maximum quantity an order can contain when purchasing the product.
+ `page_title` (string, optional) - Custom title for the product page. If not defined, the product name will be used as the meta title.
+ `meta_keywords` (array[string], optional) - Custom meta keywords for the product page. If not defined, the store's default keywords will be used.
+ `meta_description` (string, optional) - Custom meta description for the product page. If not defined, the store's default meta description will be used.
+ `view_count` (number, optional) - The number of times the product has been viewed.
+ `preorder_release_date` (string, optional) - Pre-order release date. See the `availability` field for details on setting a product's availability to accept pre-orders.
+ `preorder_message` (string, optional) - Custom expected-date message to display on the product page. If undefined, the message defaults to the storewide setting. Can contain the `%%DATE%%` placeholder, which will be substituted for the release date.
+ `is_preorder_only` (boolean, optional) - If set to `false`, the product will not change its availability from `preorder` to `available` on the release date. Otherwise, on the release date the product's availability/status will change to `available`.
+ `is_price_hidden` (boolean, optional) - False by default, indicating that this product's price should be shown on the product page. If set to `true`, the price is hidden. (NOTE: To successfully set `is_price_hidden` to `true`, the `availability` value must be `disabled`.)
+ `price_hidden_label` (string, optional) - By default, an empty string. If `is_price_hidden` is `true`, the value of `price_hidden_label` is displayed instead of the price. (NOTE: To successfully set a non-empty string value with `is_price_hidden` set to `true`, the `availability` value must be `disabled`.)
+ `custom_url` (CustomUrlProduct, optional) - The custom URL for the product on the storefront.
+ `open_graph_type` (enum[string], optional) - Type of product, defaults to `product`.
    + `product`
    + `album`
    + `book`
    + `drink`
    + `food`
    + `game`
    + `movie`
    + `song`
    + `tv_show`
+ `open_graph_title` (string, optional) - Title of the product, if not specified the product name will be used instead.
+ `open_graph_description` (string, optional) - Description to use for the product, if not specified then the meta_description will be used instead.
+ `open_graph_use_meta_description` (boolean, optional) - Flag to determine if product description or open graph description is used.
+ `open_graph_use_product_name` (boolean, optional) - Flag to determine if product name or open graph name is used.
+ `open_graph_use_image` (boolean, optional) - Flag to determine if product image or open graph image is used.


## ProductPost (object)
The model for a POST to create a product.



### Properties
+ `name` (string, optional) - The product name.
+ `type` (enum[string], optional) - The product type. One of: `physical` - a physical stock unit, `digital` - a digital download.
    + `physical`
    + `digital`
+ `sku` (string, optional) - User defined product code/stock keeping unit (SKU).
+ `description` (string, optional) - The product description, which can include HTML formatting.
+ `weight` (number, optional) - Weight of the product, which can be used when calculating shipping costs.
+ `width` (number, optional) - Width of the product, which can be used when calculating shipping costs.
+ `depth` (number, optional) - Depth of the product, which can be used when calculating shipping costs.
+ `height` (number, optional) - Height of the product, which can be used when calculating shipping costs.
+ `price` (number, optional) - The price of the product. The price should include or exclude tax, based on the store settings.
+ `cost_price` (number, optional) - The cost price of the product. Stored for reference only; it is not used or displayed anywhere on the store.
+ `retail_price` (number, optional) - The retail cost of the product. If entered, the retail cost price will be shown on the product page.
+ `sale_price` (number, optional) - If entered, the sale price will be used instead of value in the price field when calculating the product's cost.
+ `tax_class_id` (number, optional) - The ID of the tax class applied to the product. (NOTE: Value ignored if automatic tax is enabled.)
+ `product_tax_code` (string, optional) - Accepts AvaTax System Tax Codes, which identify products and services that fall into special sales-tax categories. By using these codes, merchants who subscribe to BigCommerce's Avalara Premium integration can calculate sales taxes more accurately. Stores without Avalara Premium will ignore the code when calculating sales tax. Do not pass more than one code. The codes are case-sensitive. For details, please see Avalara's documentation.
+ `categories` (array[number], optional) - An array of IDs for the categories to which this product belongs. When updating a product, if an array of categories is supplied, all product categories will be overwritten. Does not accept more than 1,000 ID values.
+ `brand_id` (number, optional) - The ID associated with the product's brand.
+ `inventory_level` (number, optional) - Current inventory level of the product. Simple inventory tracking must be enabled (See the `inventory_tracking` field) for this to take any effect.
+ `inventory_warning_level` (number, optional) - Inventory warning level for the product. When the product's inventory level drops below the warning level, the store owner will be informed. Simple inventory tracking must be enabled (see the `inventory_tracking` field) for this to take any effect.
+ `inventory_tracking` (enum[string], optional) - The type of inventory tracking for the product. Values are: `none` - inventory levels will not be tracked; `product` - inventory levels will be tracked using the `inventory_level` and `inventory_warning_level` fields; `variant` - inventory levels will be tracked based on variants, which maintain their own warning levels and inventory levels.
    + `none`
    + `product`
    + `variant`
+ `fixed_cost_shipping_price` (number, optional) - A fixed shipping cost for the product. If defined, this value will be used during checkout instead of normal shipping-cost calculation.
+ `is_free_shipping` (boolean, optional) - Flag used to indicate whether the product has free shipping. If `true`, the shipping cost for the product will be zero.
+ `is_visible` (boolean, optional) - Flag to determine whether the product should be displayed to customers browsing the store. If `true`, the product will be displayed. If `false`, the product will be hidden from view.
+ `is_featured` (boolean, optional) - Flag to determine whether the product should be included in the `featured products` panel when viewing the store.
+ `related_products` (array[number], optional) - An array of IDs for the related products.
+ `warranty` (string, optional) - Warranty information displayed on the product page. Can include HTML formatting.
+ `bin_picking_number` (string, optional) - The BIN picking number for the product.
+ `layout_file` (string, optional) - The layout template file used to render this product.
+ `upc` (string, optional) - The product UPC code, which is used in feeds for shopping comparison sites and external channel integrations.
+ `search_keywords` (string, optional) - A comma-separated list of keywords that can be used to locate the product when searching the store.
+ `availability` (enum[string], optional) - Availability of the product. Availability options are: `available` - the product can be purchased on the storefront; `disabled` - the product is listed in the storefront, but cannot be purchased; `preorder` - the product is listed for pre-orders.
    + `available`
    + `disabled`
    + `preorder`
+ `availability_description` (string, optional) - Availability text displayed on the checkout page, under the product title. Tells the customer how long it will normally take to ship this product, such as: 'Usually ships in 24 hours.'
+ `gift_wrapping_options_type` (enum[string], optional) - Type of gift-wrapping options. Values: `any` - allow any gift-wrapping options in the store; `none` - disallow gift-wrapping on the product; `list` – provide a list of IDs in the `gift_wrapping_options_list` field.
    + `any`
    + `none`
    + `list`
+ `gift_wrapping_options_list` (array[number], optional) - A list of gift-wrapping option IDs.
+ `sort_order` (number, optional) - Priority to give this product when included in product lists on category pages and in search results. Lower integers will place the product closer to the top of the results.
+ `condition` (enum[string], optional) - The product condition. Will be shown on the product page if the `is_condition_shown` field's value is `true`. Possible values: `New`, `Used`, `Refurbished`.
    + `New`
    + `Used`
    + `Refurbished`
+ `is_condition_shown` (boolean, optional) - Flag used to determine whether the product condition is shown to the customer on the product page.
+ `order_quantity_minimum` (number, optional) - The minimum quantity an order must contain, to be eligible to purchase this product.
+ `order_quantity_maximum` (number, optional) - The maximum quantity an order can contain when purchasing the product.
+ `page_title` (string, optional) - Custom title for the product page. If not defined, the product name will be used as the meta title.
+ `meta_keywords` (array[string], optional) - Custom meta keywords for the product page. If not defined, the store's default keywords will be used.
+ `meta_description` (string, optional) - Custom meta description for the product page. If not defined, the store's default meta description will be used.
+ `view_count` (number, optional) - The number of times the product has been viewed.
+ `preorder_release_date` (string, optional) - Pre-order release date. See the `availability` field for details on setting a product's availability to accept pre-orders.
+ `preorder_message` (string, optional) - Custom expected-date message to display on the product page. If undefined, the message defaults to the storewide setting. Can contain the `%%DATE%%` placeholder, which will be substituted for the release date.
+ `is_preorder_only` (boolean, optional) - If set to `false`, the product will not change its availability from `preorder` to `available` on the release date. Otherwise, on the release date the product's availability/status will change to `available`.
+ `is_price_hidden` (boolean, optional) - False by default, indicating that this product's price should be shown on the product page. If set to `true`, the price is hidden. (NOTE: To successfully set `is_price_hidden` to `true`, the `availability` value must be `disabled`.)
+ `price_hidden_label` (string, optional) - By default, an empty string. If `is_price_hidden` is `true`, the value of `price_hidden_label` is displayed instead of the price. (NOTE: To successfully set a non-empty string value with `is_price_hidden` set to `true`, the `availability` value must be `disabled`.)
+ `custom_url` (CustomUrlProduct, optional) - The custom URL for the product on the storefront.
+ `open_graph_type` (enum[string], optional) - Type of product, defaults to `product`.
    + `product`
    + `album`
    + `book`
    + `drink`
    + `food`
    + `game`
    + `movie`
    + `song`
    + `tv_show`
+ `open_graph_title` (string, optional) - Title of the product, if not specified the product name will be used instead.
+ `open_graph_description` (string, optional) - Description to use for the product, if not specified then the meta_description will be used instead.
+ `open_graph_use_meta_description` (boolean, optional) - Flag to determine if product description or open graph description is used.
+ `open_graph_use_product_name` (boolean, optional) - Flag to determine if product name or open graph name is used.
+ `open_graph_use_image` (boolean, optional) - Flag to determine if product image or open graph image is used.
+ `custom_fields` (array[CustomFieldBase], optional) 
+ `bulk_pricing_rules` (array[BulkPricingRuleBase], optional) 
+ `variants` (array[VariantProductPost], optional) 


## CustomFieldBase (object)
Common CustomField properties.



### Properties
+ `name` (string, optional) - The name of the field, shown on the storefront, orders, etc.
+ `value` (string, optional) - The name of the field, shown on the storefront, orders, etc.


## BulkPricingRuleBase (object)
Common BulkPricingRule properties



### Properties
+ `quantity_min` (number, optional) - The minimum inclusive quantity of a product to satisfy this rule. Must be greater than or equal to zero.
+ `quantity_max` (number, optional) - The maximum inclusive quantity of a product to satisfy this rule. Must be greater than the `quantity_min` value – unless this field has a value of 0 (zero), in which case there will be no maximum bound for this rule.
+ `type` (enum[string], optional) - The type of adjustment that is made. Values: `price` - the adjustment amount per product; `percent` - the adjustment as a percentage of the original price; `fixed` - the adjusted absolute price of the product.
    + `price`
    + `percent`
    + `fixed`
+ `amount` (number, optional) - The value of the adjustment by the bulk pricing rule.


## ProductPut (object)
The model for a PUT to update a product.



### Properties
+ `name` (string, optional) - The product name.
+ `type` (enum[string], optional) - The product type. One of: `physical` - a physical stock unit, `digital` - a digital download.
    + `physical`
    + `digital`
+ `sku` (string, optional) - User defined product code/stock keeping unit (SKU).
+ `description` (string, optional) - The product description, which can include HTML formatting.
+ `weight` (number, optional) - Weight of the product, which can be used when calculating shipping costs.
+ `width` (number, optional) - Width of the product, which can be used when calculating shipping costs.
+ `depth` (number, optional) - Depth of the product, which can be used when calculating shipping costs.
+ `height` (number, optional) - Height of the product, which can be used when calculating shipping costs.
+ `price` (number, optional) - The price of the product. The price should include or exclude tax, based on the store settings.
+ `cost_price` (number, optional) - The cost price of the product. Stored for reference only; it is not used or displayed anywhere on the store.
+ `retail_price` (number, optional) - The retail cost of the product. If entered, the retail cost price will be shown on the product page.
+ `sale_price` (number, optional) - If entered, the sale price will be used instead of value in the price field when calculating the product's cost.
+ `tax_class_id` (number, optional) - The ID of the tax class applied to the product. (NOTE: Value ignored if automatic tax is enabled.)
+ `product_tax_code` (string, optional) - Accepts AvaTax System Tax Codes, which identify products and services that fall into special sales-tax categories. By using these codes, merchants who subscribe to BigCommerce's Avalara Premium integration can calculate sales taxes more accurately. Stores without Avalara Premium will ignore the code when calculating sales tax. Do not pass more than one code. The codes are case-sensitive. For details, please see Avalara's documentation.
+ `categories` (array[number], optional) - An array of IDs for the categories to which this product belongs. When updating a product, if an array of categories is supplied, all product categories will be overwritten. Does not accept more than 1,000 ID values.
+ `brand_id` (number, optional) - The ID associated with the product's brand.
+ `inventory_level` (number, optional) - Current inventory level of the product. Simple inventory tracking must be enabled (See the `inventory_tracking` field) for this to take any effect.
+ `inventory_warning_level` (number, optional) - Inventory warning level for the product. When the product's inventory level drops below the warning level, the store owner will be informed. Simple inventory tracking must be enabled (see the `inventory_tracking` field) for this to take any effect.
+ `inventory_tracking` (enum[string], optional) - The type of inventory tracking for the product. Values are: `none` - inventory levels will not be tracked; `product` - inventory levels will be tracked using the `inventory_level` and `inventory_warning_level` fields; `variant` - inventory levels will be tracked based on variants, which maintain their own warning levels and inventory levels.
    + `none`
    + `product`
    + `variant`
+ `fixed_cost_shipping_price` (number, optional) - A fixed shipping cost for the product. If defined, this value will be used during checkout instead of normal shipping-cost calculation.
+ `is_free_shipping` (boolean, optional) - Flag used to indicate whether the product has free shipping. If `true`, the shipping cost for the product will be zero.
+ `is_visible` (boolean, optional) - Flag to determine whether the product should be displayed to customers browsing the store. If `true`, the product will be displayed. If `false`, the product will be hidden from view.
+ `is_featured` (boolean, optional) - Flag to determine whether the product should be included in the `featured products` panel when viewing the store.
+ `related_products` (array[number], optional) - An array of IDs for the related products.
+ `warranty` (string, optional) - Warranty information displayed on the product page. Can include HTML formatting.
+ `bin_picking_number` (string, optional) - The BIN picking number for the product.
+ `layout_file` (string, optional) - The layout template file used to render this product.
+ `upc` (string, optional) - The product UPC code, which is used in feeds for shopping comparison sites and external channel integrations.
+ `search_keywords` (string, optional) - A comma-separated list of keywords that can be used to locate the product when searching the store.
+ `availability` (enum[string], optional) - Availability of the product. Availability options are: `available` - the product can be purchased on the storefront; `disabled` - the product is listed in the storefront, but cannot be purchased; `preorder` - the product is listed for pre-orders.
    + `available`
    + `disabled`
    + `preorder`
+ `availability_description` (string, optional) - Availability text displayed on the checkout page, under the product title. Tells the customer how long it will normally take to ship this product, such as: 'Usually ships in 24 hours.'
+ `gift_wrapping_options_type` (enum[string], optional) - Type of gift-wrapping options. Values: `any` - allow any gift-wrapping options in the store; `none` - disallow gift-wrapping on the product; `list` – provide a list of IDs in the `gift_wrapping_options_list` field.
    + `any`
    + `none`
    + `list`
+ `gift_wrapping_options_list` (array[number], optional) - A list of gift-wrapping option IDs.
+ `sort_order` (number, optional) - Priority to give this product when included in product lists on category pages and in search results. Lower integers will place the product closer to the top of the results.
+ `condition` (enum[string], optional) - The product condition. Will be shown on the product page if the `is_condition_shown` field's value is `true`. Possible values: `New`, `Used`, `Refurbished`.
    + `New`
    + `Used`
    + `Refurbished`
+ `is_condition_shown` (boolean, optional) - Flag used to determine whether the product condition is shown to the customer on the product page.
+ `order_quantity_minimum` (number, optional) - The minimum quantity an order must contain, to be eligible to purchase this product.
+ `order_quantity_maximum` (number, optional) - The maximum quantity an order can contain when purchasing the product.
+ `page_title` (string, optional) - Custom title for the product page. If not defined, the product name will be used as the meta title.
+ `meta_keywords` (array[string], optional) - Custom meta keywords for the product page. If not defined, the store's default keywords will be used.
+ `meta_description` (string, optional) - Custom meta description for the product page. If not defined, the store's default meta description will be used.
+ `view_count` (number, optional) - The number of times the product has been viewed.
+ `preorder_release_date` (string, optional) - Pre-order release date. See the `availability` field for details on setting a product's availability to accept pre-orders.
+ `preorder_message` (string, optional) - Custom expected-date message to display on the product page. If undefined, the message defaults to the storewide setting. Can contain the `%%DATE%%` placeholder, which will be substituted for the release date.
+ `is_preorder_only` (boolean, optional) - If set to `false`, the product will not change its availability from `preorder` to `available` on the release date. Otherwise, on the release date the product's availability/status will change to `available`.
+ `is_price_hidden` (boolean, optional) - False by default, indicating that this product's price should be shown on the product page. If set to `true`, the price is hidden. (NOTE: To successfully set `is_price_hidden` to `true`, the `availability` value must be `disabled`.)
+ `price_hidden_label` (string, optional) - By default, an empty string. If `is_price_hidden` is `true`, the value of `price_hidden_label` is displayed instead of the price. (NOTE: To successfully set a non-empty string value with `is_price_hidden` set to `true`, the `availability` value must be `disabled`.)
+ `custom_url` (CustomUrlProduct, optional) - The custom URL for the product on the storefront.
+ `open_graph_type` (enum[string], optional) - Type of product, defaults to `product`.
    + `product`
    + `album`
    + `book`
    + `drink`
    + `food`
    + `game`
    + `movie`
    + `song`
    + `tv_show`
+ `open_graph_title` (string, optional) - Title of the product, if not specified the product name will be used instead.
+ `open_graph_description` (string, optional) - Description to use for the product, if not specified then the meta_description will be used instead.
+ `open_graph_use_meta_description` (boolean, optional) - Flag to determine if product description or open graph description is used.
+ `open_graph_use_product_name` (boolean, optional) - Flag to determine if product name or open graph name is used.
+ `open_graph_use_image` (boolean, optional) - Flag to determine if product image or open graph image is used.
+ `id` (number, optional) - The unique numerical ID of the product; increments sequentially.
+ `custom_fields` (array[CustomField], optional) 
+ `bulk_pricing_rules` (array[BulkPricingRule], optional) 
+ `variants` (array[VariantProductPut], optional) 


## CatalogSummaryResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (CatalogSummary, optional) - A BigCommerce Catalog Summary object describes a lightweight summary of the catalog.
+ `meta` (object, optional) - Empty meta object; may be used later.


## CatalogSummary (object)
A BigCommerce Catalog Summary object describes a lightweight summary of the catalog.



### Properties
+ `inventory_count` (number, optional) - A count of all inventory items in the catalog.
+ `inventory_value` (number, optional) - Total value of store's inventory.
+ `primary_category_id` (number, optional) - ID of the category containing the most products.
+ `primary_category_name` (string, optional) - Name of the category containing the most products.


## MetaFieldCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[Metafield], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## Metafield (object)
Allows app partners to write custom data to various resources in the API.



### Properties
+ `permission_set` (enum[string], optional) - Determines whether the field is completely private to the app that owns the field (`app_only`), or visible to other API consumers (`read`), or completely open for reading and writing to other apps (`write`).
    + `app_only`
    + `read`
    + `write`
+ `namespace` (string, optional) - Namespace for the metafield, for organizational purposes.
+ `key` (string, optional) - The name of the field, for example: `location_id`, `color`.
+ `value` (string, optional) - The value of the field, for example: `1`, `blue`.
+ `description` (string, optional) - Description for the metafields.
+ `resource_type` (enum[string], optional) - The type of resource with which the metafield is associated.
    + `category`
    + `brand`
    + `product`
    + `variant`
+ `resource_id` (number, optional) - The unique identifier for the resource with which the metafield is associated.
+ `id` (number, optional) - The unique identifier for the metafields.
+ `created_at` (string, optional) - Date and time of the metafield's creation.
+ `updated_at` (string, optional) - Date and time when the metafield was last updated.


## MetafieldResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (Metafield, optional) - Allows app partners to write custom data to various resources in the API.
+ `meta` (object, optional) - Empty meta object; may be used later.


## MetafieldBase (object)
Common Metafield properties.



### Properties
+ `permission_set` (enum[string], optional) - Determines whether the field is completely private to the app that owns the field (`app_only`), or visible to other API consumers (`read`), or completely open for reading and writing to other apps (`write`).
    + `app_only`
    + `read`
    + `write`
+ `namespace` (string, optional) - Namespace for the metafield, for organizational purposes.
+ `key` (string, optional) - The name of the field, for example: `location_id`, `color`.
+ `value` (string, optional) - The value of the field, for example: `1`, `blue`.
+ `description` (string, optional) - Description for the metafields.
+ `resource_type` (enum[string], optional) - The type of resource with which the metafield is associated.
    + `category`
    + `brand`
    + `product`
    + `variant`
+ `resource_id` (number, optional) - The unique identifier for the resource with which the metafield is associated.


## MetafieldPut (object)
The model for a PUT to update metafield.



### Properties
+ `permission_set` (enum[string], optional) - Determines whether the field is completely private to the app that owns the field (`app_only`), or visible to other API consumers (`read`), or completely open for reading and writing to other apps (`write`).
    + `app_only`
    + `read`
    + `write`
+ `namespace` (string, optional) - Namespace for the metafield, for organizational purposes.
+ `key` (string, optional) - The name of the field, for example: `location_id`, `color`.
+ `value` (string, optional) - The value of the field, for example: `1`, `blue`.
+ `description` (string, optional) - Description for the metafields.
+ `resource_type` (enum[string], optional) - The type of resource with which the metafield is associated.
    + `category`
    + `brand`
    + `product`
    + `variant`
+ `resource_id` (number, optional) - The unique identifier for the resource with which the metafield is associated.
+ `id` (number, optional) - The unique identifier for the metafields.


## ComplexRuleCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[ComplexRule], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## ComplexRule (object)
Apply price, weight, image, or availabilty adjustments to product, based on a set of conditions. A complex rule's condition must either contain more than one modifier value, or else contain a modifier value and a variant ID.



### Properties
+ `product_id` (number, optional) - The unique numeric ID of the product with which the rule is associated; increments sequentially.
+ `sort_order` (number, optional) - The priority to give this rule when making adjustments to the product properties.
+ `enabled` (boolean, optional) - Flag for determining whether the rule is to be used when adjusting a product's price, weight, image, or availabilty.
+ `stop` (boolean, optional) - Flag for determining whether other rules should not be applied after this rule has been applied.
+ `purchasing_disabled` (boolean, optional) - Flag for determining whether the rule should disable purchasing of a product when the conditions are applied.
+ `purchasing_disabled_message` (string, optional) - Message displayed on the storefront when a rule disables the purchasing of a product.
+ `purchasing_hidden` (boolean, optional) - Flag for determining whether the rule should hide purchasing of a product when the conditions are applied.
+ `price_adjuster` (Adjuster, optional) 
+ `weight_adjuster` (Adjuster, optional) 
+ `id` (number, optional) - The unique numeric ID of the rule; increments sequentially.
+ `image_url` (string, optional) - The URL for an image displayed on the storefront when the conditions are applied.
+ `conditions` (array[ComplexRuleCondition], optional) 


## ComplexRuleCondition (object)
Complex rules may return with conditions that apply to one or more variants, or with a single modifier value (if the rules were created using the v2 API or the control panel). Complex rules created or updated in the v3 API must have conditions that either reference multiple `modifier_value_id`'s, or else reference a `modifier_value_id` and a `variant_id`.



### Properties
+ `id` (number, optional) - The unique numeric ID of the rule condition; increments sequentially.
+ `rule_id` (number, optional) - The unique numeric ID of the rule with which the condition is associated.
+ `modifier_id` (number, optional) - The unique numeric ID of the modifier with which the rule condition is associated.
+ `modifier_value_id` (number, optional) - The unique numeric ID of the modifier value with which the rule condition is associated.
+ `variant_id` (number, optional) - The unique numeric ID of the variant with which the rule condition is associated.
+ `combination_id` (number, optional) - (READ-ONLY:) The unique numeric ID of the SKU (v2 API), or Combination, with which the rule condition is associated. This is to maintain cross-compatibility between v2 and v3.


## ComplexRuleResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (ComplexRule, optional) - Apply price, weight, image, or availabilty adjustments to product, based on a set of conditions. A complex rule's condition must either contain more than one modifier value, or else contain a modifier value and a variant ID.
+ `meta` (object, optional) - Empty meta object; may be used later.


## ComplexRuleBase (object)
Common ComplexRule properties.

### Properties
+ `product_id` (number, optional) - The unique numeric ID of the product with which the rule is associated; increments sequentially.
+ `sort_order` (number, optional) - The priority to give this rule when making adjustments to the product properties.
+ `enabled` (boolean, optional) - Flag for determining whether the rule is to be used when adjusting a product's price, weight, image, or availabilty.
+ `stop` (boolean, optional) - Flag for determining whether other rules should not be applied after this rule has been applied.
+ `purchasing_disabled` (boolean, optional) - Flag for determining whether the rule should disable purchasing of a product when the conditions are applied.
+ `purchasing_disabled_message` (string, optional) - Message displayed on the storefront when a rule disables the purchasing of a product.
+ `purchasing_hidden` (boolean, optional) - Flag for determining whether the rule should hide purchasing of a product when the conditions are applied.
+ `price_adjuster` (Adjuster, optional) 
+ `weight_adjuster` (Adjuster, optional) 


## ComplexRulePost (object)
The model for a POST to create a complex rule on a product.



### Properties
+ `product_id` (number, optional) - The unique numeric ID of the product with which the rule is associated; increments sequentially.
+ `sort_order` (number, optional) - The priority to give this rule when making adjustments to the product properties.
+ `enabled` (boolean, optional) - Flag for determining whether the rule is to be used when adjusting a product's price, weight, image, or availabilty.
+ `stop` (boolean, optional) - Flag for determining whether other rules should not be applied after this rule has been applied.
+ `purchasing_disabled` (boolean, optional) - Flag for determining whether the rule should disable purchasing of a product when the conditions are applied.
+ `purchasing_disabled_message` (string, optional) - Message displayed on the storefront when a rule disables the purchasing of a product.
+ `purchasing_hidden` (boolean, optional) - Flag for determining whether the rule should hide purchasing of a product when the conditions are applied.
+ `price_adjuster` (Adjuster, optional) 
+ `weight_adjuster` (Adjuster, optional) 
+ `conditions` (array[ComplexRuleConditionBase], optional) 


## ComplexRuleConditionBase (object)
Common ComplexRuleCondition properties.



### Properties
+ `id` (number, optional) - The unique numeric ID of the rule condition; increments sequentially.
+ `rule_id` (number, optional) - The unique numeric ID of the rule with which the condition is associated.
+ `modifier_id` (number, optional) - The unique numeric ID of the modifier with which the rule condition is associated.
+ `modifier_value_id` (number, optional) - The unique numeric ID of the modifier value with which the rule condition is associated.
+ `variant_id` (number, optional) - The unique numeric ID of the variant with which the rule condition is associated.


## ComplexRulePut (object)
The model for a PUT to update a complex rule on a product.



### Properties
+ `product_id` (number, optional) - The unique numeric ID of the product with which the rule is associated; increments sequentially.
+ `sort_order` (number, optional) - The priority to give this rule when making adjustments to the product properties.
+ `enabled` (boolean, optional) - Flag for determining whether the rule is to be used when adjusting a product's price, weight, image, or availabilty.
+ `stop` (boolean, optional) - Flag for determining whether other rules should not be applied after this rule has been applied.
+ `purchasing_disabled` (boolean, optional) - Flag for determining whether the rule should disable purchasing of a product when the conditions are applied.
+ `purchasing_disabled_message` (string, optional) - Message displayed on the storefront when a rule disables the purchasing of a product.
+ `purchasing_hidden` (boolean, optional) - Flag for determining whether the rule should hide purchasing of a product when the conditions are applied.
+ `price_adjuster` (Adjuster, optional) 
+ `weight_adjuster` (Adjuster, optional) 
+ `id` (number, optional) - The unique numeric ID of the rule; increments sequentially.
+ `conditions` (array[ComplexRuleConditionBase], optional) 


## ConfigurableFieldCollectionResponse (object)
Response payload for the BigCommerce configurable fields API.



### Properties
+ `data` (array[ConfigurableField], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## ConfigurableField (object)
A configurable field, which is a means of collecting information from a shopper about how they'd like their product configured. This information is then stored alongside the product when added to cart and is reference-able on the order for fulfillment purposes. NOTE: Configurable fields are deprecated, as their complete set of functionality is available via Product Options. They may be removed in a future release.



### Properties
+ `name` (string, optional) - The name for the configurable field. Will display on the storefront and can be used as a reference point in the Orders API.
+ `type` (enum[string], optional) - The type of the configurable field, which determines what sort of information the field is intended to collect on the storefront. Supported types in include a text input, a multi-line textarea, a checkbox, a file upload, and a dropdown selection.
    + `text`
    + `textarea`
    + `checkbox`
    + `file`
    + `select`
+ `file_allowed_types` (array[string], optional) - For fields of "file" type, this controls the allowed file types for upload.
+ `file_max_size` (array[number], optional) - For fields of "file" type, this controls the maximum file size. The platform has a maximum file size of 512MB for all uploads regardless of this setting.
+ `select_options` (array[string], optional) - For fields of "select" type, this is an array of the options which should be presented in the dropdown.
+ `required` (boolean, optional) - Controls whether the field is required to have some input before a product may be added to cart.
+ `sort_order` (number, optional) - Controls the sort order of this field relative to other configurable fields on the product, for purposes of ordering them on the storefront.
+ `id` (number, optional) - The unique numeric ID of the configurable field; increments sequentially.


## ConfigurableFieldResponse (object)
Response payload for the BigCommerce single configurable field API.



### Properties
+ `data` (ConfigurableField, optional) - A configurable field, which is a means of collecting information from a shopper about how they'd like their product configured. This information is then stored alongside the product when added to cart and is reference-able on the order for fulfillment purposes. NOTE: Configurable fields are deprecated, as their complete set of functionality is available via Product Options. They may be removed in a future release.
+ `meta` (object, optional) - Empty meta object; may be used later.


## CustomFieldCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[CustomField], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## CustomFieldResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (CustomField, optional) - Gets custom fields associated with a product. These allow you to specify additional information that will appear on the product's page, such as a book's ISBN or a DVD's release date.
+ `meta` (object, optional) - Empty meta object; may be used later.


## ConfigurableFieldBase (object)
Common ConfigurableField properties.



### Properties
+ `name` (string, optional) - The name for the configurable field. Will display on the storefront and can be used as a reference point in the Orders API.
+ `type` (enum[string], optional) - The type of the configurable field, which determines what sort of information the field is intended to collect on the storefront. Supported types in include a text input, a multi-line textarea, a checkbox, a file upload, and a dropdown selection.
    + `text`
    + `textarea`
    + `checkbox`
    + `file`
    + `select`
+ `file_allowed_types` (array[string], optional) - For fields of "file" type, this controls the allowed file types for upload.
+ `file_max_size` (array[number], optional) - For fields of "file" type, this controls the maximum file size. The platform has a maximum file size of 512MB for all uploads regardless of this setting.
+ `select_options` (array[string], optional) - For fields of "select" type, this is an array of the options which should be presented in the dropdown.
+ `required` (boolean, optional) - Controls whether the field is required to have some input before a product may be added to cart.
+ `sort_order` (number, optional) - Controls the sort order of this field relative to other configurable fields on the product, for purposes of ordering them on the storefront.


## BulkPricingRuleCollectionResponse (object)
Response payload for the BigCommerce bulk pricing rules API.



### Properties
+ `data` (array[BulkPricingRule], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## BulkPricingRuleResponse (object)
Response payload for the BigCommerce single bulk pricing rule API.



### Properties
+ `data` (BulkPricingRule, optional) - Rules that offer price discounts based on quantity breaks.
+ `meta` (object, optional) - Empty meta object; may be used later.


## PriceListCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[PriceList], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## PriceList (object)


### Properties
+ `id` (number, optional) - The unique numeric ID of the `Price List`; increments sequentially.
+ `date_created` (string, optional) - The date on which the `Price List` was created.
+ `date_modified` (string, optional) - The date on which the `Price List` was created.
+ `record_count` (number, optional) - The number of `Price Records` associated with this `Price List`.
+ `name` (string, optional) - The unique name of the Price List.
+ `active` (boolean, optional) - Whether or not this `Price List` and its prices are active.  Defaults to `true`.


## PriceListResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (PriceList, optional) 
+ `meta` (object, optional) - Empty meta object; may be used later.


## PriceListBase (object)
Common Price List properties.



### Properties
+ `name` (string, optional) - The unique name of the Price List.
+ `active` (boolean, optional) - Whether or not this `Price List` and its prices are active.  Defaults to `true`.


## PriceRecordCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[PriceRecord], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## PriceRecord (object)
The comprehensive Price Record object.



### Properties
+ `calculated_price` (number, optional) - The price of the variant as seen on the storefront if a price record is in effect. It will be equal to the `sale_price`, if set, and the `price` if there is not a `sale_price`.  Read only.
+ `date_created` (string, optional) - The date on which the Price entry was created.
+ `date_modified` (string, optional) - The date on which the Price entry was created.
+ `product_id` (number, optional) - The id of the `Product` this `Price Record`'s variant_id is associated with.  Read only.
+ `price` (number, optional) - The list price for the variant mapped in a Price List. Overrides any existing or Catalog list price for the variant/product.
+ `sale_price` (number, optional) - The sale price for the variant mapped in a Price List. Overrides any existing or Catalog sale price for the variant/product. If empty, the sale price will be treated as not being set on this variant.
+ `retail_price` (number, optional) - The retail price for the variant mapped in a Price List. Overrides any existing or Catalog retail price for the variant/product.  If empty, the retail price will be treated as not being set on this variant.
+ `map_price` (number, optional) - The MAP (Manufacturer's Advertised Price) for the variant mapped in a Price List. Overrides any existing or Catalog MAP price for the variant/product. If empty, the MAP price will be treated as not being set on this variant.
+ `bulk_pricing_tiers` (array[BulkPricingTier], optional) 
+ `sku` (string, optional) - The SKU code associated with this `Price Record` if requested and it exists.


## BulkPricingTier (object)


### Properties
+ `quantity_min` (number, optional) - The minimum quantity of associated variant in the cart needed to qualify for this tiers pricing.
+ `quantity_max` (number, optional) - The maximum allowed quantity of associated variant in the cart to qualify for this tiers pricing.
+ `type` (enum[string], optional) - The type of adjustment that is made. Acceptable values: price – the adjustment amount per product; percent – the adjustment as a percentage of the original price; fixed – the adjusted absolute price of the product.
    + `price`
    + `percent`
    + `fixed`
+ `amount` (number, optional) - The price adjustment amount. This value along with the type will decide the price per variant for the pricing tier.


## PriceRecordResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (PriceRecord, optional) - The comprehensive Price Record object.
+ `meta` (object, optional) - Empty meta object; may be used later.


## PriceRecordBase (object)
Common Price Record properties.



### Properties
+ `price` (number, optional) - The list price for the variant mapped in a Price List. Overrides any existing or Catalog list price for the variant/product.
+ `sale_price` (number, optional) - The sale price for the variant mapped in a Price List. Overrides any existing or Catalog sale price for the variant/product. If empty, the sale price will be treated as not being set on this variant.
+ `retail_price` (number, optional) - The retail price for the variant mapped in a Price List. Overrides any existing or Catalog retail price for the variant/product.  If empty, the retail price will be treated as not being set on this variant.
+ `map_price` (number, optional) - The MAP (Manufacturer's Advertised Price) for the variant mapped in a Price List. Overrides any existing or Catalog MAP price for the variant/product. If empty, the MAP price will be treated as not being set on this variant.
+ `bulk_pricing_tiers` (array[BulkPricingTier], optional) 
+ `sku` (string, optional) - The SKU code associated with this `Price Record` if requested and it exists.


## PriceRecordBatchItem (object)
`Price Record` object used in batch create or update.



### Properties
+ `variant_id` (number, optional) - The variant with which this price set is associated. Either variant_id or sku is required.
+ `sku` (string, optional) - The sku for the variant with which this price set is associated.  Either sku or variant_id is required.
+ `currency` (string, optional) - The 3-letter currency code with which this price set is associated.
+ `price` (number, optional) - The list price for the variant mapped in a Price List. Overrides any existing or Catalog list price for the variant/product.
+ `sale_price` (number, optional) - The sale price for the variant mapped in a Price List. Overrides any existing or Catalog sale price for the variant/product. If empty, the sale price will be treated as not being set on this variant.
+ `retail_price` (number, optional) - The retail price for the variant mapped in a Price List. Overrides any existing or Catalog retail price for the variant/product.  If empty, the retail price will be treated as not being set on this variant.
+ `map_price` (number, optional) - The MAP (Manufacturer's Advertised Price) for the variant mapped in a Price List. Overrides any existing or Catalog MAP price for the variant/product. If empty, the MAP price will be treated as not being set on this variant.
+ `bulk_pricing_tiers` (array[BulkPricingTier], optional) 


## PriceRecordIdentifiers (object)


### Properties
+ `price_list_id` (number, optional) - The Price List with which this price set is associated.
+ `variant_id` (number, optional) - The variant with which this price set is associated. Either variant_id or sku is required.
+ `sku` (string, optional) - The variant with which this price set is associated. Either sku or variant_id is required.
+ `currency` (string, optional) - The 3-letter currency code with which this price set is associated.


## PriceRecordBatchErrorSet (object)
Error during `Price Record` batch PUT.  Includes data sent in the request and errors.



### Properties
+ `data` (PriceRecordIdentifiers, optional) - `Price Record` object used in batch create or update.
+ `field_errors` (string, optional) 


## BaseError (object)
Error payload for the BigCommerce API.

### Properties
+ `status` (number, optional) - The HTTP status code.
+ `title` (string, optional) - The error title describing the particular error.
+ `type` (string, optional) 
+ `instance` (string, optional) 


## TransactionPost (object)
Payload to create a transaction in BigCommerce.



### Properties
+ `event` (enum[string], required) - Store event that created the transaction.
    + `purchase`
    + `authorization`
    + `capture`
    + `refund`
    + `void`
    + `pending`
    + `settled`
+ `method` (enum[string], required) - The payment method: `credit_card` - a credit-card transaction; `electronic_wallet` - an online wallet; `store_credit` - a transaction using store credit; `gift_certificate` - a transaction using a gift certificate; `custom` - manual payment methods; `token` - payment token; `nonce` - temporary payment token; `offsite` - online payment off the site (e.g., PayPal); `offline` - payment method that takes place offline.
    + `credit_card`
    + `electronic_wallet`
    + `gift_certificate`
    + `store_credit`
    + `apple_pay_card`
    + `apple_pay_token`
    + `token`
    + `custom`
    + `offsite`
    + `offline`
    + `nonce`
+ `amount` (number, required) - Amount of money in the transaction.
+ `currency` (string, required) - Currency used for the transaction.
+ `gateway` (enum[string], required) - The payment gateway, where applicable.
    + `2checkout`
    + `adyen`
    + `amazon`
    + `authorizenet`
    + `bankdeposit`
    + `braintree`
    + `cheque`
    + `cod`
    + `custom`
    + `firstdatagge4`
    + `giftcertificate`
    + `hps`
    + `instore`
    + `klarna`
    + `migs`
    + `moneyorder`
    + `nmi`
    + `paypalexpress`
    + `paypalpaymentsprous`
    + `paypalpaymentsprouk`
    + `plugnpay`
    + `qbmsv2`
    + `securenet`
    + `square`
    + `storecredit`
    + `stripe`
    + `testgateway`
    + `usaepay`
+ `gateway_transaction_id` (string, optional) - The transaction ID returned by the payment gateway for this transaction item.
+ `date_created` (string, optional) - The datetime of the transaction.
+ `test` (boolean, optional) - True if the transaction performed was a test, or if the gateway is in test mode.
+ `status` (enum[string], optional) - Status of the transaction.
    + `ok`
    + `error`
+ `fraud_review` (boolean, optional) - Result of gateway fraud review, if any. Default is `false`.
+ `reference_transaction_id` (number, optional) - Identifier for an existing transaction upon which this transaction acts.
+ `offline` (Offline, optional) - Offline payment (e.g., check or purchase order).
+ `custom` (Custom, optional) - Custom payment from manual order.


## Offline (object)
Offline payment (e.g., check or purchase order).



### Properties
+ `display_name` (string, optional) - Display name for the offline payment.


## Custom (object)
Custom payment from manual order.



### Properties
+ `payment_method` (string, optional) - Text entered for the payment method in the control panel.


## TransactionResponse (object)
Response payload for the BigCommerce Order Transactions API single transaction.



### Properties
+ `data` (Transaction, optional) - A BigCommerce Transaction object describes a single transaction.
+ `meta` (object, optional) - May be used in the future


## Transaction (object)
A BigCommerce Transaction object describes a single transaction.



### Properties
+ `event` (enum[string], required) - Store event that created the transaction.
    + `purchase`
    + `authorization`
    + `capture`
    + `refund`
    + `void`
    + `pending`
    + `settled`
+ `method` (enum[string], required) - The payment method: `credit_card` - a credit-card transaction; `electronic_wallet` - an online wallet; `store_credit` - a transaction using store credit; `gift_certificate` - a transaction using a gift certificate; `custom` - manual payment methods; `token` - payment token; `nonce` - temporary payment token; `offsite` - online payment off the site (e.g., PayPal); `offline` - payment method that takes place offline.
    + `credit_card`
    + `electronic_wallet`
    + `gift_certificate`
    + `store_credit`
    + `apple_pay_card`
    + `apple_pay_token`
    + `token`
    + `custom`
    + `offsite`
    + `offline`
    + `nonce`
+ `amount` (number, required) - Amount of money in the transaction.
+ `currency` (string, required) - Currency used for the transaction.
+ `gateway` (enum[string], required) - The payment gateway, where applicable.
    + `2checkout`
    + `adyen`
    + `amazon`
    + `authorizenet`
    + `bankdeposit`
    + `braintree`
    + `cheque`
    + `cod`
    + `custom`
    + `firstdatagge4`
    + `giftcertificate`
    + `hps`
    + `instore`
    + `klarna`
    + `migs`
    + `moneyorder`
    + `nmi`
    + `paypalexpress`
    + `paypalpaymentsprous`
    + `paypalpaymentsprouk`
    + `plugnpay`
    + `qbmsv2`
    + `securenet`
    + `square`
    + `storecredit`
    + `stripe`
    + `testgateway`
    + `usaepay`
+ `gateway_transaction_id` (string, optional) - The transaction ID returned by the payment gateway for this transaction item.
+ `date_created` (string, optional) - The datetime of the transaction.
+ `test` (boolean, optional) - True if the transaction performed was a test, or if the gateway is in test mode.
+ `status` (enum[string], optional) - Status of the transaction.
    + `ok`
    + `error`
+ `fraud_review` (boolean, optional) - Result of gateway fraud review, if any. Default is `false`.
+ `reference_transaction_id` (number, optional) - Identifier for an existing transaction upon which this transaction acts.
+ `offline` (Offline, optional) - Offline payment (e.g., check or purchase order).
+ `custom` (Custom, optional) - Custom payment from manual order.
+ `id` (number, optional) - Unique identifier for the transaction.
+ `order_id` (string, optional) - Identifier for the BigCommerce Order with which this transaction is associated.
+ `avs_result` (AVSResult, optional) - Address Verification Service (AVS) result from the payment gateway.
+ `cvv_result` (CVVResult, optional) - Card Verification Value result from the payment gateway.
+ `credit_card` (CreditCard, optional) - A credit-card model.
+ `gift_certificate` (GiftCertificate, optional) - A gift-certificate model.
+ `store_credit` (StoreCredit, optional) - A store credit model.


## AVSResult (object)
Address Verification Service (AVS) result from the payment gateway.

### Properties
+ `code` (string, optional) - AVS code.
+ `message` (string, optional) - AVS message.
+ `street_match` (string, optional) - AVS Code for street matching result.
+ `postal_match` (string, optional) - AVS Code for postal matching result.


## CVVResult (object)
Card Verification Value result from the payment gateway.

### Properties
+ `code` (string, optional) - CVV code.
+ `message` (string, optional) - CVV message.


## CreditCard (object)
A credit-card model.



### Properties
+ `card_type` (string, optional) - The credit-card type: Visa, MasterCard, etc.
+ `card_iin` (string, optional) - The IIN of a credit-card number.
+ `card_last4` (string, optional) - The last 4 digits of a credit-card number.


## GiftCertificate (object)
A gift-certificate model.



### Properties
+ `code` (string, optional) - The gift-certificate code.
+ `original_balance` (number, optional) - The balance on a gift certificate when it was purchased.
+ `starting_balance` (number, optional) - The balance on a gift certificate at the time of this purchase.
+ `remaining_balance` (number, optional) - The remaining balance on a gift certificate.
+ `status` (enum[string], optional) - The status of a gift certificate: `active` - gift certificate is active; `pending` - gift certificate purchase is pending; `disabled` - gift certificate is disabled; `expired` - gift certificate is expired.
    + `active`
    + `pending`
    + `disabled`
    + `expired`


## StoreCredit (object)
A store credit model.



### Properties
+ `remaining_balance` (string, optional) - Remaining balance of shopper's store credit.


## TransactionCollectionResponse (object)
Response payload for the BigCommerce Order Transactions API.



### Properties
+ `data` (array[Transaction], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## NoContent (object)
No-content response for the BigCommerce API.



### Properties
+ `status` (number, optional) - 204 HTTP status code.
+ `title` (string, optional) - The error title describing the situation.
+ `type` (string, optional) 
+ `instance` (string, optional) 


## Job (object)
A job.

### Properties
+ `errors` (array[Error], optional) - The errors.
+ `id` (string, optional) - The identifier.
+ `percent_complete` (number, optional) - The percent complete.
+ `result` (string, optional) - The result.
+ `status` (string, optional) - The status.
+ `time` (string, optional) - The time.
+ `warnings` (array[Warning], optional) - The warnings.


## Error (object)


### Properties
+ `error` (string, optional) - The error.
+ `message` (string, optional) - The message.


## Warning (object)


### Properties
+ `message` (string, optional) - The message.
+ `warning` (string, optional) - The warning.


## Theme (object)
A theme.

### Properties
+ `variations` (array[Variation], optional) - The variations.
+ `uuid` (string, optional) - The identifier.
+ `name` (string, optional) - The theme name identifier.
+ `is_private` (boolean, optional) - Flag to identify private themes.


## Variation (object)
A variation.

### Properties
+ `description` (string, optional) - The description.
+ `external_id` (string, optional) - The external identifier.
+ `name` (string, optional) - The name.
+ `uuid` (string, optional) - The identifier.


## JobId (object)
The job identifier.

### Properties
+ `job_id` (string, optional) - The job identifier.


## Activate (object)
Request definition for activation endpoint.

### Properties
+ `variation_id` (string, required) - The identifier for the variation to activate.
+ `which` (enum[string], required) - Which configuration to use.
    + `original`
    + `last_activated`
    + `last_created`


## ThemesCollectionResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (array[Theme], optional) 
+ `meta` (CollectionMeta, optional) - Data about the response, including pagination and collection totals.


## ThemeResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (Theme, optional) - A theme.
+ `meta` (object, optional) - Empty meta object; may be used later.


## JobResponse (object)
Response payload for the BigCommerce API.



### Properties
+ `data` (Job, optional) - A job.
+ `meta` (object, optional) - Empty meta object; may be used later.


## WhichThemeToDownload (object)


### Properties
+ `which` (enum[string], optional) - Which revision to use.
    + `original`
    + `last_activated`
    + `last_created`


## ErrorResponse (object)


### Properties
+ `status` (number, optional) - The HTTP status code.
+ `title` (string, optional) - The error title describing the particular error.
+ `type` (string, optional) 
+ `instance` (string, optional) 
+ `errors` (string, optional) 


## NotFound (object)
Error payload for the BigCommerce API.



### Properties
+ `status` (number, optional) - 404 HTTP status code.
+ `title` (string, optional) - The error title describing the particular error.
+ `type` (string, optional) 
+ `instance` (string, optional) 


## PriceRecordBatchErrorResponse (object)
Errors during batch usage for the BigCommerce API.



### Properties
+ `batch_errors` (array[PriceRecordBatchErrorSet], optional)
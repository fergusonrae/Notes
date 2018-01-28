# Create XML feed file

## Best Practices

* The first line of the feed has the following format

  * ```xml
    <?xml version="1.0" encoding="utf-8"?>
    ```

* The standard character-encoding scheme must match the scheme used for special characters

* If you don't have a particular field, omit it. Do not include the field with a blank value



## XML Schema / elements

Will consist of 

`<Feed>`

​	`<Brands>`

​	`<Categories>`

​	`<Products>`

* `<Feed>`
  * **name** - short version of Bazaarvoice client name
  * **extractDate**
  * **incrememntal** - whether feed includes all catalog data. For SS, should be false
  * **supplemental** - Whather the feed contains supplemental catalog data. Should only be used when doing multiple catalog sources. So, Don't include for SS
  * **xmlns** - Schema reference with hard coded value. For SS, value is "http://www.bazaarvoice.com/xs/PRR/ProductFeed/14.7"
  * `<Brands>` 
    * `<Brand>` - Can include removed="true" attribute to mark it as inactive
      * **ExternalId** - Unique brand ID with only alphanumeric, hyhens, and underscores. Ensure it is a stable ID
      * **Name** - The name visible to end users
  * `<Categories>`

| **Element**                            | **Value**                                | **Required**                             |
| -------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| `Category`                             | Represents a product category in your feed and may include other elements listed in this table.You can include the **removed="true"** attribute in the `<Category>` element to mark the category [inactive](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Collect/product_feed.html#Control). | Yes                                      |
| `ExternalId`                           | Unique category or subcategory ID that can contain only alphanumeric characters, hyphens (`-`), and underscores (`_`). If a category ID contains an invalid character, replace it with an alternate character, such as an underscore. This format is used in the data feed only and does not affect end users. The ID is case insensitive, so you cannot use IDs that match except for case.Ensure that the category ID is stable and will not change, even if the name of the category changes. | Yes                                      |
| `ParentExternalId`                     | Parent category's ID of the subcategory in question. | No                                       |
| `Name` or `Names`                      | Name of the category or subcategory, which is visible to end users.If specifying localized categories in a multilingual implementation, include a `<Name>` element for each locale in a parent `<Names>` element, and then specify the **locale**attribute (of type String) for each `<Name>` child element. | Yes                                      |
| `CategoryPageUrl`or `CategoryPageUrls` | Unique URL for the category or subcategory. When specifying a URL, be aware of the following:Do not include extraneous query string parameters that you might use for tracking and partnership codes.If the URL contains a reserved (special) character, you must [URL-encode ![img](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Resources/Images/components/external-link.png)](https://en.wikipedia.org/wiki/Percent-encoding#Percent-encoding_in_a_URI) the character. For example, use `&amp` for an ampersand, use `%20` for a space, or use `%5B` and `%5D` for square brackets ([ ]).If specifying localized categories in a multilingual implementation, include a `<CategoryPageUrl>`element for each locale in a parent `<CategoryPageUrls>` element, and then specify the **locale** attribute (of type String) for each `<CategoryPageUrl>` child element. | Only if collecting Questions and Answers content at the Category level |
| `ImageUrl` or `ImageUrls`              | Unique URL for the category or subcategory image, which is usually hosted on your website or a content delivery network. When specifying a URL, be aware of the following:If the URL contains a reserved (special) character, you must [URL-encode ![img](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Resources/Images/components/external-link.png)](https://en.wikipedia.org/wiki/Percent-encoding#Percent-encoding_in_a_URI) the character. For example, use `&amp` for an ampersand, use `%20` for a space, or use `%5B` and `%5D` for square brackets ([ ]).If specifying localized categories in a multilingual implementation, include an `<ImageUrl>` element for each locale in a parent `<ImageUrls>` element, and then specify the **locale** attribute (of type String) for each `<ImageUrl>` child element.**Note: **If Conversations is deployed on an HTTPS site, you must provide image URLs at an HTTPS location in your [product catalog](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Collect/product_feed.html#). If you do not, your customers will see a mixed content warning. | Only if collecting Questions and Answers content at the Category level |

* `<Products>`

| **Element**                           | **Value**                                | **Required**                             |
| ------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| `Product`                             | Represents a product in your feed and may include other elements listed in this table.You can include the **removed="true"**attribute in the `<Product>` element to mark the product [inactive](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Collect/product_feed.html#Control).  If the product does not exist in the database and is marked inactive, it is not added to the database. | Yes                                      |
| `ExternalId`                          | Unique product ID that can contain only alphanumeric characters, hyphens (`-`), and underscores (`_`). If the external product ID contains an invalid character, replace it with an alternate character, such as an underscore. The ID is case insensitive, so you cannot use IDs that match except for case.This format is used in the data feed only and is not visible to end users. | Yes, one per product                     |
| `Name` or `Names`                     | Name or names of the product, which is visible to end users.If specifying localized product names in a multilingual implementation, include a `<Name>` element for each locale in a parent `<Names>` element, and then specify the **locale** attribute (of type String) for each `<Name>` child element. | Yes, one per locale                      |
| `Description` or `Descriptions`       | Description of the product. Bazaarvoice recommends that product descriptions be at least three sentences or 300 characters long.If specifying localized product descriptions in a multilingual implementation, include a `<Description>` element for each locale in a parent `<Descriptions>`element, and then specify the **locale**attribute (of type String) for each `<Description>` child element. | Yes, one per locale                      |
| `Brand`                               | The name of the brand to which the product belongs. You must include a `<Name>` child element, to specify the brand name.**Note: **Specify either `<Brand>`or `<BrandExternalId>` in the `<Product>` element, but do not specify both. | Yes, one per product, if `<BrandExternalId>`is not provided |
| `BrandExternalId`                     | ID of the brand to which the product belongs. Specify this element if a brand is declared as a separate element in the [``](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Collect/product_feed.html#Brands) block. The value of `<BrandExternalId>` must match a brand ID defined in the `<Brands>`block. If the `<Brands>` block is not defined in the product feed, use `<Brand>` (above) instead.**Note: **Specify either `<BrandExternalId>` or `<Brand>` in the `<Product>`element, but do not specify both. | Yes, one per product, if `<Brand>` is not provided |
| `CategoryExternalId`                  | Category or subcategory ID for the product. Specify this element if a category is declared as a separate element in the [``](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Collect/product_feed.html#Categori) block. The value of `<CategoryExternalId>`must match a category ID defined in the `<Categories>` block. If the `<Categories>` block is not defined in the product feed, use `<CategoryPath>` (below) instead.**Note: **Specify either `<CategoryExternalId>` or `<CategoryPath>` in the `<Product>` element, but you cannot specify both. | Yes, one per product                     |
| `CategoryPath`                        | A list of categories ordered by hierarchy. Each category must be specified in a `<CategoryName>` child element. You can specify multiple `<CategoryName>` child elements, each for a subcategory of the `<CategoryName>` immediately above it.**Note: **Specify either `<CategoryPath>` or `<CategoryExternalId>` in the `<Product>` element, but you cannot specify both. | Recommended, one per product             |
| `ProductPageUrl` or `ProductPageUrls` | Unique, uncorrupted URL for a product page. Do not include extraneous query string parameters that you might use for tracking and partnership codes. When specifying a URL, be aware of the following:If the URL contains a reserved (special) character, you must [URL-encode ![img](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Resources/Images/components/external-link.png)](https://en.wikipedia.org/wiki/Percent-encoding#Percent-encoding_in_a_URI) the character. For example, use `&amp` for an ampersand, use `%20` for a space, or use `%5B` and `%5D` for square brackets ([ ]).If specifying localized URLs in a multilingual implementation, include a `<ProductPageUrl>`element for each locale in a parent `<ProductPageUrls>`element, and then specify the **locale** attribute (of type String) for each `<ProductPageUrl>`child element. | Yes, one per locale                      |
| `ImageUrl` or `ImageUrls`             | Unique URL for the product image. The optimal but slightly flexible display size is 600 x 600 pixels. When specifying a URL, be aware of the following:If the URL contains a reserved (special) character, you must [URL-encode ![img](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Resources/Images/components/external-link.png)](https://en.wikipedia.org/wiki/Percent-encoding#Percent-encoding_in_a_URI) the character. For example, use `&amp` for an ampersand, use `%20` for a space, or use `%5B` and `%5D` for square brackets ([ ]).If specifying localized images in a multilingual implementation, include an `<ImageUrl>` element for each locale in a parent `<ImageUrls>` element, and then specify the **locale** attribute (of type String) for each `<ImageUrl>` child element.**Note: **If Conversations is deployed on an HTTPS site, you must provide image URLs at an HTTPS location in your [product catalog](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Collect/product_feed.html#). If you do not, your customers will see a mixed content warning. | Yes, one per locale                      |
| `ModelNumbers`                        | Unique referencing code that businesses use to identify a part that a particular industry uses. Specify a `<ModelNumber>` child element for each model number you want to define. Each model number can contain letters, numerals, and other characters. | No; if included, one per product         |
| `ManufacturerPartNumbers`             | Manufacturer-specific part number. Specify a `<ManufacturerPartNumber>` child element for each part number you want to define. Part numbers can contain letters, numerals, and characters. | Yes; you can specify an unlimited number of child elements |
| `EANs`                                | European Article Numbers (EANs), which are used worldwide for marking retail goods. Specify an `<EAN>` child element for each EAN you want to define, which must be a string of eight numerals or 13 numerals (no letters or other characters are allowed). Remove spaces and hyphens because they disrupt syndication matching.**Note:** Version 14.3+ of the schema does not enforce length or numerical constraints on EANs. Any string in this field is treated as valid by the product schema. Values are validated during the catalog import process, however, and only valid values are stored. | Either `EANs`, `UPCs`, or `ISBNs` is required.If included, you can specify an unlimited number of child elements. Syndication matching improves if you specify multiple values. |
| `UPCs`                                | Universal Product Code (UPC), which is a 6- or 12-digit bar code used for standard retail packaging in the United States. Specify a `<UPC>` child element for each UPC you want to define, which can contain numerals only, with no letters or other characters. Remove spaces and hyphens because they disrupt syndication matching.**Note:** Version 14.3+ of the schema does not enforce length or numerical constraints on UPCs. Any string in this field is treated as valid by the product schema. Values are validated during the catalog import process, however, and only valid values are stored. | Either `EANs`, `UPCs`, or `ISBNs` is required.If included, you can specify an unlimited number of child elements. Syndication matching improves if you specify multiple values. |
| `ISBNs`                               | International Standard Book Number (ISBN), which is a 10- or 13-character value used predominantly for media products such as books, music, and videos. Specify an `<ISBN>` child element for each ISBN you want to define. The last character provides a checksum that helps validate the product identifier. Most ISBNs are composed only of digits, except for some 10-character ISBN values that use an X for the checksum. | Either `EANs`, `UPCs`, or `ISBNs` is required.If included, you can specify an unlimited number of child elements. Syndication matching improves if you specify multiple values. |
| `Attributes`                          | Custom attributes that enable you to define additional product-specific information, to [report on product-specific information](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Collect/product_feed.html#custom-product-attributes) or to [support product families](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Collect/product_feed.html#share-reviews-using-product-families). Specify an `<Attribute>` child element for each product attribute you want to define. Be sure to include the name of the product attribute using the **id** attribute of the `<Attribute>` element; spaces are not permitted in the attribute ID. | No; if included, you can specify an unlimited number of child elements |

## Validate

First, check that it works with the [Bazaarvoice XML schema](http://release-assets.bazaarvoice.com/xs/PRR/ProductFeed/14.7). You can do this using an online tool like  [CoreFiling](http://www.corefiling.com/opensource/schemaValidate.html).

1. Save the [Bazaarvoice XML schema ![img](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Resources/Images/components/external-link.png)](http://release-assets.bazaarvoice.com/xs/PRR/ProductFeed/14.7) as an XML file.
2. Choose the Bazaarvoice Schema XML file for the XML schema.
3. Choose your XML file for the XML Instance.
4. Click Validate.



## Upload

An updated product feed should be uploaded whenever changed are made to the product catalog. This is done by uploading the XML feed file to the `/import-inbox` directory of the SFTP server

If your data is hosted in the US, use the following URLs on port 22:

- Staging server—*sftp-stg.bazaarvoice.com*
- Production server—*sftp.bazaarvoice.com*

After you upload a product feed to an SFTP server, Bazaarvoice automatically begins importing the feed at 2 AM Central Time (CST: UTC-6 or CDT: UTC-5), although Bazaarvoice may not finish importing your feed until later the same day due to the import process.

If you uploaded the feed to a *staging server*, you can trigger an import manually. (You cannot manually trigger an import to the production server.) Complete the following steps to manually import the feed:

1. From the Bazaarvoice Workbench of the [staging server ![img](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Resources/Images/components/external-link.png)](https://workbench-staging.bazaarvoice.com/), select **Settings » Validate Product Feed**.
2. Click **Schedule one-time import** to manually import the feed.

## Check Feed Status

You can view the import summary, which lists errors and warnings.

View the import summary in the [staging Workbench ![img](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Resources/Images/components/external-link.png)](https://workbench-staging.bazaarvoice.com/) or [production Workbench ![img](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Resources/Images/components/external-link.png)](https://workbench.bazaarvoice.com/) by selecting **Settings » Validate Product Feed**. If your feed returns an error or warning, click it to get detailed information.

- Maybe we should create a test that checks that the XML file is good before upload. A unit test?



# Questions

- Is External ID designated by BazaarVoice or can it be whatever?
- Can it be the sku number again?
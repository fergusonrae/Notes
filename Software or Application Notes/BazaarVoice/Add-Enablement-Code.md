# Overview

**CITE**: https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Display/display_integration.html#add-bazaarvoice-code-to-your-website

# Steps

1. Add the BV loader in the `<head>` tag of the page

   1. ```html
      <script async src="https://apps.bazaarvoice.com/deployments/<client_name>/<site_ID>/<environment>/<locale>/bv.js"></script>
      ```

   2. *<client_name>*— The client name provided by Bazaarvoice. Be sure to use lowercase letters for the value.

   3. *<site_ID>*—The ID of the [deployment zone](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Learn/config_hub_overview.html#Deployme) you want to use. This is set in the Bazaarvoice configuration hub within the Bazaarvoice Workbench. The default deployment zone is “main_site”. Check with your Bazaarvoice representative to ensure the correct ID, or click ![img](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Collect/Images/zone_id.PNG) to the right of the deployment zone on the Site Manager page of the configuration hub.

   4. *<environment>*—The deployment environment where you want to implement Bazaarvoice features. For a production environment, include **production** in the path. If you are referencing a staging environment, include **staging** in the path.

   5. *<locale>*—The [locale](https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Learn/localization.html#supported-locales-and-languages) that is used by the implementation. For example, en_US for English.

2. Add display modules for the CGC features

   1. Add code to the `<body>` where CGC features should be displayed.

      * **Reating summary** - Position this as close to the product name and image as possible.

        * ```html
          <div data-bv-show="rating_summary" data-bv-productId="ExternalId"></div>
          ```

        * The ID must match the ExternalId in the product catalog and should be replaced with it

      * **Reviews**

        * ```html
          <div data-bv-show="reviews" data-bv-productId="ExternalId"></div>
          ```

      * **Review highlights**

        * But this towards the top of the page for the largest impact

        * ```html
          <div data-bv-show="review_highlights" data-bv-productId="ExternalId"></div>
          ```

      * **Questions**

        * ```html
          <div data-bv-show="questions" data-bv-productId="ExternalId"></div>
          ```

3. Make sure product schema is in use.

   * Currently is for sentry safe.com
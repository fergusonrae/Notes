# Overview

A container page is a generic HTML doc that Bazaarvoice uses to create dedicated submission pages that are hosted on your website. It's a container for submission forms. Mobile submission requests are always directed to a container page, you can decide whether non-mobile submission requests open on a container page or a lightboc

**CITE:** https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Collect/container_page.html

# Create and Host Container Page

Bazaarvoice has a generic container page for mobile requests, but it has a Bazaarvoice url. If you don't want that, do the following:

1. Create a blank HTML doc and add only the following code

   1. ```html
      <!DOCTYPE html>
      <html>
        <head>
          <meta charset="utf-8"/>
          <title></title>
          <meta name="robots" content="noindex, nofollow">
          <link rel="canonical" href="container.htm"/>
        </head>
        <body>
          <script type="text/javascript" src="https://display.ugc.bazaarvoice.com/bvstaging/static/<client_name>/<site_ID>/<locale>/bvapi.js"></script>
          <script>
            $BV.container('global', {} );
          </script>
        </body>
      </html>
      ```

2. In the `<link>` element, replace the red with the relative URL that will host the container page.

3. In the `<script>` element, replace:

   1. `<client_name>` - Client name provided by BV. Use lowercase letters
   2. `<site_ID>` - ID of the deployment zone you want to use. This is set in BV config hub within Workbench. The default is "main_site"
   3. `<locale>` - If you're not using US English, use the correct locale code

4. Reference the correct environment for these steps:

   1. Add the HTML doc to the domain integrated with BV code
   2. In the **Getting Started** section of the Conversations config hub, click **Technical Setup**. From the **Site Profile** page, scroll to the **Hosts and URLs** section and enter the container page URL in the **Container URL** text box.
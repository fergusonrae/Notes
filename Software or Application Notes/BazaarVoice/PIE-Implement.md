# PIE Implementation

**PIE** - Post-Interaction Email

This will be sent out when a consumer purchases one of our products, but does not leave a review or feedback.

**CITE/Further info:** https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Collect/pie.html

## Prerequisites

To send a PIE you need:

* product ID
  * This is the same as the product's ExternalId in the product catalog

## Workflow and Timing

1. Customer completes a transaction
2. Transaction record is generated within your database and sent to Bazaarvoice in a PIE feed
3. BazaarVoice determines:
   1. Whether the customer has submitted an approved review for 1+ past products or if products were purchased > 180 days ago. If so, reviewed products are not included in PIE message.
4. PIE is sent to custoemr
   1. Is generally 14-21 days after transaction
   2. The amount of days to wait is customizable.
5. Customer recieves PIE and then:
   1. Submits a review
      1. Woo!
      2. If they go to submit a review after 30 days, it is no longer pre-authenticated and they are no longer considered a verified purchaser. But, they can still submit.
   2. Does not submit a review
      1. Boo. Follow up message is sent after they complete another transaction or it's been a bit. This delay between messages is also customizable.
6. Each review is published on site if it passes the mods

## Setup Overview

### Required

1. Enable PIE
2. Determine how transaction data will be sent
   1. Maintenance free
      1. Works with BV Pixel to collect encrypted transaction and interaction data direct from site. You add BV Pixel events to any page element on the site.
   2. Feed-based
      1. You upload an XML file to Bazaarvoice with transactions to use in PIE messages
      2. This is used if PV Pixel is not enabled on your site or you want to import historical data or offline purchases like in-store
   3. Test

### Optional

* Configure email templates
* Track PIE performance
* Manage consumer email subscriptions
* Configure submission form questions



### Enable PIE

1. Login to Bazaarvoice Workbench and click **Settings > Manage Application**
2. Edit the implementation where you want to configure the PIE feature
   1. In order to integrate Bazaarvoice, you have to first set up staging and production environments in the configuration hub
   2. Here **implementations** define how BV features display and the **deployment zones** define which sites/pages the implementations apply to.



TO BE CONTINUED
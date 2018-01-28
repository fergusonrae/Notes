# What is it?
A "suite of applications". Cloud-based, user-generated content engine.

# Products

### Conversations

Captures and shares people's review, questions, and experiences regarding your company.

* Rating and Reviews
  * Like Amazon, share number of stars and images
* Campaigns/Spot Light
  * More indepth
  * Good for SEO
* Q + A
  * Like Amazon Q + A
  * Brings it to your site for ease of reply to customers and a sense of transparency
* Sampling
  * Optional
  * Participants receive products to review so you have reviews ready to go when you release your product.
  * These reviews can also be shared across the netowrk to retailer sites that carry the product.
  * Has its own branded portal

Syncs to Facebook and other retailers. Can increase ability to be seen on sites like Walmart and such. Is shared between all of these companies so your reviews for you.

Has an analytics plug-in with real-time social data analysis.

### Connections

Leading retailers allow Q+As and review interaction between products and the company that makes the company.

You're alerted in a dashboard for response for all sites your product and bazaarvoice is on. Your correspondance is displayed on that same page.

Premium - Tells you when you get a bad review, gives a "branded response", filters reponse by level of importance

### Curations

Used to leverage social media. Takes content from a wide variety of social platforms. You then organize the media that match your filter preferences in the portal. So, no need to send visitors off site to show user-generated content

Filters are so only on-brand content is approved for display. Can filter out curse words and mentions of other competitors

### Advertising

Uses first-party data to find shoppers in-market for products. Using data they have gathered, can run turnkey ad campaigns for specific KPI. Has about 5000 brands and retailers

**turnkey** - already completed, good as is. Weird word to put here?

### Brand Edge

? Not sure what thi is? Page just lists what the other product do. Maybe it's selling the package of all products?



# Implementation

SS is going with Conversations.

**CGC** - consumer-generated content

**PIE** - Post-Integration Email

**PDP** - product display page

**Link to documentation** - https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/implementation.html

### 1. Initial tech setup

1. Provide product catalog
   * Can do single or multiple feeds
     * Single: all of your catalog data in one file. Most reliable way.
     * Multiple: If catlog data is sourced in different systems. Need to contact Client Care before attempting
   * File formats
     * XML
     * Text
2. Create a container page
   * A container is a generic HTML doc that is used to create dedicated submission pages. The pages act as containers for submission forms. You can choose whether non-mobile requests go to a container page or a lightbox on the PDP.
3. Enable the BV Pixel
   * BV Pixel is a way to prove ROI.
   * Tracks user behavior to gather analytics.
   * Is added to conversion pages, "Thank you" pages or any pages after a user reaches their desired content. Like a GA script
   * Works with host to track hovering, scrolling through. More than GA.
4. Integrate code to display content
5. Add schema.org markup
   * Note: pages can only contain one schema.org type
6. Request reviews with PIE
   * After a person buys something, an email is prompted to them asking for a review. Does not send messages to products previously reviewed.
7. Add inline ratings
8. Optomize SEO



# Questions for Call

1. Do we have a certain number of support hours? Cost?
   1. We have 72 hours




# General Order of Implementation steps

1. Configure product feed
2. Create a container page
3. Add enablement code to your site
4. Add BV Pixel to your site
5. Configure email templates
6. Enable Post-Interaction Email (PIE)

**CITE:** https://knowledge.bazaarvoice.com/wp-content/conversations/en_US/Learn/config_hub_overview.html#technical-setup


# The Meeting

- Only US
- 90 days and 74 hours of support
- Ben is the technical
- They do an initial QA before completely handing it over
- Automated feed, can do it once per day
- Standard display on product detail pages
- They use Basecamp for interacting with people
  - Has a to-do list
  - Tasks can be assigned, like Jira
- Ben will have access to the review site
- Whitelist bazaarvoice
- Discovery call - what questions?
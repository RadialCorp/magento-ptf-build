[![Radial Logo](assets/radial_logo.png)](http://www.radial.com/)

# Radial Magento Payments Tax Fraud Extension 

## Note about Ship Methods

Radial's Fraud Engine needs to understand what ship methods are being used in a storefront to provide accurate fraud assessments (i.e. Next Day Air, Ground, etc...) as this information is passed back to Radial.  Please coordinate with your Radial team to ensure that Radial has a correct understanding of what ship methods are being used for your storefront.

## Sign Up for Radial API Access

For access to Radial API's, please see [Radial.com](http://www.radial.com/) for more information...

## Order Management and Fraud

Rolling out Radial Fraud processing involves making some important modifications to order fulfillment.  In a traditional model, orders are received and filled; Radial fraud processing sits in the middle of order received and order fulfillment to provide a recommendation on whether an order is fraudulent before filling.  Now, orders are received, fraud evaluated, and filled if fraud approved, which means that the fulfillment process needs to understand when fraud evaluation is completed - to accomplish this, the Radial Fraud extension introduces some new order statuses to reflect different stages of processing.  

New order statuses include (with their Magento order status codes and descriptions of meaning):

- Fraud Accepted ('risk_accept'): Order has been evaluated and determined to be non-fraudulent
- Order Submitted to Fraud System ('risk_submitted'): Order data has been submitted to the Radial fraud engine for evaluation
- Order Under Review for Fraud Detection ('risk_processing'): Order is currently under review
- Fraud Cancelled ('risk_cancel'): Order has been determined to be fraudulent and should be canceled.  
- Fraud Ignore ('risk_ignore'): Fraud engine is ignoring the order due to setup on Radial side
- Fraud Suspend ('risk_suspend'): Order is undergoing extended evaluation 
- Fraud Reject Pending('risk_rejectpending'): Indicating that there is a high likelihood of imminent rejection of the order

In the end, each order state is a *recommendation* for handing the order (with the exception of Fraud Cancels which literally cancels the order in Magento) - business needs can override the processing and fill the order if and when needed.  Each storefront has to adopt a process around how it handles each status in fraud processing.  This often entails:

1. Updating feeds jobs which send order data to a fulfillment center which might currently send everything based on payment authorization, but now may want to wait for a risk_accept status to come in.
2. Train internal staff responsible for fulfilling orders to ensure that they adhere to the process and only fulfill orders in these newer statuses.

Work with your Magento SI to adjust any feeds / cron jobs which base themselves off of order status so that they only pick up orders in an appropriate/desired state

## Next Docs

[Main](../README.md)

[Installation And Upgrading](INSTALL.md)

[Setup and Configuration](SETUP.md)

[Troubleshooting](SUPPORT.md)


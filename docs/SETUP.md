[![Radial Logo](assets/radial_logo.png)](http://www.radial.com/)

# Radial Magento Payments Tax Fraud Extension 

## Contents
  * [Admin Console Setup and Configuration](#admin-console-setup-and-configuration)
  * [Enabling Credit Card Processing](#enabling-credit-card-processing)
  * [Enabling PayPal Processing](#enabling-paypal-processing)
  * [Enabling Fraud Processing](#enabling-fraud-processing)
  * [Disabling Radial Payment Methods and Fraud Processing](#disabling-radial-payment-methods-and-fraud-processing)

## Admin Console Setup and Configuration

The Radial PTF extension does not function unless it is a) configured and b) linked to an active account for accessing Radial's Public API's.  These first three steps are required before anything can be done to enable/activate payment, tax, or fraud processing at Radial.

Step 1 - Rename the app/etc/rom.xml.sample file to rom.xml - make sure you clear any caches running on the store.  See [Integrators Guide](SI.md) for other potential edits needed to this file. 

Step 2 - Log into Admin > System > Configuration > Radial - Payments, Tax, Fraud

Step 3 - Your Radial Technical contact will provide you with the information needed to complete these fields

<img src="assets/magento-admin-ptf.png">

Please be sure to test API and AMQP connectivity before proceeding to any other steps.  If this connectivity is not working, that must be resolved before anything else is done.

Assuming all fields and entered and the connectivity test buttons work correctly, save the configuration and, if applicable, clear cache.  

## Enabling Credit Card Processing

To start using Radial Credit Card Processing as an active Payment Method in Magento - go to Admin > System > Configuration > Payment Methods select the eBay Enterprise Credit Card header and set Enabled to Yes

<img src="assets/payment_method.png">

Some other settings of note:

- Title: What appears on the checkout payments page describing this payment option
- Payment from Applicable Countries: if this payment method is allowed from only certain countries, change "All Allowed Countries" to "Specific Countries" and then select the desired countries from the list below.
- Use Client Side Encryption: If client side encryption is being used, set Use Client Side Encryption to "Yes" - this will make a new field appear to input the encryption key - please note that Radial must provide this encryption key.  

Once done, click Save Config and, if necessary, clear cache.

## Enabling PayPal Processing

To start using Radial PayPal Processing as an active Payment Method in Magento - go to Admin > System > Configuration > Payment Methods select the eBay Enterprise PayPal header and set Enabled to Yes

<img src="assets/payment_method_paypal.png">

Some other settings of note:

- Title: What appears on the checkout payments page describing this payment option
- Payment from Applicable Countries: if this payment method is allowed from only certain countries, change "All Allowed Countries" to "Specific Countries" and then select the desired countries from the list below.
- Sandbox Mode: Should be set to "Yes" for any non-production environments to prevent actual transaction processing at PayPal (i.e. developer Sandboxes, testing systems, etc...); should be set to "No" for live storefronts that need to conduct real PayPal transactions.
- Shortcut On Shopping Cart: Enables an option on the cart page to finish checkout via PayPal
- Shortcut on Product Page: Enables an option on the product page to finish checkout via PayPal 

## Enabling Fraud Processing

Go to System > Configuration > Radial - Payments, Tax, Fraud and select the Fraud tab and set "Enabled" to Yes.

<img src="assets/magento-admin-ptf-fraud.png">


Some other settings of note:

- Fraud Files Installed?: this is a sanity-check report to ensure that Radial's needed JavaScript files are actually loaded on the deployed-to server
- Debug Mode: Should be set to "No" at all times and only set to "Yes" if one is actively debugging fraud integration with Radial.  Turning this on will send much of the fraud messaging to the store's system.log.

In order for the storefront to receive fraud evaluations from Radial, please ensure that Cron is running on your Magento installation and set a schedule for the ebayenterprise_amqp_runner_process_queues job - this is the job which reads the fraud service responses that help determine which orders to fill / not fill - it is recommended that this cron mask be set to run no more than every 5 minutes (the default setting) to ensure timely processing of orders (most fraud determinations are made in well under 5 minutes).

Please remember to cache-clear after setting up data in Magento admin...

## Disabling Radial Payment Methods and Fraud Processing

If there is a need to temporarily disable Radial Payment and/or Fraud processing, both can be shut off via Magento Admin using the below steps.  Please note: If Radial Credit Card and PayPal are disabled, another payment method will need to be enabled otherwise the storefront will have no configured means of paying for an order and customers will not be able to checkout.

To stop using Radial Credit Card Processing as an active Payment Method in Magento - go to Admin > System > Configuration > Payment Methods select the eBay Enterprise Credit Card header and set Enabled to No.  Save and clear cache.

To stop using Radial PayPal Processing as an active Payment Method in Magento - go to Admin > System > Configuration > Payment Methods select the eBay Enterprise PayPal header and set Enabled to No.  Save and clear cache.

To disable Radial Fraud Processing, go to System > Configuration > Radial - Payments, Tax, Fraud and select the Fraud tab and set "Enabled" to No.  Save and clear cache.

## Next Docs

[Main](../README.md)

[Installation And Upgrading](INSTALL.md)

[Integrators Guide](SI.md)

[Troubleshooting](SUPPORT.md)

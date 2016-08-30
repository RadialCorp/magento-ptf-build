[![Radial Logo](assets/radial_logo.png)](http://www.radial.com/)

# Radial Magento Payments Tax Fraud Extension 

## Contents
  * [Enabling Credit Card Processing](#enabling-credit-card-processing)
  * [Enabling PayPal Processing](#enabling-paypal-processing)

## General Payments Settings

<img src="assets/payments_tab.png">


## Enabling Credit Card Processing

To start using Radial Credit Card Processing as an active Payment Method in Magento - go to Admin > System > Configuration > Payment Methods select the eBay Enterprise Credit Card header and set Enabled to Yes

<img src="assets/radial_credit_card.png">

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

## Next Docs

[Main](../README.md)

[Installation And Upgrading](INSTALL.md)

[Integrators Guide](SI.md)

[Troubleshooting](SUPPORT.md)

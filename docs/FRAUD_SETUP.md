[![Radial Logo](assets/radial_logo.png)](http://www.radial.com/)

# Radial Magento Payments Tax Fraud Extension 

## Contents
  * [Enabling Fraud Processing](#enabling-fraud-processing)
  * [Recommended Reports](#recommended_reports)

## Enabling Fraud Processing

Go to System > Configuration > Radial - Payments, Tax, Fraud and select the Fraud tab and set "Enabled" to Yes.

<img src="assets/fraud_tab.png">


Some other settings of note:

- Fraud Files Installed?: this is a sanity-check report to ensure that Radial's needed JavaScript files are actually loaded on the deployed-to server
- Debug Mode: Should be set to "No" at all times and only set to "Yes" if one is actively debugging fraud integration with Radial.  Turning this on will send much of the fraud messaging to the store's system.log.

## Recommended Reports

Since fraud processing can be an integral part of the order fulfillment lifecycle, it is important to check on its health from time to time.  The easiest way to do this is via existing Admin by going to Sales > Orders > and then defining some filter characteristics - in the below example, a date range of several days ago was provided filtered on the order status "Fraud Suspended" to see if there are orders lingering too long in a processing state.  

<img src="assets/fraud_suspend_report.png">


## Next Docs

[Main](../README.md)

[Installation And Upgrading](INSTALL.md)

[Integrators Guide](SI.md)

[Troubleshooting](SUPPORT.md)

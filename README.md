# mantle-shipit

   Integration with Shippit for shipping rates, labels, and create orders.
   In this Integration we worked on staging environment. So, the rates may vary from production evironment.

To use simply:
1. Load the setup data in data/ShippitSetupData.xml
2. Load the demo configuration data in data/ShippitZaaDemoData.xml or create your own configuration and load it; if you use the demo data, add your API token (SgoApiToken option).

~ get#ShippingRates service: 
   This rate API will fetch rates of a Shipment from Shippit.

~ create#Order service: 
   This create order API will create order of a particular shipment.

~ create#ShippingLabel service :
   This create label API will create Label of order from order ID.

~ void#ShippingLabel service:
   This cancel order API will cancel the order and also voids the label.
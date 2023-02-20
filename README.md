# mantle-shipit

Integration with Shippit for shipping rates, labels, and create orders.

To add this component to Moqui the easiest approach is to use the Gradle get component task:

To use simply:

1. Load the setup data in data/ShippitSetupData.xml
2. Load the demo configuration data in data/ShippitZaaDemoData.xml or create your own configuration and load it; if you use the demo data, add your API token (SgoApiToken option).

Note:    
   In this Integrations, Shippit create order service works only for (ACT, NSW, NT, QLD, SA, TAS, VIC, WA) states only.
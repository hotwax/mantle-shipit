# mantle-shipit

   Integration with Shippit for shipping rates, labels, and create orders.
   In this Integration we worked on staging environment. So, the rates may vary from production evironment.

To use simply:
1. Load the setup data in data/ShippitSetupData.xml
2. Load the demo configuration data in data/ShippitZaaDemoData.xml or create your own configuration and load it; if you use the demo data, add your API token (SgoApiToken option).

~ post#ShippingRates service: 
   API path: https://app.staging.shippit.com/api/3/quotes
   The Quote API will return a quote given a destination location and parcel attributes.
   At minimum, a Quote requires a delivery location and information on the parcels being delivered. However, different couriers and delivery methods can require additional fields to satisfy their requirements. There is a maximum of 1000 parcels per quote request.

~ post#CreateOrder service: 
   API path: https://app.staging.shippit.com/api/3/orders
   At minimum, an Order requires a delivery location, user details, and parcel details. Shippit will then generate the order, allocate the courier, and fill in the origin location based on the provided info and merchant configuration on Shippit.
   Note that the required fields for an Order can vary depending on the type of order, the requested courier, whether it is local or international, etcetera.
   There are only selected states available now for deliveries are ACT, NSW, NT, QLD, SA, TAS, VIC, WA.
   In response this API call returns a tracking number with which we can generate a label or cancel our order. 

~ get#CreateLabel service :
   API path: https://app.staging.shippit.com/api/3/orders/{tracking_number}/label
   The label API will return a URL to a label for an order.
   Retrieves labelling information for an Order using the tracking number.
   The labelling information for an Order can only be retrieved once the Order has been processed and allocated a courier, which may take some time after the Order has been placed. If the Order is yet to be processed, you will get a 422 Unprocessable response.

~ delete#CancelOrder service:
   API path: https://app.staging.shippit.com/api/3/orders/{tracking_number}
   Cancels an Order in Shippit using the tracking number.
   The API first checks if the Order can be cancelled, ie., if its current state allows it, then returns an immediate response. If the Order is successfully cancelled, the API will answer with the Order with its state updated as cancelled. If it cannot be cancelled, it will throw a 422 error.

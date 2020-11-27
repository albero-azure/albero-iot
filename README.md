# albero-iot
## Solutions Gallery Case for Industrial IoT and beyond

In this scenario, you are building an Industrial IoT analytics solution for a manufacturer to provide overall equipment effectiveness (OEE) and predictive maintenance insights to the plant manager, the process engineer, and the data scientists. Such an IIoT analytics solution relies on real-time and historical data from industrial devices and control systems located in discrete and process manufacturing facilities. We need to keep in mind that there are diverse platforms to connect, then standardize the data into a common, open format. 
To decide what services will back it up, we will analyze the write and read profiles. 

__For the write pattern:__ 

*	We are expecting streaming data from the devices in an append mainly manner. *throughput/sec ?*
* We are also ingesting data in batches *business reason? different devices? can we have both streaming and batch?*
*	Capability to manage the devices centrally to update the firmware, reboot, or configure the desired state. 
*	Generate notifications in the event of detecting a warning condition.

This bi-directional connectivity from the device to cloud and from cloud to the device shows us that we will need IoT Hub for the ingestion of the data. To generate notifications, we will need a streaming analytics block that will process the data in time windows and an Azure service bus that will produce messages to trigger the notifications.

__Read pattern:__ 

*	Different APIs for the different personas – PowerBI, REST API, spark
*	Warm and cold analytics support
*	Highly interactive warm analytics to perform frequent and large number of queries over short time span
*	Views for daily, weekly and monthly reports
*	Support of different asset hierarchy that describes the domain and metadata associated with the raw signals from the assets and devices.

The above leads us to consider Time Series Insights as the persistent storage. Although we land in different services for the write and read profile, we see at the Albero that the integration of those is supported natively. 


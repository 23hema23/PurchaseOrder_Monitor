# PurchaseOrder_Monitor
ABAP Cloud project for monitoring Purchase Orders. In this project a background job monitors data in Purchase order header and Purchase order Item tables and pushes filtered records into a monitoring table based on parameters given. Monitoring data is then exposed as a service to Fiori UI and also as API which can be consumed by a data consumber.  

**Tables**
1. ZEKKO : holds purchase order details.
2. ZEKPO : holds purchase order item details for a given purchase order.
3. ZPO_MONITOR : holds Purchase order number and Purchase order item number information of monitored data.
 
**Background job**
There is a background job(PO Monitor) to filter records based on parameters set and put them into ZPO_MONITOR table. Parameters for this job are:

1. S_PAYTER : this parameter holds information about payment terms ( in number of days). Background Job will filter out records mathing this value in range and pushes records into a ZPO_MONITOR table.
2. S_PO_CRE : this parameter holds information about creation days. Which helps to identify PO records created in past x days. Background Job will filter out records mathing this value in range and pushes records into ZPO_MONITOR table.

**Classes**
1. zcl_temp_fill_ekko : this class fills dummy data in ZEKKO table
2. zcl_temp_fill_zepko : this class fills dummy data in ZEPKO table
3. zcl_po_monitor_job : class for PO monitor job
4. zcl_po_monitor_scheduler : class to schedule PO monitor job
 
**Business service**
1. OData V4 - UI business service is created to be consumed at ui side.
2. OData V4 - Web API is created to expose data outside.


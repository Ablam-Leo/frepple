====================
Manufacturing orders
====================

This table contains the manufacturing orders of your supply chain, either proposed by frePPLe or confirmed.

**Fields**

================ ================= =================================================================================================================================
Field            Type              Description
================ ================= =================================================================================================================================
operation        operation         The operation to perform.
start date       DateTime          The date when the operation is starting.
end date         DateTime          The date when the operation is ending.
quantity         number            The manufactured quantity.
status           non-empty string  | This field should have one of the following keywords :
                                   | proposed : The manufacturing order is proposed by frePPLe to meet the plan (optimization output).
                                   | approved : The manufacturing order is present in the ERP system but can still be rescheduled by frePPLe (optimization input).
                                   | confirmed : The manufacturing order is confirmed, it has been populated in your ERP system (optimization input).
                                   | closed : The manufacturing order has been completed.
Demands          demand            The demand(s) (and quantity) pegged to the manufacturing order. This is a generated field.
Owner            number            In the case of a suboperation, the identifier of the operation calling this suboperation.
Inventory Status Number            | The Inventory Status is a calculated field that highlights the urgency of the manufacturing order.
                                   | The cells have a background color that can be green, orange or red. Sorting 
                                   | the manufacturing orders using the Inventory Status column (red ones first) allows the planner to 
                                   | immediately focus on the manufacturing orders that should be treated first. 
criticality      number            | The criticality is a read-only field, calculated by the planning engine. 
                                   | It represents an indication of the slack time in the usage of the manufacturing order.
                                   | A criticality of 0 indicates that the manufacturing order is on the critical path of one or more demands.
                                   | Higher criticality values indicate a delay of the manufacturing order will not immediately impact the shipment of any demand.                                   
                                   | A criticality of 999 indicates a manufacturing order that isn’t used at all to meet any demand.
                                   | Note that the criticality is independent of whether the customer demand will be shipped on time or not.
delay            Duration          | The delay is a read-only field, calculated by the planning engine.
                                   | It compares the end data of the manufacturing order with the latest possible end date to ship all demands it feeds on time.
================ ================= =================================================================================================================================                            
                                  

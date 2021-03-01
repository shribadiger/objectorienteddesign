# Object Oriented Design #
#### Initial Approach to Design Problem ####
1. Collect the complete requirement, ask for clarification if any of requirement statement is not clear. Identify the corner cases which stops to design entry points.
2. Understand the System Expectation and Usecases which are involved in the problem statement. Make out the usecases flow and expectation of each usecase.
3. Identify the Key Object which required to solve each usecases.
4. Prepare the list of operations which associated with Object intended to do. 
5. Prepare the list of flows required between the Objects. Inter-communication between the Objects and make the usecases to meet the end requirement. 
6. Finally validates about the proposed design handle the SOLID principles. 

#### Some Design Solutions: Example-Online Shopping Portal ####
We are using the online shoping portal to purchanges a product, but when the design comes to picture. 
Usually will start with Login/Logout/User profile/Product View and some process related to Orders.

But following points are essential to consider in the design process
1) How to search the products and relationship of the product search operations - Discoverability
2) After Identifying the product, How to load into CART and CHECKOUT options ( Creative Way - Different Approach than current online portal)  - One_Click_Approach
3) Some Secure Payment Options providing - Security features need to consider the basic design
4) Feedfack and rating feature need to consider- Invidual Product rating and feedback details. - Usability of the available features.

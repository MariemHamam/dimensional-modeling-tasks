# dimensional-modeling-tasks
# Dimensional Modeling Tasks

## Case Study 1: Retail Company (Restaurant)

**Step 1 - Business process:** Sales

**Step 2 - Grain:** One row = one product sold in one invoice.

**Step 3 - Dimensions:**
- Date_Dim: Date_Key (PK), Day, Month, Quarter, Year
- Branch_Dim: Branch_Key (PK), Region, Governorate, Branch_Name
- Product_Dim: Product_Key (PK), Product_Name, Category, Type
- Emp_Dim: Emp_Key (PK), Waiter_Name

**Step 4 - Facts (Fact_Sales):**
- Cost, Revenue, Sales_Qty
- Sale_Type (Delivery / Dine-in / Take-away) is kept in the fact table as a degenerate dimension because it has only 3 values.

**Schema type:** Star Schema

**Notes:**
- Product variety = COUNT(DISTINCT Product_Key)
- HR head-count = COUNT(DISTINCT Emp_Key) per branch

---

## Case Study 2: Real Estate Agency

**Step 1 - Business process:** Agency activity (Sale, Rent, Visit)

**Step 2 - Grain:** One row = one activity (sale, rent or visit) on one estate, with one customer and one agent.

**Step 3 - Dimensions:**
- Date_Dim: Date_Key (PK), Day, Month, Quarter, Year
- Estate_Dim: Estate_Key (PK), Category, Area, City, Province, Rooms, Bedrooms, Garage, Meters, Owner info
- Agent_Dim: Agent_Key (PK), Name, Surname, Office, Address, City, Phone
- Customer_Dim: Customer_Key (PK), Name, Surname, Budget, Address, City, Phone
- Activity_Type_Dim: Activity_Type_Key (PK), Activity_Type (Sale / Rent / Visit)

**Step 4 - Facts (Fact_Activity):**
- Price (for sale and rent)
- Duration (for visits)
- Status

**Schema type:** Star Schema

**Supervisor view:** The supervisor can analyze the estates the agency deals with (Estate_Dim) and the agents' work (Agent_Dim) over time (Date_Dim).

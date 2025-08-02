# businessproblem_task4
import pulp

# 1. Initialize Model
prob = pulp.LpProblem("Production_Optimization", pulp.LpMaximize)

# 2. Define Decision Variables
x_A = pulp.LpVariable("Product_A_Quantity", lowBound=0, cat='Continuous')
x_B = pulp.LpVariable("Product_B_Quantity", lowBound=0, cat='Continuous')

# 3. Define Objective Function (Maximize Profit)
prob += 3 * x_A + 5 * x_B, "Total_Profit" # Example profits

# 4. Define the Constraints
prob += 2 * x_A + 4 * x_B <= 100, "Raw_Material_Constraint" # Example raw material usage and availability
prob += 3 * x_A + 2 * x_B <= 80, "Labor_Constraint"      # Example labor usage and availability

# 5. Solve Model
prob.solve()

# Print results
print(f"Status: {pulp.LpStatus[prob.status]}")
print(f"Optimal Production of Product A: {pulp.value(x_A)}")
print(f"Optimal Production of Product B: {pulp.value(x_B)}")
print(f"Maximum Total Profit: {pulp.value(prob.objective)}")

"# Data_Modelling" 
=============================
The schema has 4 dimensions feeding into 1 fact table:
DimCustomers — 7 unique customers, keyed by DimCustomersKey (surrogate INT generated via ROW_NUMBER())
DimProducts — 9 products (Electronics + Accessories), with DimProductsKey as surrogate
DimRegion — 8 rows at country-level grain (e.g. North America → USA, Canada separately), keyed by DimRegionKey
DimDate — 10 distinct order dates, keyed by DimDateKey
FactSales — holds the 4 measures (OrderID, Quantity, UnitPrice, TotalAmount) plus all 4 foreign keys pointing to each dimension. Populated via a 4-way LEFT JOIN on trans_sales.
The pipeline at the bottom shows the full flow — sales_new.orders → stg_sales (raw copy) → trans_sales (filtered: Quantity IS NOT NULL) → views → dimension tables → FactSales.
You can click any table in the diagram to dive deeper into it!

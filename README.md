<img width="1305" height="358" alt="Screenshot 2026-08-21 214630" src="https://github.com/user-attachments/assets/6ef29406-5fc9-46c8-a74e-db849fbc850a" />

the source data are divided into 3 sources 
first is excel fine which contain dimension product table 
second is access database which have the location discount table 
third one is csv file which is the fact table where each event is a certain event recorded with date 

Thanks to Mike Grivin for providing this data 
Link to Data 
https://excelisfun.net/files/PowerQuery02Files.zip

First Phase:-
Data importing and cleaning 

we need to import the three tables 
location discount table a.k.a dim_location discount table it contains the sales channel and discount 
but there was problem with this file location store was recorded as store and in other tables was In store so we needed to replace values using power query from Store to In Store 

We needed to split columns in the fact_sales table into to columns to get product_id table and sales_channel table 

Also we needed to convert iso date column into date column in the fact_sales table 

Second Phase:-
merging the tables (joining)

fact_sales with dim_product using left join and product_id as forign key from first table and primary key from second table 

second join fact_sales with dim_locationdiscount table using sales location column as merging key between two tables 


third Phase:- 

calculations 
now we have all information we need in the fact table all we need is to calculate units, price and discount percent 
we won't use dax or worksheet calculation but we will use Power Query calculation with this amazing PQ formula 
Net Sales = Units*price*(1-DiscountPercent) then we round the values

we removed unwanted columns and kept the ones we need 

Visualization 

<img width="1920" height="1020" alt="Screenshot 2026-08-21 214700" src="https://github.com/user-attachments/assets/33868da8-9101-4c53-9eeb-670453f468ef" />

we made pivot table and we put product name or boomerang in rows 
and net sales in values 
and sales locations into columns 

as we see from the visualization products Majestic and Quads have the highest Sales where sales from web site are is top sold category 



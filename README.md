# Data engineering tasks (Decathlon).
## Task 1. Vacations.
HR department asked you to acquire Employees absense data for analysis.

They need it in the following format:
employee,type_of_absence,start_date,end_date,duration

You were given access to Employees data via an API and was able
to acquire records of employees absence (Vacations or Business trips).

[API data](task1_data/response.data)

Every record holds all the necessary data:
- user
- type of absence
- start date
- end date

You need to process this data and give it back to HR deparment in CSV format.

A code written in Python 3.x is expected.

### Additional challenges.
* Suppose we can have multiple types of absense.
* Some records can cover same periods. Think of the way to split them and put it in the code.

---

## Task 2. BigQuery.
Please, explore the following documentation for BigQuery Pricing:

[On demand pricing](https://cloud.google.com/bigquery/pricing#on_demand_pricing)

Suppose we have 4 tables and 1 view on hand:
* a table: data_per_fam - huge, approx. 20000 records per day, 6 Gb of data

Schema:
`to_type:STRING, sto_num:INT, unv_num:INT, fam_num:INT, date:DATE, kpi1:FLOAT, comp_kpi1:FLOAT, kpi2:FLOAT, comp_kpi2:FLOAT, kpi3:INT, comp_kpi3:INT, kpi4:INT, comp_kpi4:INT, sto_rus_name:STRING, sto_eng_name:STRING, unv_name_eng:STRING, unv_name_rus:STRING, fam_name_eng:STRING, fam_name_rus:STRING`

For the purpose of the task, to_type values equal to 10 bytes, all other String field values = 30 bytes.

* 3 tables: d_fam, d_unv, d_sto - very small, 300 KB of data

* a view: data_per_fam_view:


	`select`   
	`	t1.to_type, t1.sto_num, t1.unv_num, t1.fam_num, t1.date,`  
	`	t1.kpi1, t1.comp_kpi1, t1.kpi2, t1.comp_kpi2,`  
	`	t1.kpi3, t1.comp_kpi3, t1.kpi4, t1.comp_kpi4,`
	`	t2.fam_name_eng, t2.fam_name_rus,`   
	`	t3.sto_name_eng, t3.sto_name_rus,`  
	`	t4.unv_name_eng, t4.unv_name_rus`     
	`from data_per_fam t1`  
	`left join d_fam t2`  
	`	on t1.fam_num = t2.fam_num`  
	`left join d_sto t3`   
	`	on t1.sto_num = t3.sto_num`  
	`left join d_unv t4`  
	`	on t1.unv_num  = t4.unv_num`  
	`where t1.date>='2018-01-01';`  


Please check the following queries:
1. `select * from data_per_fam where date='2020-07-01'`
2. `select * from data_per_fam where date between '2018-01-01' and '2018-12-31'`
3. `select * from data_per_fam_view where date='2020-07-01'`
4. `select * from data_per_fam_view where date between '2018-01-01' and '2018-12-31'`

And for each of them answer the following questions:
- How much data (appr.) will be consumed by running this query?
- How much data (appr.) will be billed by running it?



# Data engineering tasks (Decathlon).
## Task 1.
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
* Some records can cover the same periods. Think of the way to split them and put it in the code.

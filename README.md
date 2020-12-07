# US I94 immigration data Spark ETL

## Context
This projects aims to empower analytics team to analyze the US I94 immigration data with enriched U.S. City Demographic data and Airport Codes data. 

The ETL pipeline data analysis process is scaled up through the use of big data processing framework: Spark. A set of start schema analytics tables are created which allows analytics team to continue finding insights on immigration data.


## Dataset
The immigration dataset comes from the US National Tourism and Trade Office [I-94 Record](https://travel.trade.gov/research/reports/i94/historical/2016.html/). The dataset is partitioned by month and year. Each file is in sas7bdat format and contains metadata about an immigration record.

The demographic dataset comes from OpenSoft [US Cities: Demographics](https://public.opendatasoft.com/explore/dataset/us-cities-demographics/export/). The file is in CSV format and contains data about about the demographics of all US cities.

The airport code dataset comes from Datahub [Airport Codes](https://datahub.io/core/airport-codes#data/). The file is in CSV format and simple table of airport codes and corresponding cities.



## ETL Pipeline
This project scales up the data analysis process through the use of Spark framework, in order to further optimize queries on song play analysis.Spark achives high performance when processing analytic workloads on big data sets. Using in-memory computing, parallel processing and lazy evaluation, Spark supports fast query, analyze, and transform data at scale across a cluster with multiple machines.

1. The ETL pipeline extracts data from 3 different data sources
2. Processes the data using Spark
3. Transforms the data into star schema analytics tables



## Database Schema
Star Schema is used on analytics tables to give users the ability to perform simple query with less joins and fast aggregations. The Fact Table records in log data associated with song plays. Using this table, the company can relate and analyze four dimensions users, songs, artists and time.

* Fact Table: fact_immigration
* Dimension Tables: dim_airports, dim_city, dim_state, dim_date, dim_model_type, dim_visa_code

### Tables:
| table name | columns | description | type |
| ------- | ---------- | ----------- | ---- |
| fact_immigration | 'immigration_id', 'immigration_airport_id', 'immigration_arr_sas_date', 'immigration_dep_sas_date', 'immigration_model_type_id', 'immigration_addr_state_code', 'immigration_visa_code_id', 'immigration_age', 'immigration_match_flag', 'immigration_birth_year', 'immigration_gender', 'immigration_ins_number', 'immigration_airline', 'immigration_admission_number', 'immigration_flight_number', 'immigration_visa_type'| stores all i94 immigrations data | fact table |
| dim_airport | 'airport_id', 'airport_name', 'airpot_type', 'airport_state_code', 'airpot_city', 'airport_local_code', 'airport_coordinates' | stores information related to airports | dimension table |
| dim_city | 'city_id', 'city_name', 'city_state_name', 'city_state_code', 'city_median_age', 'city_male_population', 'city_female_population', 'city_total_population', 'city_veterans', 'city_foreign_born', 'city_household_size' | stores demographics data for cities | fact table |
| dim_state | 'state_code', 'state_name', 'state_male_population', 'state_female_population', 'state_total_population', 'state_veterans', 'state_foreign_born' | stores demographics data for states | dimension table |
| dim_date | 'sas_date', 'date_timestamp', 'date_day', 'date_month', 'date_year', 'date_weekday', 'date_week'] | stores date data | dimension table |
| dim_model_type | 'model_type_id', 'model_type_name' | stores immigration model type information | dimension table |
| dim_visa_code | 'visa_code_id', 'visa_code_name' | stores immigration visa code information | dimension table |
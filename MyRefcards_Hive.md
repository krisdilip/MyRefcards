# Hive

## References

###### 1. [Hive Documentation](https://cwiki.apache.org/confluence/display/Hive/Home)
###### 2. [Programming Hive by Edward Capriolo, Dean Wampler, and Jason Rutherglen � O'Reilly Media](http://shop.oreilly.com/product/0636920023555.do)

## Data Types

1. Numeric Data Types
	* TINYINT			e.g., 
	* SMALLINT			e.g., 
	* INT				e.g., 
	* BIGINT			e.g., 
	* FLOAT				e.g., 
	* DOUBLE			e.g., 
	* DECIMAL			e.g., 
2. String Data Types
	* STRING			e.g., 
	* VARCHAR			e.g., 
	* CHAR				e.g., 
3. Date/Time Data Types
	* DATE				e.g., 
	* TIMESTAMP			e.g., 
	* bytearray			e.g., 
4. Misc Data Types
	* BOOLEAN			e.g., 
	* BINARY			e.g., 
5. Complex Types
	* STRUCT			e.g., 
	* MAP				e.g., 
	* ARRAY				e.g., 
	
## Operators

1. Arithmetic Operators
	* A + B
	* A - B
	* A * B
	* A / B
	* A % B
	* A & B
	* A | B
	* A ^ B
	* ~B
2. Relational Operators
	* A = B
	* A != B
	* A <=> B
	* A <> B
	* A < B
	* A <= B
	* A > B
	* A >= B
	* A BETWEEN B AND C
	* A NOT BETWEEN B AND C
	* A IS NULL
	* A IS NOT NULL
	* A LIKE B
	* A NOT LIKE B
	* A RLIKE B
	* A REGEXP B
3. Logical Operators
	* A AND B
	* A && B
	* A OR B
	* A || B
	* NOT A
	* !A
	* A IN (value1, value2, …)
	* A IN (SUBQUERY)
	* A NOT IN (value1, value2, …)
	* A NOT IN (subquery)
	* EXISTS (subquery)
	* NOT EXISTS (subquery)
4. Complex Operators
	* A[i]
	* M[key]
	* S.a
	
## Hive Data Definition Language
	
### Creating a database schema

	CREATE DATABASE retail_dba LOCATION '/user/hive/warehouse/retail_dba/';
	
### Dropping a database schema

	-- Drop Database. Error will be thrown if the database does not exist
	Drop database retail_dba;
	
	-- Drop Database. Error will not be thrown if the database does not exist
	Drop database if exists retail_dba;
	
	-- Drop Database. Error will be thrown if the database is not empty
	Drop database if exists retail_dba restrict;
	
	-- Drop Database. if the database is not empty, all tables are dropped before dropping the database
	Drop database if exists retail_dba cascade;
	
	
### Altering a database schema

	Alter database retail_dba set dbproperties ('Created by' = 'zik-zak-jack', 'Created on' = '04-Dec-2016');
	
### Using a database schema
	
	Use retail_dba;
	
### Showing database schemas

	Show databases;
	
### Describing a database schema

	Describe schema retail_dba;
	
	Describe schema extended retail_dba;
	
	
### Creating tables

	
### Dropping tables

	
### Truncating tables

	
### Renaming tables

	
### Altering table properties

	
### Creating viewsDropping views

	
### Altering the view properties

	
### Altering the view as select

	
### Showing tables

	
### Showing partitions

	
### Show the table properties

	
### Showing create table

	
### HCatalog

	
### WebHCat

## Partitioning

	Partitioning in Hive is used to increase query performance. Partitions are like horizontal slices of data that allows the large sets of data as more manageable chunks.
	
	-- Partition by country
	CREATE TABLE customer(id STRING, name STRING, gender STRING, state STRING) PARTITIONED BY (country STRING);
	
	-- Multiple Partitions by country, state
	CREATE TABLE customer(id STRING, name STRING, gender STRING) PARTITIONED BY (country STRING, state STRING);

	-- How to prevent full table scan query
	hive> set hive.mapred.mode=strict;
	
	-- How to allow full table scan query
	hive> set hive.mapred.mode=nonstrict;
	
	-- List Partitions of a table
	SHOW PARTITIONS customer;
	
	-- Partition filters
	SHOW PARTITIONS customer PARTITION(country = 'US');
	SHOW PARTITIONS customer PARTITION(country = 'US', state='DC');
	
## Bucketing
	
	-- Enable Buketing
	set hive.enforce.bucketing=true;
	
	CREATE TABLE sales_bucketed (id INT, fname STRING, lname STRING, address STRING,city STRING,state STRING, zip STRING, IP STRING, prod_id STRING, date1 STRING) CLUSTERED BY (id) INTO 10 BUCKETS;
	INSERT INTO sales_bucketed SELECT * from sales;
	

## Beeline

	beeline -u 'jdbc:hive2://localhost:10000/default' -n root -p xxx -d org.apache.hive.jdbc.HiveDriver -e "select * from sales;"
	beeline -u 'jdbc:hive2://localhost:10000/default' -n cloudera -p cloudera -d org.apache.hive.jdbc.HiveDriver -e "select * from sales;"
	

## Hive cli

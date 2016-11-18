# Sqoop

## Help

sqoop help

## Version

sqoop version

## List Databases

    sqoop list-databases \

        --connect jdbc:mysql://quickstart:3306/retail_db \
    
        --username=retail_dba \
    
        --password=cloudera \
    
        --verbose

## List Tables

    sqoop list-tables \

        --connect jdbc:mysql://quickstart:3306/retail_db \
    
        --username=retail_dba \
    
        --password=cloudera \
    
        --verbose

## Provide Password from Command Prompt

    sqoop list-tables \

        --connect jdbc:mysql://quickstart:3306/retail_db \
    
        --username=retail_dba \
    
        -P

## Import a Table

    sqoop import \

        -m 1 \
    
        --connect jdbc:mysql://quickstart:3306/retail_db \
    
        --username=retail_dba \
    
        --password=cloudera \
    
        --table departments  \
    
        --warehouse-dir=/user/hive/warehouse \
    
        --hive-import
    
## Import only a sub-set of Table data

    sqoop import \

        -m 1 \
    
        --connect jdbc:mysql://quickstart:3306/retail_db \
    
        --username=retail_dba \
    
        --password=cloudera \
    
        --table departments  \
    
        --where "department_id > 10" \
    
        --warehouse-dir=/user/hive/warehouse \
    
        --hive-import
    
    
# Incremental-Data-Load

We are using Azure data factory for handling incremental load. We are creating a pipeline.

![image](https://user-images.githubusercontent.com/130303992/234020643-fd31c112-5fab-4af9-8c84-fcd3ae99d6e9.png)

This is our dataset in which date column is very important because according to date column we are deciding which data is added recently.

We are using incremental load. We are creating the STAGING TABLE which is a temporary data store table. And every time we are first dump all data in STAGING TABLE and then, finding from which date we have to update data.

We are first take maximum date from old table and then, according this max date we are finding greater date from STAGING TABLE. Then all data copy into the actual table.

SELECT * from [dbo].[stg_order003] where (cast([DATE] as date)) > (SELECT MAX(cast([DATE] as date)) from [dbo].[order003])

Once we copy data from STAGING TABLE then, we have to do empty STAGING TABLE.

TRUNCATE TABLE stg_order003


1.
![image](https://user-images.githubusercontent.com/130303992/234020845-79e84fc3-555d-4772-933d-d4e4bea3c952.png)

2.
![image](https://user-images.githubusercontent.com/130303992/234020911-669d49a9-ca1a-4c56-aa35-bbd2ac0d512a.png)

3.
![image](https://user-images.githubusercontent.com/130303992/234020998-69f47fa0-03c0-4cd5-b26d-8f80902d8f0f.png)

4.
![image](https://user-images.githubusercontent.com/130303992/234021050-68e461b2-c6db-45ee-be5a-3451148a5a69.png)

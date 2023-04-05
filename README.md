# Databricks-Goodread-ETL
▪ Goodreads rating dataset files are available in a parquet file format in Landing zone in S3 pointing the data 
▪ Creating cross account instance profile to point the data in S3 
▪ Apache Spark processes the files and does below transformations before loading into Silver Zone 
  o Clean-up - Null/blank/datatype check 
  o Splitting a big denormalized tables into smaller normalized tables 
  o Generating random unique id for author and publisher to create a Primary Key/Foreign key relationship 
  o List of tables created in Silver Zone: Books, Publisher, Author, Rating, Rating Detailed 
▪ Another Spark job reads from delta lake and creates a more curated delta table in Gold Zone 
  o List of tables created in Gold zone: Top ranked books, Books aggregated by author, Books aggregated by publisher, Books aggregated by year 
▪ Both the pipelines are scheduled using Databricks Scheduler 
▪ For quicker analysis, the data in Gold Zone can be queried using Serverless Databricks SQL

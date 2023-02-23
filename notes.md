my_spark = SparkSession \
    .builder \
    .appName("myApp") \
    .config("spark.mongodb.read.connection.uri", "mongodb://host.docker.internal/test.fruit") \
    .config("spark.mongodb.write.connection.uri", "mongodb://host.docker.internal/test.fruit") \
    .getOrCreate()


    people = my_spark.createDataFrame([("Bilbo Baggins",  50), ("Gandalf", 1000), ("Thorin", 195), ("Balin", 178), ("Kili", 77), ("Dwalin", 169), ("Oin", 167), ("Gloin", 158), ("Fili", 82), ("Bombur", None)], ["name", "age"])



```
pyspark --conf "spark.mongodb.read.connection.uri=mongodb://host.docker.internal:27017/countries.countries" --conf "spark.mongodb.write.connection.uri=mongodb://host.docker.internal:27017/countries.countries" --conf "spark.mongodb.write.database.uri=countries" --conf "spark.mongodb.write.collection.uri=countries" --conf "spark.mongodb.write.upsertDocument=false" --packages org.mongodb.spark:mongo-spark-connector_2.12:10.1.0
```

```
people = spark.createDataFrame([("France", "Paris")], ["country", "capital"])
```
```
people.write.format("mongodb").mode("append").save()
```
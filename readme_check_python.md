### Check the connection between the laptop m mongodb rs and spark worker

#### MONGODB RS.

Repeat the config on the /etc/localhost and rs.reconfig() of the kafka project

####  Spark worker.

https://pypi.org/project/pymongo/

* Check python on the spark worker side
```
python -c "import sys; print(sys.version)"
python -c "import pymongo; print(pymongo.version); print(pymongo.has_c())"
````

* Test the connection
````
python
import pymongo
client = pymongo.MongoClient("host.docker.internal", 27017)
db = client.test
db.name
db.my_collection
db.my_collection.insert_one({"x": 10}).inserted_id
````

possible output

````
bash-5.0# python
Python 2.7.18 (default, May  3 2020, 22:58:12) 
[GCC 8.3.0] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pymongo
>>> client = pymongo.MongoClient("host.docker.internal", 27017)
>>> db = client.test
>>> db.name
u'test'
>>> db.my_collection
Collection(Database(MongoClient(host=['host.docker.internal:27017'], document_class=dict, tz_aware=False, connect=True), u'test'), u'my_collection')
>>> db.my_collection.insert_one({"x": 10}).inserted_id
ObjectId('63f5f8720b56fd76d0601676')
>>> 
```
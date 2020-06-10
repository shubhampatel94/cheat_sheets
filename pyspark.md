1. Using UDF Coversion.

~~~python
from pyspark.sql.column import Column
from pyspark.sql.column import _to_java_column
from pyspark.sql.column import _to_seq
from pyspark.sql.functions import col


def getWeek(field):
    _week = sc._jvm._jvm.x.y.z.b.Bv.getBc()
    return Column(_week.apply(_to_seq(sc, [field], _to_java_column)))

df = spark.read.parquet("/x/y/z/b/date=2020-01-01")

from pyspark.sql.functions import avg, udf, substring, col

df.printSchema()

df.select(getWeek(col("c").cast("long"))).show()
~~~

2. PySpark Template
~~~python
import pyspark
from pyspark.shell import sqlContext
from pyspark.sql.functions import *
from pyspark import SparkContext
from pyspark.conf import SparkConf
from pyspark.sql import SQLContext

spark.sparkContext.stop()
spark.stop()

conf = (SparkConf()
        .setAppName("The name of the app")
       .set('spark.sql.session.timeZone', 'UTC')
        .set("spark.ui.enabled", "true")
        .set('spark.cores.max', '50')
        .set("spark.executor.memory", "8g")
        .set("spark.dynamicAllocation.enabled","false")
      .set("spark.sql.execution.arrow.enabled", "true"))
sc = SparkContext.getOrCreate(conf = conf)
sqlContext = SQLContext(sc)
print(sqlContext)
~~~
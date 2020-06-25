
1. SparkSessionTestWrapper
~~~Scala

package x.y.z
import org.apache.spark.sql.SparkSession

trait SparkSessionTestWrapper {

  lazy val spark: SparkSession = {
    SparkSession
      .builder()
      .master("local")
      .appName("spark test example")
      .getOrCreate()
  }

}

~~~

2. Basic Unit Test Template.
~~~scala


import org.scalatest.{FlatSpec, Matchers}

class MainTest extends FlatSpec with Matchers with SparkSessionTestWrapper {

// value check

def x():Int={
    2
}

"x operation" should "return the correct value" in {

    x shouldBe 2

}

  
}

~~~

3. Getting path of the file in test
~~~Scala
val path = getClass.getResource("/path/from/the/top/of/resources/directory").getPath
~~~

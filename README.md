# Assignment-16.1



Given a list of numbers - List[Int] (1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

scala> var a = List(1,2,3,4,5,6,7,8,9,10)
a: List[Int] = List(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)


scala> var b = sc.parallelize(a)
b: org.apache.spark.rdd.RDD[Int] = ParallelCollectionRDD[4] at parallelize at <console>:29



find the sum of all numbers
scala> var sum=b.sum()
sum: Double = 55.0

- find the total elements in the list
scala> var count=b.count()
count: Long = 10

- calculate the average of the numbers in the list
scala> var avg =sum/count
avg: Double = 5.5

- find the sum of all the even numbers in the list
scala> var even = b.filter(i=> (i%2==0))
even: org.apache.spark.rdd.RDD[Int] = MapPartitionsRDD[3] at filter at <console>:31

               ^
scala> even.foreach(println)
2
4
6
8
10

scala> var sumeven= even.sum()
sumeven: Double = 30.0


- find the total number of elements in the list divisible by both 5 and 3
scala> var Divide5 = b.filter(i=> (i%5==0))
Divide5: org.apache.spark.rdd.RDD[Int] = MapPartitionsRDD[2] at filter at <console>:31

scala> var Divide3 = b.filter(i=> (i%3==0))
Divide3: org.apache.spark.rdd.RDD[Int] = MapPartitionsRDD[3] at filter at <console>:31

scala> Divide5.foreach(println)
5
10

scala> Divide3.foreach(println)
3
6
9


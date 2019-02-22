---
layout: post
title: Different Ways To WordCount
tags:
  - BigData
  - Spark
  - WordCount
---

#### Hi Big Data Devs,

When it comes to provide an example for a big-data framework, WordCount program is like a hello world programme.The main reason it gives a snapshot of Map-shuffle-reduce for the beginners.Here I am providing different ways to achieve it

## ReduceByKey (Transformation)

_Return type is same as input RDD type_

---

{% highlight java %}

JavaRDD<String> file = sc.textFile("/<Path_To_File>/README.md");

JavaRDD<String> words = file
.flatMap(f -> Arrays.asList(f.split(" ")).iterator())
.filter(f -> !f.isEmpty());

// grouping words with number 1
JavaPairRDD<String,Integer> wordMap_to_pair = words
.mapToPair(f -> new Tuple2<String,Integer>(f,1) );

//ReduceBykey,will merge at partition level and sends result to driver
JavaPairRDD<String,Integer> reducebyKey = wordMap_to_pair.reduceByKey((a,b) -> a+b);

System.out.println(reducebyKey.collect());

{% endhighlight %}

## foldByKey (Transformation)

---

It is similar to reeducebykey but takes the zeroValue.The user does not need to specify a combiner

{% highlight java %}

JavaPairRDD<String, Integer> Foldbykey = wordMap_to_pair.foldByKey(0, ((acc, val) -> acc+val));

System.out.println(Foldbykey.collect());

{% endhighlight %}

## aggregateByKey (Transformation)

---

_Return type need not be same as input RDD type_
_parameters_

**initalValue** @primitive types. `0` in Addition and subtraction , `1` in multiplication /division , `[]` on list ,`""` on string<br>
**SequenceFunction** @operates within partition level ,<br>
**CombinerFunction** @operates across partition level<br>

{% highlight java %}
JavaPairRDD<String,Integer> aggreagteBykey = wordMap_to_pair.aggregateByKey(
0 // initial value
, ( (a,v) -> a+v ) //seq,counting operation within partition
, ( (a,v) -> a+v )); // merge, counting operation across partition

System.out.println( aggreagteBykey.collect());

{% endhighlight %}

## CombineByKey (Transformation)

---

The user can specify a combiner function and customize combining behavior unlike aggregate and fold bykeys.

_Return type need not be same as input RDD type_

_parameters_

**createCombiner** @A function accepts current values and returns new value

**mergeValue** @merge/combine values within partition level

**mergeCombiners** @merge/combine values across partition level

{% highlight java %}

wordMap_to_pair.combineByKey(
i -> i, //createCombiner
(a,v) -> (a+v) //mergeValue
,(a,b) -> a+b) //mergeCombiners
.collect()
.forEach(System.out::println);

{% endhighlight %}

## groupByKey (Transformation)

---

Returns a Tuple of key and collection of values.performs hash join across partitions

{% highlight java %}

JavaPairRDD<String,Iterable<Integer>> groupByKey = wordMap_to_pair.groupByKey();

groupByKey
.mapValues( v -> Iterables.size(v)) // [1,1,1,1] -> [4]
.collect()
.forEach(System.out:println);

{% endhighlight %}

---

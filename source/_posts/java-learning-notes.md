---
title: Java Learning Notes
author: Jun Hu
tags:
  - Java
date: 2020-05-02 17:57:47
---

Start to take some notes when learning Java:

<!-- more -->

## Note1-enum
enum:
```java
public enum States {
    processing,processed,pending;
    public boolean isprocessing(){
        return this == processing;
    }
```
Test Case:
```java
@Test
        public void enumtest(){
            States state[] ={States.processing,States.pending};
            int i;
            for (i=0;i<2;i++) {
                if (state[i].isprocessing()) {
                    System.out.println(i + 1 + " :true");
                } else {
                    System.out.println(i + 1 + " :false");
                }
            }
        }
```
Output in Console:

```
1 :true
2 :false
```

## Note2-Logging

First, import the [framwork](http://www.slf4j.org/manual.html):
```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
```
Class:
```java
public class Car {
    static public void Process (String input){
            Logger log = LoggerFactory.getLogger(Car.class);
            log.info("hello{}",input);
    }
}
```
Test Case:
```java
@Test
        public void loggingtest(){
            Car car1 = new Car();
            car1.Process("damaoche");

        }
```
Output in Console:
```
7 [main] INFO com.junhu.learning.lesson1.Car - hellodamaoche
```


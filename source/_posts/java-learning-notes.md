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

## Note2-logging

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

## Note3-main method
Class:
```java
public class Lesson1 {
        public static void main(String[] args){
            for (String arg:args) {
                new Car().Process(arg);
            }
        }
```
Now I can run the class Lesson1 or the main method directly.
But still I can write a test case.
Test Case:
```java
@Test
    public void maintest(){
        String[] args = {"damao1", "damao2"};
        Lesson1.main(args);
    }
```

## Note4-exception handling
Write some switch cases to throw an exception:
```java
public class Car {
    static public int add(int input) {
        switch (input) {
            case 1:
                return 2;
            case 2:
                return 3;
            default:
                throw new RuntimeException("Invalid input: " + input);
        }
    }
}
```
Test Case
```jave
@Test
    public void execptiontest(){
    int inputs[]={1,3};
    for (int input:inputs){
        System.out.println( new Car().add(input));
    }
}
```
Output in Console:
```
2
java.lang.RuntimeException: Invalid input: 3
...
```
But it isn't actually handlling the exception. To handle it, add a try-catch block:
```java
@Test
    public void execptiontest() {
        int inputs[] = {1, 3};
        for (int input : inputs) {
            try {
                System.out.println(new Car().add(input));
            } catch (RuntimeException e) {
                System.out.println(e.getMessage());
                }

            }
        }
    }
```
Output in Console:
```
2
Invalid input: 3
```
Now, I start to understand some error messages and maybe even how to resolve some. :)


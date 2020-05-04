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
```java
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

## Note5-interface
>Interfaces are used to encode similarities which the classes of various types share, but do not necessarily constitute a class relationship. --  [Wikipedia](https://en.wikipedia.org/wiki/Interface_(Java))
For example, a car and a tank can both drive and stop:
```java
public class Car{
    public void drive() {
    	System.out.println("The car is driving...");
    }

    public void stop() {
    	System.out.println("The car is stopping...");
    }
}
public class Tank{
    public void drive() {
    	System.out.println("The tank is driving...");
    }

    public void stop() {
    	System.out.println("The tank is stopping...");
    }
}
```
Test Case:
```java
@Test
public void interfacetesting(){
    Car v1 =new Car();
    Tank v2 =new Tank();
    v1.drive();
    v1.stop();
    v2.drive();
    v2.stop();
}
```
Output in console:
```
The car is driving...
The car is stopping...
The tank is driving...
The tank is stopping...
```
To introduce the interface `Behavior`:
```java
public interface Behavior {
    void drive();
    void stop();
}
```
Then update the classes to `implement` the interface:
```java
public class Car implements Behavior { //implemets interface
    public void drive() {
    	System.out.println("The car is driving...");
    }

    public void stop() {
        System.out.println("The car is stopping...");
    }
}
public class Tank implements Behavior { //implemets interface
    public void drive() {
    	System.out.println("The tank is driving...");
    }

    public void stop() {
        System.out.println("The tank is stopping...");
    }
}
```
Test Case then can be re-written as follows:
```java
@Test
public void interfacetesting(){
    Behavior[] behaviors = {new Car(), new Tank()}; //interface variables can refer to any classes implementing this interface
    for(Behavior each:behaviors){
        each.drive();
        each.stop();
    }
}
```
The output will be the same. Now I can iterate different classes in the same for-loop.

## Note6-inheritance
The inheritance seems to be not so recommend, it can be used to avoid duplicated codes as interface but with (maybe) less flexibility.
To start with, write a class to inherite from:
```java
public class Vehicle {
    public void drive() {
        System.out.println("The vehicle is driving...");
    }

    public void stop() {
        System.out.println("The vehicle is stopping...");
    }
```
To inherite it, use `extends`:
```java
public class NewCar extends Vehicle{

}
public class NewTank extends Vehicle{
}
```
Test Case:
```java
@Test
public void inheritancetesting(){
    Vehicle[] vechiles = {new NewCar(),new NewTank()};
    for(Vehicle each:vechiles){
        each.drive();
        each.stop();
    }
}
```
Output in console:
```
The vehicle is driving...
The vehicle is stopping...
The vehicle is driving...
The vehicle is stopping...
```
I think I can use interface and inheritance interchangeably, but maybe not.


---
title: Java Learning Notes
author: Jun Hu
tags:
  - Java
date: 2020-05-02 17:57:47
---

To help myself to take reference in the furture. I am starting to take notes while learning Java from Marcus Biel's great [tutorials](https://www.youtube.com/playlist?list=PLFmkgh1ckFjH1LaQvs_5pAuaZVVZ_3qcM) .

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
To start with, write a class to inherite:
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

## Note7-clone method and more

Actually there were three ways of copying (i.e. the 'more'), see if I can repeat them all.

1. `clone` method in `Object` class

   a. Good practice:
	```java
	@Test
	public void goodclone(){
		String[] strs1={"a","b","c"};
		String[] strs2=strs1.clone();
		System.out.print("strs1:");
		for (String strs:strs1) {
			System.out.print(strs);
			System.out.print(";");
		}
		System.out.println("");
		System.out.print("strs2:");
		for (String strs:strs2) {

			System.out.print(strs);
			System.out.print(";");
		}
		System.out.println("");
		if(strs1==strs2){
			System.out.println("strs1 and strs2 are the same!");
		}else{
			System.out.println("strs1 and strs2 are NOT the same!");
		}
	}
	```
	Output in console:
	```
	strs1:a;b;c;
	strs2:a;b;c;
	strs1 and strs2 are NOT the same!
	```
	Why it is good? Because the contains are strings - immutable objects.
	
	b. Not so good but ok practice:
	Create a class and override the `clone` method:
	```java
	public class Car implements Cloneable { //need to implement Cloneable interface
    public Owner owner; //change it to a object type of Owner and to public so I can test it
    public Car (String owner){
        this.owner=owner;
    }
    public String whos(){
        return("The owner is " +owner);
    }
    @Override //to override clone method from object class
    public Car clone(){
        try {
            return (Car) super.clone(); //make return type as Car instead of object
        } catch (CloneNotSupportedException e) {
            throw new AssertionError();
        }
    }
	}
	```
	Test Case:
	```java
	@Test
    public void okclonetesting(){
        Car car1=new Car("damao1");
        Car car2=car1.clone();
        assertNotSame(car1,car2); //to show that two cars are not the same object
        assertEquals(car1.whos(),car2.whos()); //to show that car2 is a copy of car1
    }
	```
	So car1 and car2 are not the same object but the owner is the same. Which shows that car2 is a copy of car1.
	But why not so good? Because of the codes I have to wirte to override `clone` method. Why still ok? Because the contains are still strings, and this is a shallow copy - if the contains are objects they are not copied.
	
	c. Bad practice:
	If the contains are objects and I create a shallow copy of it:
	Class:
	```java
	public class Owner implements Cloneable{ //always remember to implement Cloneable interface!
		private String name;
		public Owner(String name){
			this.name=name;
		}
		public String ownersname(){
			 return (name);
		}
		public void changeowner(String newname) {
        this.name=newname;
		}
	}
	```
	and also change it in Car class
	```java
	...
	private Owner owner; //change it to a object
	...
	public String whos(){
        return("The owner is " +owner.ownersname()); //to retrive the name value
    }
	...
	```
	```java
	Test Case:
	@Test
    public void badclonetesting(){
        Owner owner1=new Owner("damao1");
        Car car1=new Car(owner1);
        Car car2=car1.clone();
        assertNotSame(car1,car2); //to show that two cars are not the same object
        assertSame(car1.owner,car2.owner); //to show that two owners actually refer the same object
        car2.owner.changeowner("damao2"); //to change owner2's name and see owner1's name also changes
        System.out.println("car1: "+ car1.whos());
        System.out.println("car2: "+ car2.whos());
    }
	```
	Output in console:
	```
	car1: The owner is damao1
	car2: The owner is damao1
	```
	Which shows that the owner is not copied.
	So to copy the owner, first to override `clone` method in Owner class:
	```java
	@Override //to override clone method from object class
    public Owner clone(){
        try {
            return (Owner) super.clone();
        } catch (CloneNotSupportedException e) {
            throw new AssertionError();
        }
    }
	```
	then to rewrite `clone` method in Car class:
	```java
	@Override //to override clone method from object class
    public Car clone(){
        try {
            Car car =(Car) super.clone();
            car.owner=owner.clone();
            return car;
        } catch (CloneNotSupportedException e) {
            throw new AssertionError();
        }
    }
	```
	Test Case:
	```java
	@Test
    public void badclonetesting(){
        Owner owner1=new Owner("damao1");
        Car car1=new Car(owner1);
        Car car2=car1.clone();
        assertNotSame(car1,car2); //to show that two cars are not the same object
        assertNotSame(car1.owner,car2.owner); //to show that two owners are not the same object
        car2.owner.changeowner("damao2"); //to change owner2's name and see owner1's name does not change now
        System.out.println("car1: "+ car1.whos());
        System.out.println("car2: "+ car2.whos());
    }
	```
	Output in console:
	```
	car1: The owner is damao1
	car2: The owner is damao2
	```
	It works now, but indeed it is too complicated. It is a good way of practicing though.
	
2. constructor
	To make a copy of itself, create a constructor with itself as the parameter.
	```java
	...
	private String name;
	public Owner(String name){
		this.name=name;
	}
	public Owner(Owner owner){ //makecopy
        this.name = name;
    }
	...
	
	...
	public Owner owner;
    public Car (Owner owner){
        this.owner=owner;
    }
	public Car(Car car){ //makecopy
        this.owner=new Owner(car.owner);
    }
	...
	```
	Test Case:
	```java
	@Test
    public void constructortesting(){
        Owner owner1 = new Owner("damao1");
        Car car1 = new Car(owner1);
        Car car2 = new Car(car1);
        assertNotSame(car1,car2);
        assertNotSame(owner1,car2.owner);
    }
	```
	But constructors don't have meaningful names so can be confusing.
3. static factory method
	>Consider static factory methods instead of constructors. -- Joshua Bloch
	
	Static factory method has a distinct method name but the logic and the structer looks the same - create a method with itself as the parameter, and return a new object of its type.
	```java
	...
	public static Car newInstance(Car car){
        return new Car(Owner.newInstance(car.owner));
    }
	...
	
	...
	public static Owner newInstance(Owner owner){
        return new Owner(owner.name);
    }
	...
	```
	Test Case:
	```java
	@Test
    public void constructortesting(){
        Owner owner1 = new Owner("damao1");
        Car car1 = new Car(owner1);
        Car car2 = Car.newInstance(car1);
        assertNotSame(car1,car2);
        assertNotSame(owner1,car2.owner);
    }
	```
That's the end of the first learning notes. I will continute with specific topics then.

---
title: Java Comparable Interface
author: Jun Hu
tags:
  - Java
date: 2020-05-09 19:02:22
---

>Java Comparable interface is used to order the objects of the user-defined class. This interface is found in java. lang package and contains only one method named compareTo(Object). It provides a single sorting sequence only, i.e., you can sort the elements on the basis of single data member only.

This post show an example of sorting apples by their types (string), colors (enum) and weights (int).

<!-- more -->

First, create an enum Color:
```java
public enum Color {
    RED,ALMOSTRED,ALMOSTGREEN,GREEN
}
```
Where RED can be considered as 0, ALMOSTRED as 1, and so on.

Then create the apple class:
```java
public class Apple implements Comparable<Apple> { //implements interface
    private String Type;
    private Color Color;
    private int Weight;

    //to compare apples, first by brand then by color at last by weight
    @Override
    public int compareTo(Apple input){
        int temp;
        if ((temp=Type.compareTo(input.Type))==0){
            if ((temp=Color.compareTo(input.Color))==0){
                if ((temp=Integer.compare(this.Weight,input.Weight))==0){
                    return 0;
                }
                return temp;
            }
            return temp;
        }
        return temp;
    }

    public Apple(String Type, Color Color, int Weight){
        this.Type=Type;
        this.Color=Color;
        this.Weight=Weight;
    }
}
```
Test Case:
```java
@Test
public void comparabletesting(){
	Apple apple1=new Apple("B",Color.RED,12);
	Apple apple2=new Apple("B",Color.RED,12);
	Apple apple3=new Apple("A",Color.RED,12);
	Apple apple4=new Apple("A",Color.ALMOSTGREEN,12);
	Apple apple5=new Apple("A",Color.RED,12);
	Apple apple6=new Apple("B",Color.RED,12);
	Apple[] apples ={apple1,apple2,apple3,apple4,apple5,apple6};
	int i;
	for (i=0;i<5;i++) {
		System.out.println("apple"+(i+1)+"/"+"apple"+(i+2)+": "+apples[i].compareTo(apples[i+1]));
	}
}
```
Output in Console:
```
apple1/apple2: 0
apple2/apple3: 1
apple3/apple4: -2
apple4/apple5: 2
apple5/apple6: -1
```
Where "B">"A" by 1, RED<ALMOSTGREEN by 2.


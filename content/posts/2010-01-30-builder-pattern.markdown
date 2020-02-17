---
author: admin
comments: true
date: 2010-01-30 17:15:29+00:00
template: "post"
link: https://quachson.com/builder-pattern/
slug: builder-pattern
title: Builder Pattern
wordpress_id: 18
categories:
- Design Pattern
tags:
- Design Pattern
---

**Builder pattern: Construct a complex object from simple objects step by step. **

Example:
To build a house, we will take several steps:
1.build foundation,
2.build frame,
3.build exterior,
4.build interior.
Let's use an abstract class HouseBuilder to define these 4 steps. Any subclass of HouseBuilder will follow these 4 steps to build house (that is to say to implement these 4 methods in the subclass). Then we use a WorkShop class to force the order of these 4 steps (that is to say that we have to build interior after having finished first three steps). The TestBuilder class is used to test the coordination of these classes and to check the building process

import java.util.*;

class WorkShop {
//force the order of building process
public void construct(HouseBuilder hb) {
hb.buildFoundation();
hb.buildFrame();
hb.buildExterior();
hb.buildInterior();
}
}

//set steps for building a house
abstract class HouseBuilder {
protected House house = new House();

protected String showProgress() {
return house.toString();
}

abstract public void buildFoundation();
abstract public void buildFrame();
abstract public void buildExterior();
abstract public void buildInterior();
}

class OneStoryHouse extends HouseBuilder {

public OneStoryHouse(String features) {
house.setType(this.getClas


s() + " " + features);
}
public void buildFoundation() {
//doEngineering()
//doExcavating()
//doPlumbingHeatingElectricity()
//doSewerWaterHookUp()
//doFoundationInspection()
house.setProgress("foundation is done");
}public void buildFrame() {
//doHeatingPlumbingRoof()
//doElectricityRoute()
//doDoorsWindows()
//doFrameInspection()
house.setProgress("frame is done");
}

public void buildExterior() {
//doOverheadDoors()
//doBrickWorks()
//doSidingsoffitsGutters()
//doDrivewayGarageFloor()
//doDeckRail()
//doLandScaping()
house.setProgress("Exterior is done");
}

public void buildInterior() {
//doAlarmPrewiring()
//doBuiltinVacuum()
//doInsulation()
//doDryWall()
//doPainting()
//doLinoleum()
//doCabinet()
//doTileWork()
//doLightFixtureBlinds()
//doCleaning()
//doInteriorInspection()
house.setProgress("Interior is under going");
}
}

class TwoStoryHouse extends HouseBuilder {

public TwoStoryHouse(String features) {
house.setType(this.getClass() + " " + features);
}
public void buildFoundation() {
//doEngineering()
//doExcavating()
//doPlumbingHeatingElectricity()
//doSewerWaterHookUp()
//doFoundationInspection()
house.setProgress("foundation is done");
}

public void buildFrame() {
//doHeatingPlumbingRoof()
//doElectricityRoute()
//doDoorsWindows()
//doFrameInspection()
house.setProgress("frame is under construction");
}

public void buildExterior() {
//doOverheadDoors()
//doBrickWorks()
//doSidingsoffitsGutters()
//doDrivewayGarageFloor()
//doDeckRail()
//doLandScaping()
house.setProgress("Exterior is waiting to start");
}

public void buildInterior() {
//doAlarmPrewiring()
//doBuiltinVacuum()
//doInsulation()
//doDryWall()
//doPainting()
//doLinoleum()
//doCabinet()
//doTileWork()
//doLightFixtureBlinds()
//doCleaning()
//doInteriorInspection()
house.setProgress("Interior is not started yet");
}
}

class House {
private String type = null;
private List features = new ArrayList();

public House() {

}

public House(String type) {
this.type = type;
}

public void setType(String type) {
this.type = type;
}

public String getType() {
return type;
}

public void setProgress(String s) {
features.add(s);
}

public String toString() {
StringBuffer ff = new StringBuffer();
String t = type.substring(6);
ff.append(t + "n ");
for (int i = 0; i < features.size(); i ++) {
ff.append(features.get(i) + "n ");
}
return ff.toString();
}
}

class TestBuilder {

public static void main(String[] args) {

HouseBuilder one = new OneStoryHouse("2 bedrooms, 2.5 baths, 2-car garage, 1500 sqft");
HouseBuilder two = new TwoStoryHouse("4 bedrooms, 4 baths, 3-car garage, 5000 sqft");

WorkShop shop = new WorkShop();
shop.construct(one);
shop.construct(two);

System.out.println("Check house building progress: n");
System.out.println(one.showProgress());
System.out.println(two.showProgress());
}
}

**Consider a builder when faced with many constructor parameters.**

// Telescoping constructor pattern - does not scale well!
public class NutritionFacts {
private final int servingSize; // (mL) required
private final int servings; // (per container) required
private final int calories; // optional
private final int fat; // (g) optional
private final int sodium; // (mg) optional
private final int carbohydrate; // (g) optional

public NutritionFacts(int servingSize, int servings) {
this(servingSize, servings, 0);
}

public NutritionFacts(int servingSize, int servings, int calories) {
this(servingSize, servings, calories, 0);
}

public NutritionFacts(int servingSize, int servings, int calories, int fat) {
this(servingSize, servings, calories, fat, 0);
}

public NutritionFacts(int servingSize, int servings, int calories, int fat, int sodium) {
this(servingSize, servings, calories, fat, sodium, 0);
}

public NutritionFacts(int servingSize, int servings, int calories, int fat, int sodium, int carbohydrate) {
this.servingSize = servingSize;
this.servings = servings;
this.calories = calories;
this.fat = fat;
this.sodium = sodium;
this.carbohydrate = carbohydrate;
}

}

When you want to create an instance, you use the constructor with the shortest parameter list containing all the parameters you want to set:

NutritionFacts cocaCola = new NutritionFacts(240, 8, 100, 0, 35, 27);

Typically this constructor invocation will require many parameters that you don’t want to set, but you’re forced to pass a value for them anyway. In this case, we passed a value of 0 for fat. With “only” six parameters this may not seem so bad, but it quickly gets out of hand as the number of parameters increases

In short,** the telescoping constructor pattern works, but it is hard to write client code when there are many parameters, and harder still to read it**. The reader is left wondering what all those values mean and must carefully count parameters to find out. Long sequences of identically typed parameters can cause subtle bugs. If the client accidentally reverses two such parameters, the compiler won’t complain, but the program will misbehave at runtime. A second alternative when you are faced with many constructor parameters is the JavaBeans pattern, in which you call a parameterless constructor to create the object and then call setter methods to set each required parameter and each optional parameter of interest:

// JavaBeans Pattern - allows inconsistency, mandates mutability
public class NutritionFacts {
// Parameters initialized to default values (if any)
private int servingSize = -1; // Required; no default value
private int servings = -1; // " " " "
private int calories = 0;
private int fat = 0;
private int sodium = 0;
private int carbohydrate = 0;

public NutritionFacts() { }

// Setters
public void setServingSize(int val) { servingSize = val; }
public void setServings(int val) { servings = val; }
public void setCalories(int val) { calories = val; }
public void setFat(int val) { fat = val; }
public void setSodium(int val) { sodium = val; }
public void setCarbohydrate(int val) { carbohydrate = val; }
}

This pattern has none of the disadvantages of the telescoping constructor pattern. It is easy, if a bit wordy, to create instances, and easy to read the resulting code:

NutritionFacts cocaCola = new NutritionFacts();
cocaCola.setServingSize(240);
cocaCola.setServings(8);
cocaCola.setCalories(100);
cocaCola.setSodium(35);
cocaCola.setCarbohydrate(27);

Unfortunately, the JavaBeans pattern has serious disadvantages of its own. Because construction is split across multiple calls, ** a JavaBean may be in an inconsistent state partway through its construction**. The class does not have the option of enforcing consistency merely by checking the validity of the con-structor parameters. Attempting to use an object when it’s in an inconsistent state may cause failures that are far removed from the code containing the bug, hence difficult to debug. A related disadvantage is that** the JavaBeans pattern pre-cludes the possibility of making a class immutable**, an requires added effort on the part of the programmer to ensure thread safety.

Luckily, there is a third alternative that combines the safety of the telescoping constructor pattern with the readability of the JavaBeans pattern. It is a form of the Builder pattern. Instead of making the desired object directly, the client calls a constructor (or static factory) with all of the required parameters and gets a builder object. Then the client calls setter-like methods on the builder object to set each optional parameter of interest. Finally, the client calls a parame-terless build method to generate the object, which is immutable. The builder is a static member class of the class it builds. Here’s how it looks in practice:

// Builder Pattern
public class NutritionFacts {
private final int servingSize;
private final int servings;
private final int calories;
private final int fat;
private final int sodium;
private final int carbohydrate;

public static class Builder {
// Required parameters
private final int servingSize;
private final int servings;
// Optional parameters - initialized to default values
private int calories = 0;
private int fat = 0;
private int carbohydrate = 0;
private int sodium = 0;

public Builder(int servingSize, int servings) {
this.servingSize = servingSize;
this.servings = servings;
}

public Builder calories(int val) {
calories = val;
return this;
}

public Builder fat(int val) {
fat = val; return this;
}

public Builder carbohydrate(int val) {
carbohydrate = val;
return this;
}

public Builder sodium(int val) {
sodium = val;
return this;
}

public NutritionFacts build() {
return new NutritionFacts(this);
}
}

private NutritionFacts(Builder builder) {
servingSize = builder.servingSize;
servings = builder.servings;
calories = builder.calories;
fat = builder.fat;
sodium = builder.sodium;
carbohydrate = builder.carbohydrate;
}
}

Note that NutritionFacts is immutable, and that all parameter default values are in a single location. The builder’s setter methods return the builder itself so that invocations can be chained. Here’s how the client code looks:

NutritionFacts cocaCola = new NutritionFacts.Builder(240, 8).
calories(100).sodium(35).carbohydrate(27).build();

This client code is easy to write and, more importantly, to read. **The Builder pattern simulates named optional parameters as found in Ada and Python**.



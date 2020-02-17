---
author: admin
comments: true
date: 2011-04-25 06:47:01+00:00
template: "post"
link: https://quachson.com/design-pattern-prototype/
slug: design-pattern-prototype
title: 'Design Pattern: Prototype'
wordpress_id: 546
categories:
- Design Pattern
- Java
tags:
- Creational Patterns
- Design Pattern
- Java
---

**Prototype Pattern** là một trong những pattern thuộc **Creational Patterns** (Abstract Factory, Builder, Factory Method, [Prototype](http://wp.me/pimex-8O), [Singleton](http://quachson.wordpress.com/2011/04/25/design-pattern-singleton/))

Mục đích của Prototype patern là Clone.

[code lang="java"]
/**
 * Prototype class
 */
interface Prototype {
    void setX(int x);

    void printX();

    int getX();
}

/**
 * Implementation of prototype class
 */
class PrototypeImpl implements Prototype, Cloneable {
    private int x;

    /**
     * Constructor
     */
    public PrototypeImpl(int x) {
        setX(x);
    }

    @Override
    public void setX(int x) {
        this.x = x;
    }

    @Override
    public void printX() {
        System.out.println("Value: " + x);
    }

    @Override
    public int getX() {
        return x;
    }

    @Override
    public PrototypeImpl clone() throws CloneNotSupportedException {
        return (PrototypeImpl) super.clone();
    }
}

/**
 * Client code
 */
public class PrototypeTest {
    public static void main(String args[]) throws CloneNotSupportedException {
        PrototypeImpl prototype = new PrototypeImpl(1000);

        for (int y = 1; y < 10; y++) {
            // Create a defensive copy of the object to allow safe mutation
            Prototype tempotype = prototype.clone();

            // Derive a new value from the prototype's "x" value
            tempotype.setX(tempotype.getX() * y);
            tempotype.printX();
        }
    }
}
[/code]

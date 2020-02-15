---
author: quachson
comments: true
date: 2016-08-09 17:01:20+00:00
layout: post
link: https://quachson.com/builder-patterns/
slug: builder-patterns
title: Builder Pattern
wordpress_id: 1259
categories:
- Design Pattern
tags:
- Creational Patterns
- Design Pattern
- Java
---

Builder Patterns: constructor có quá nhiều parameters, dùng builder để group lại cho dễ sử dụng.

[code lang="java"]
public class Hero {
   private final String name;
   private final String weapon;
   private final String armor;
 
   // get, set  
  
   public Hero(Builder builder) {
      this.name = builder.name;
      this.weapon = builder.weapon;
      this.armor = builder.armor;
   }

   public static class Builder {
      private final String name;
      private String weapon;
      private String armor;

      public Builder(String name) {
         if (name == null) {
            throw new IllegalArgumentException("name can not be null");
         }
         this.name = name;
      }

      public Builder withWeapon(String weapon) {
         this.weapon = weapon;
         return this;
      }
      public Builder withArmor(String armor) {
         this.armor = armor;
         return this;
      }

      public Hero build() {
         return new Hero(this);
      }

   } // end Builder
}  //end Hero
[/code]

Sau đây là cách gọi để khởi tạo

[code lang="java"]
public class App {
   public static void main(String[] args) {
       Hero hero = new Hero.Builder("Xavior").withWeapon("gun").withArmor("leather").build();
   }
}

[/code]

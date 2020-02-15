---
author: admin
comments: true
date: 2011-04-25 16:41:40+00:00
layout: post
link: https://quachson.com/design-pattern-composite/
slug: design-pattern-composite
title: 'Design Pattern: Composite'
wordpress_id: 552
categories:
- Design Pattern
- Java
tags:
- Design Pattern
- Java
---

**Định nghĩa**: the **composite pattern** is a partitioning [design pattern](http://en.wikipedia.org/wiki/Design_pattern_%28computer_science%29). The composite pattern describes that a group of objects are to be treated in the same way as a single instance of an object. The intent of a composite is to "compose" objects into tree structures to represent part-whole hierarchies. Implementing the composite pattern lets clients treat individual objects and compositions uniformly.[[1]](http://en.wikipedia.org/wiki/Composite_pattern#cite_note-GangOfFour-1)

[code java="lang"]
<pre>
public class Directory {
   private Directory directory;
   private File[] files;

   public Directory(File[] files) {
      this.files = files;
   }

   public Directory(Directory directory, File[] files) {
      this.directory = directory;
      this.files = files;
   }
   boolean isDirectory() {
      return files != null;
   }
   boolean isFile() {
      return files ==null;
   }

   public Directory getDirectory() {
      return directory;
   }

   public void setDirectory(Directory directory) {
      this.directory = directory;
   }

   public File[] getFiles() {
      return files;
   }

   public void setFiles(File[] files) {
      this.files = files;
   }

}
[/code]

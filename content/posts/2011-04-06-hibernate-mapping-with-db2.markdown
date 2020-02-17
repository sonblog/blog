---
author: admin
comments: true
date: 2011-04-06 02:39:33+00:00
template: "post"
link: https://quachson.com/hibernate-mapping-with-db2/
slug: hibernate-mapping-with-db2
title: Hibernate Mapping with DB2
wordpress_id: 429
categories:
- Hibernate
- Java
tags:
- Hibernate
- Java
---

[code lang="xml"]
<?xml version="1.0"encoding="utf-8" ?>

<!DOCTYPE hibernate-mapping PUBLIC "-//Hibernate/Hibernate Mapping DTD 3.0//EN"

"http://hibernate.sourceforge.net/hibernate-mapping-3.0.dtd">

<hibernate-mapping>

<class name="com.quachson.Example" table="EXAMPLE" schema="DBO">

<id name="id" type="java.lang.Long">

<column name=<em>"ID"</em> />

<generator class=<em>"assigned"</em> />

</id>

<property name="varBlob" type="java.lang.String">

<column name="VAR_BLOB" />

</property>

<property name="varCharacter" type="java.lang.String">

<column name="VAR_CHARACTER" length="10" />

</property>

<property name="varClob" type="java.lang.String">

<column name="VAR_CLOB" />

</property>

<property name="varDate" type="java.util.Date">

<column name="VAR_DATE" length="10" />

</property>

<property name="varDbclob" type="java.lang.String">

<column name="VAR_DBCLOB" />

</property>

<property name="varDecimal" type="java.lang.Integer">

<column name=<em>"VAR_DECIMAL"</em> precision=<em>"5"</em> scale=<em>"0"</em> />

</property>

<property name=<em>"varDouble"</em> type=<em>"java.lang.Double"</em>>

<column name=<em>"VAR_DOUBLE"</em> precision=<em>"53"</em> scale=<em>"0"</em> />

</property>

<property name=<em>"varGraphic"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_GRAPHIC"</em> length=<em>"20"</em> />

</property>

<property name=<em>"varInteger"</em> type=<em>"java.lang.Integer"</em>>

<column name=<em>"VAR_INTEGER"</em> />

</property>

<property name=<em>"varLongvarchar"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_LONGVARCHAR"</em> length=<em>"32700"</em> />

</property>

<property name=<em>"varLongvargraphic"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_LONGVARGRAPHIC"</em> length=<em>"32700"</em> />

</property>

<property name=<em>"varReal"</em> type=<em>"java.lang.Float"</em>>

<column name=<em>"VAR_REAL"</em> precision=<em>"24"</em> scale=<em>"0"</em> />

</property>

<property name=<em>"varSmallint"</em> type=<em>"java.lang.Short"</em>>

<column name=<em>"VAR_SMALLINT"</em> />

</property>

<property name=<em>"varTime"</em> type=<em>"java.sql.Time"</em>>

<column name=<em>"VAR_TIME"</em> length=<em>"8"</em> />

</property>

<property name=<em>"varTimestamp"</em> type=<em>"java.sql.Timestamp"</em>>

<column name=<em>"VAR_TIMESTAMP"</em> length=<em>"26"</em> />

</property>

<property name=<em>"varVarchar"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_VARCHAR"</em> length=<em>"10"</em> />

</property>

<property name=<em>"varVargraphic"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_VARGRAPHIC"</em> length=<em>"20"</em> />

</property>

<property name=<em>"varXml"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_XML"</em> />

</property>

</class>

</hibernate-mapping>

[/code]

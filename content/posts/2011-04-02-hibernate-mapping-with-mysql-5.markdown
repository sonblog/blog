---
author: admin
comments: true
date: 2011-04-02 07:12:37+00:00
template: "post"
link: https://quachson.com/hibernate-mapping-with-mysql-5/
slug: hibernate-mapping-with-mysql-5
title: Hibernate Mapping with MySQL 5
wordpress_id: 419
categories:
- Hibernate
- Java
tags:
- Hibernate
- Java
---

[code lang="xml"]

<hibernate-mapping>

<class name=<em>"Hibernate"</em> table=<em>"hibernate"</em> catalog=<em>"test"</em>>

<id name=<em>"id"</em> type=<em>"java.lang.Long"</em>>

<column name=<em>"ID"</em> />

<generator class=<em>"identity"</em> />

</id>

<property name=<em>"varMediumint"</em> type=<em>"java.lang.Integer"</em>>

<column name=<em>"VAR_MEDIUMINT"</em> />

</property>

<property name=<em>"varInt"</em> type=<em>"java.lang.Integer"</em>>

<column name=<em>"VAR_INT"</em> />

</property>

<property name=<em>"varSmallint"</em> type=<em>"java.lang.Short"</em>>

<column name=<em>"VAR_SMALLINT"</em> />

</property>

<property name=<em>"varTinyint"</em> type=<em>"java.lang.Short"</em>>

<column name=<em>"VAR_TINYINT"</em> />

</property>

<property name=<em>"varFloat"</em> type=<em>"java.lang.Float"</em>>

<column name=<em>"VAR_FLOAT"</em> precision=<em>"12"</em> scale=<em>"0"</em> />

</property>

<property name=<em>"varDouble"</em> type=<em>"java.lang.Double"</em>>

<column name=<em>"VAR_DOUBLE"</em> precision=<em>"22"</em> scale=<em>"0"</em> />

</property>

<property name=<em>"varDecimal"</em> type=<em>"java.lang.Long"</em>>

<column name=<em>"VAR_DECIMAL"</em> precision=<em>"10"</em> scale=<em>"0"</em> />

</property>

<property name=<em>"varChar"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_CHAR"</em> length=<em>"50"</em> />

</property>

<property name=<em>"varVarchar"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_VARCHAR"</em> length=<em>"50"</em> />

</property>

<property name=<em>"varTinytext"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_TINYTEXT"</em> />

</property>

<property name=<em>"varText"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_TEXT"</em> length=<em>"65535"</em> />

</property>

<property name=<em>"varMediumtext"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_MEDIUMTEXT"</em> length=<em>"16777215"</em> />

</property>

<property name=<em>"varLongtext"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_LONGTEXT"</em> />

</property>

<property name=<em>"varBinary"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_BINARY"</em> />

</property>

<property name=<em>"varVarbinary"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_VARBINARY"</em> />

</property>

<property name=<em>"varTinyblob"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_TINYBLOB"</em> />

</property>

<property name=<em>"varBlob"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_BLOB"</em> />

</property>

<property name=<em>"varMediumblob"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_MEDIUMBLOB"</em> />

</property>

<property name=<em>"varLongblob"</em> type=<em>"java.lang.String"</em>>

<column name=<em>"VAR_LONGBLOB"</em> />

</property>

<property name=<em>"varDate"</em> type=<em>"java.util.Date"</em>>

<column name=<em>"VAR_DATE"</em> length=<em>"10"</em> />

</property>

<property name=<em>"varTime"</em> type=<em>"java.sql.Time"</em>>

<column name=<em>"VAR_TIME"</em> length=<em>"8"</em> />

</property>

<property name=<em>"varYear"</em> type=<em>"java.util.Date"</em>>

<column name=<em>"VAR_YEAR"</em> length=<em>"0"</em> />

</property>

<property name=<em>"varDatetime"</em> type=<em>"java.sql.Timestamp"</em>>

<column name=<em>"VAR_DATETIME"</em> length=<em>"19"</em> />

</property>

<property name=<em>"varTimestamp"</em> type=<em>"java.sql.Timestamp"</em>>

<column name=<em>"VAR_TIMESTAMP"</em> length=<em>"19"</em> />

</property>

</class>

</hibernate-mapping>

[/code]

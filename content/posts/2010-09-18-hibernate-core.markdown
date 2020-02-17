---
author: admin
comments: true
date: 2010-09-18 06:29:20+00:00
template: "post"
link: https://quachson.com/hibernate-core/
slug: hibernate-core
title: Hibernate Core Notes
wordpress_id: 317
categories:
- Hibernate
- Java
tags:
- Hibernate
- Java
---

+ Class Domain


<blockquote>public class User implements **Serializable** {

private String username;

private Address address;

** public User() {}**

// SET, GET

}</blockquote>


Notes POJO:

1) Serializable, Hibernate không yêu cầu bắt buộc nhưng khi lưu trữ trong httpSession hay RMI thì lại bắt buộc nên tốt nhất là nên có

2) Construct của class domain bắt buộc luôn là không có tham số.

3) Identifier property: phải có thuộc tính khóa trong Class, ở DB có hay không có primary key cũng được.

4) Nên có 2 phương thức equals() và hashCode() để khi lưu vào Map có thể so sánh.

The component type used as identifier must implement equals() and hashCode(). (Composite )

5) Non-final classes: Không nên khai báo final class khi class đó làm POJO, để có thế lazy loading.

- Be sure to import `@javax.persistence.Entity` to mark a class as an entity. It's a common mistake to import `@org.hibernate.annotations.Entity` by accident. (If use Annotations)

[code]
<class  name="ClassName"                               (1)
        table="tableName"                              (2)
        schema="owner"                                 (3)
        discriminator-value="discriminator_value"      (4)
        mutable="true|false"                           (5)
        catalog="catalog"                              (6)
        proxy="ProxyInterface"                         (7)
        dynamic-update="true|false"                    (8)
        dynamic-insert="true|false"                    (9)
        select-before-update="true|false"              (10)
        polymorphism="implicit|explicit"               (11)
        where="arbitrary sql where condition"          (12)
        persister="PersisterClass"                     (13)
        batch-size="N"                                 (14)
        optimistic-lock="none|version|dirty|all"       (15)
        lazy="true|false"                              (16)
        entity-name="EntityName"                       (17)
        check="arbitrary sql check condition"          (18)
        rowid="rowid"                                  (19)
        subselect="SQL expression"                     (20)
        abstract="true|false"                          (21)
        node="element-name"                            (22)
/>
[/code]

(1):  name="com.quachson.domain.Account" có phân biệt chữ hoa chữ thường. ( là Option, nhưng nên có )

(2): table="ACCOUNT" trùng với tên table trong Database.

(3): schema="DBO" trùng với schema trong Database, sẽ override lên <hibernate-mapping>

[code]
<id name="propertyName"                                             (1)
    type="typename"                                                 (2)
    column="column_name"                                            (3)
    unsaved-value="null|any|none|undefined|id_value"                (4)
    access="field|property|ClassName">                              (5)
    node="element-name|@attribute-name|element/@attribute|."
    <generator class="edentity|auto|sequence|..."/>
</id>
[/code]

Example:

[code]
<id name="id" type="java.lang.Integer" column="ID">
     <generator class="identity" />
</id>
[/code]

ID là primary key.

- Generator class:

+ IDENTITY: supports identity columns in **DB2, MySQL, MS SQL Server, Sybase** and **HypersonicSQL**. The returned identifier is of type long, short or int.

+ SEQUENCE: uses a sequence in **DB2, PostgreSQL, Oracle, SAP DB, McKoi **or a generator in Interbase. The returned identifier is of type `long`, `short` or `int`

+ TABLE (called MultipleHiLoPerTableGenerator in Hibernate) : uses a hi/lo algorithm to efficiently generate identifiers of type long, short or int, given a table and column as a source of hi values. The hi/lo algorithm generates identifiers that are unique only for a particular database.

+ AUTO: selects IDENTITY, SEQUENCE or TABLE depending upon the capabilities of the underlying database.


### Optimistic locking properties (optional)


Trong những phiên làm việc dài (long conversation or transation), lưu version là rất hữu ích để đảm bảo rằng 1 entity có cùng lúc 2 người cập nhật (update) , người thứ nhất cập nhật thành công, khi người thứ 2 cập nhật thì sẽ được thông báo dữ liệu đã thay đổi và không được cập nhật.

Có thể sử dụng 2 phương pháp:** version** hay **timestamp**.

Nó đặc biệt hữu ích khi dùng assigned identifiers or composite keys.

[code]
<version column="version_column"                                                         (1)
         name="propertyName"                                                             (2)
         type="typename"                                                                 (3)
         access="field|property|ClassName"                                               (4)
         unsaved-value="null|negative|undefined"                                         (5)
         generated="never|always"                                                        (6)
         insert="true|false"                                                             (7)
         node="element-name|@attribute-name|element/@attribute|."
/>
[/code]

(3): _type_ (optional - defaults to integer): the type of the version number.

(4): _access_ (optional - defaults to property): the strategy Hibernate uses to access the property value.

(5): _unsaved-value_ (optional - defaults to undefined): a version property value that indicates that an instance is newly instantiated (unsaved), distinguishing it from detached instances that were saved or loaded in a previous session. Undefined specifies that the identifier property value should be used.

Example:

Anotation

[code]

@Entitypublic class Flight implements Serializable {
   ...
   @Version
   @Column(name="OPTLOCK")
   public Integer getVersion() { ... }
}
[/code]

Hibernate provides three forms of lazy fetching - lazy (single-point) associations, lazy collections, and lazy properties

...

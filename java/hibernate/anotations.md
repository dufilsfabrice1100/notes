
* @Timestamp 
  * column="timestamp_column"                          (1)
  * name="propertyName"                                (2)
  * access="field|property|ClassName"                  (3)
  * unsaved-value="null|undefined"                     (4)
  * source="vm|db"                                     (5)
  * generated="never|always"                           (6)
  * node="element-name|@attribute-name|element/@attribute|."

* @Transient
   Everything is consider as persistant unless you specify @Transient

* @Type and @TypeDefs 

```java
//in org/hibernate/test/annotations/entity/package-info.java
@TypeDefs(
    {
    @TypeDef(
        name="caster",
        typeClass = CasterStringType.class,
        parameters = 6
            @Parameter(name="cast", value="lower")
        }
    )
    }
)
package org.hibernate.test.annotations.entity;

//in org/hibernate/test/annotations/entity/Forest.java
public class Forest {
    @Type(type="caster")
    public String getSmallText() {
    ...

```

* @Column

@Column(
    name="columnName";                                     (1)
    boolean unique() default false;                        (2)
    boolean nullable() default true;                       (3)
    boolean insertable() default true;                     (4)
    boolean updatable() default true;                      (5)
    String columnDefinition() default "";                  (6)
    String table() default "";                             (7)
    int length() default 255;                              (8)
    int precision() default 0; // decimal precision        (9)
    int scale() default 0; // decimal scale



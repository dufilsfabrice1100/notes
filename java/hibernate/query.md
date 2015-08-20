# Querying

## Class : __Criteria__ 

* **Criteria** is a Factory of **Session** 

* List all Records


```java

List result = HibernateUtil.getSessionFactory()
      .getCurrentSession().createCriteria(Event.class).list();

   if( result.size() > 0){
      Iterator it = result.iterator();
      while( it.hasNext()){
         Event event = ( Event ) it.next();
         System.out.println( event.getTitle() );
         System.out.println( event.getName() );
         System.out.println( dateFormatter.format (event.getDate() );
      }
   }

```

## Use SQL Expression 


```java
   Query query = session.createSQLQuery("SELECT * FROM EVENTS WHERE NAME like ?")
         .addEntity( Event.call );

   List eventList = query.setString("name", "Can Fest%").list();

```


```java
   
    protected void createAndStoreEvent(String title, Date theDate) {
        Event theEvent = new Event();
        theEvent.setTitle(title);
        theEvent.setDate(theDate);

        HibernateUtil.getSessionFactory()
                .getCurrentSession().save(theEvent);
    }

```

## CRUD 
   Create , Read , Update, Delete

```java

@Entity
@Table(name="CHAOS")
@SQLInsert( sql="INSERT INTO CHAOS(size, name, nickname, id) VALUES(?,upper(?),?,?)")
@SQLUpdate( sql="UPDATE CHAOS SET size = ?, name = upper(?), nickname = ? WHERE id = ?")
@SQLDelete( sql="DELETE CHAOS WHERE id = ?")
@SQLDeleteAll( sql="DELETE CHAOS")
@Loader(namedQuery = "chaos")
@NamedNativeQuery(name="chaos", query="select id, size, name, lower( nickname ) as nickname from CHAOS where id= ?", resultClass = Chaos.class)
public class Chaos {
    @Id
    private Long id;
    private Long size;
    private String name;
    private String nickname;
```

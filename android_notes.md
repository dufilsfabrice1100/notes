

Intents 
=========

* Intents are async messages which allow application components
  to request functionality from other Android components. 
* Interact with components of the same application as well with
  components contributed by other applications. 

* Class     android.content.Intent 
* *startActivity()* define that the Intent should be use to start 
  an activity. 
* Intent content Data via *Bundle*. This data can be use by receiving
  component. 

* __startActivity(intent)__ is defined on the __Context__ object which
  Activity extends. __that mean every Activity class can call the 
  method startActivity(intent)__ 

Demonstration 
```java
   public class ActivityOne extends Activity{

      // Start the activity connect to the
      // specified class 
      
      Intent intent = new Intent( this , ActivityTwo.class );
      intent.putExtra("Value1" , "some value 1");
      intent.putExtra("Value2" , "some value 2");
      startActivity( intent );

   }
```
* Subactivities which are started by other android android activities
  are called __sub-activity__. Among Example demonstrate this.

         AtivityTwo is an sub-activity of ActivityOne

* Implicit and explicit Intents 

* Explicit Intent: define the target component directly in the intent.
  see among demonstration 

* Implicit Indent: system evaluate registered components based on the
  intend data. it specitfy the action which should be performed.
  If only one component is found, Android starts this component 
  directly. If several components are identified by the Android 
  system, the user will get a selection dialog and can decide 
  which component should be used for the intent.

```
   Intent intent = new Intent(Intent.ACTION_VIEW, 
   Uri.parse("http://www.vogella.com"));
   startActivity(intent); 
```

* data transfer to the target component 
   * Class: Bundle
   * functions: getExtras(), putExtra(), getAction(), getData()
   
```
   Bundle extras = getIntent().getExtras();
   if (extras == null) {
    return;
   }
   // get data via the key
   String value1 = extras.getString(Intent.EXTRA_TEXT);
   if (value1 != null) {
      // do something with the data
   } 
```

* Using shared Intent
   * share some data with others applications 
   * example : Facebook, G+, Gmail, Twitter ....


```
   // this runs, for example, after a button click
   Intent intent = new Intent(Intent.ACTION_SEND);
   intent.setType("text/plain");
   intent.putExtra(android.content.Intent.EXTRA_TEXT, "News for you!");
   startActivity(intent); 
```

* Retrieving result data from sub-activity 
   * Activity can be closed via the back button on the phone.
     In this case the __finish()__ method is performed.
   * if the sub-activity was started with the __startActivity(intent)
     method call, the caller requires no result or feedback from
     sub-activity which now is closed
   * Preference to __startActivityForResult()__ method call, which
     when the sub-activity ends can retrieve data from the sub-activity
     in __onActivityResult()__ event handler. 

```
// Main activity 
public void onClick(View view) {
  Intent i = new Intent(this, ActivityTwo.class);
  i.putExtra("Value1", "This value one for ActivityTwo ");
  i.putExtra("Value2", "This value two ActivityTwo");
  // set the request code to any code you like,
  // you can identify the callback via this code
  startActivityForResult(i, REQUEST_CODE);
} 


@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
  if (resultCode == RESULT_OK && requestCode == REQUEST_CODE) {
    if (data.hasExtra("returnKey1")) {
      Toast.makeText(this, data.getExtras().getString("returnKey1"),
        Toast.LENGTH_SHORT).show();
    }
  }
} 

// sub-activity 

@Override
public void finish() {
  // Prepare data intent 
  Intent data = new Intent();
  data.putExtra("returnKey1", "Swinging on a star. ");
  data.putExtra("returnKey2", "You could be better then you are. ");
  // Activity finished ok, return the data
  setResult(RESULT_OK, data);
  super.finish();
} 
```


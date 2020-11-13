# Implementation
Make the following changes to your `app/build.gradle`
- add the maven plugin `apply plugin: 'maven'`
- add the repository
     ```
    repositories {
        maven {url "https://www.myget.org/F/nexxtv/maven"}
    }
    ```
- add the following dependencies und `dependencies`
    ```
    dependencies {
        implementation group: 'tv.nexx', name: 'nexxplay-android-widget', version: '1.6', ext: 'aar'
        implementation 'androidx.appcompat:appcompat:1.2.0'
        implementation 'com.googlecode.json-simple:json-simple:1.1'
        implementation 'com.android.volley:volley:1.1.1'
    }
    ```


## To add the widget to your app, may use the following:
```java
import tv.nexx.widget.widgetmodule.NexxWidget;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        NexxWidget widget = new NexxWidget();
        JSONObject config = new JSONObject();
        try {
            config.put("feedUpdateInterval", 90); // 30 minutes is default value
            config.put("userHash","userhash");
            config.put("deviceHash","devicehash");
            config.put("language","de");
        } catch (JSONException e) {
            e.printStackTrace();
        }
        widget.updateConfiguration(this, config);
    }
}
```
## To set the config set the values inside `values/strings.xml`, like this:
```xml
<resources>
    <string name="nexxwidget_domain_id" translatable="false">YOUR_DOMAIN_ID</string>
    <string name="nexxwidget_feed_hash" translatable="false">YOUR_FEED_HASH</string>
    <string name="nexxwidget_activity_id" translatable="false">YOUR_MAIN_ACTIVITY</string>
    <!-- following params are optional -->
    <string name="nexxwidget_feed_secret" translatable="false">YOUR_FEED_SECRET</string>
    <string name="nexxwidget_app_id" translatable="false">YOUR_APP_ID</string>
</resources>
```
For the activity ID, add something like the following `com.example.myapplication.MainActivity`

The data of the selected item/image will be sent to the specified activity via an intent with the following properties:
- `streamtype`
- `itemHash`
- `globalID`
- `refnr`
- `slug`
- `link`
- `abTestVersion`

## Compatibility
This widget should be compatible with Android 4.1 (API level 16) to Android 11 (API level 30).

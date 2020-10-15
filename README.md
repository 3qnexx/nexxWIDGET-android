# Implementation
Maven Dependency
```xml
<!-- https://www.myget.org/F/nexxtv/maven/tv.nexx/nexxplay-android-widget/1.3/nexxplay-android-widget-1.3.aar -->
<dependency>
  <groupId>tv.nexx</groupId>
  <artifactId>nexxplay-android-widget</artifactId>
  <version>1.3</version>
  <type>aar</type>
</dependency>

```

To add the widget to your app, may use the following:
```java
import tv.nexx.widget.widgetmodule.NexxWidget;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        NexxWidget widget = new NexxWidget();
        NexxWidget.setfeedUpdateInterval(90);
    }
}
```
To set the config set the values inside `values/strings.xml`, like this:
```xml
<resources>
    <string name="nexxwidget_domain_id" translatable="false">YOUR_DOMAIN_ID</string>
    <string name="nexxwidget_feed_hash" translatable="false">YOUR_FEED_HASH</string>
    <string name="nexxwidget_feed_secret" translatable="false">YOUR_FEED_SECRET</string>
    <string name="nexxwidget_activity_id" translatable="false">YOUR_PACKAGE_NAME</string>
    <string name="nexxwidget_app_id" translatable="false">YOUR_APP_ID</string>
</resources>
```

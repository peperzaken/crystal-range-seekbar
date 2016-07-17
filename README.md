# Crystal Range Seekbar

An extended version of seekbar and range seekbar with basic and advanced customization.

![alt tag](https://drive.google.com/uc?export=view&id=0B9bDENyIABT6cnh3MXY3TWstQWM)

# Usage
Add a dependency to your `build.gradle`:
```groovy
dependencies {
    compile 'com.crystal:crystalrangeseekbar:1.0.0'
}
```

# Features
- Customize with xml using custom handy attributes.
- Customize in your activity, fragment or dialog.
- Styling with your own widget.
- Creating newly widget from activity, fragment or dialog.

# Sample usage - Seekbar
![alt tag](https://drive.google.com/uc?export=view&id=0B9bDENyIABT6eFZkcFZKbWUxY1E)

Default style using xml.
```groovy
<com.crystal.crystalrangeseekbar.widgets.CrystalSeekbar
    android:id="@+id/rangeSeekbar1"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"/>
```
---
![alt tag](https://drive.google.com/uc?export=view&id=0B9bDENyIABT6Snk1Q21TbjhkWjQ)

Styling with bubble animation using custom widget `BubbleThumbSeekbar`.
```groovy
<com.crystal.crystalrangeseekbar.widgets.BubbleThumbSeekbar
    android:id="@+id/rangeSeekbar2"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:corner_radius="10"
    app:min_value="50"
    app:max_value="150"
    app:bar_color="#C69E89"
    app:bar_highlight_color="#A54B17"
    app:left_thumb_color="#775E4F"
    app:left_thumb_color_pressed="#4C2D1A"
    app:data_type="_integer"/>
```
---
![alt tag](https://drive.google.com/uc?export=view&id=0B9bDENyIABT6cHBraW9fUDBMaEU)

Styling with bubble animation with drawable using custom widget `BubbleThumbSeekbar`.
```groovy
<com.crystal.crystalrangeseekbar.widgets.BubbleThumbSeekbar
    android:id="@+id/rangeSeekbar3"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:corner_radius="10"
    app:min_value="0"
    app:max_value="100"
    app:steps="5"
    app:bar_color="#F7BB88"
    app:bar_highlight_color="#E07416"
    app:left_thumb_image="@drawable/thumb"
    app:left_thumb_image_pressed="@drawable/thumb_pressed"
    app:data_type="_integer"/>
```                    
---
![alt tag](https://drive.google.com/uc?export=view&id=0B9bDENyIABT6c0FnSDlVYnJyNVE)

Right to Left position (rtl)
```groovy
<com.crystal.crystalrangeseekbar.widgets.CrystalSeekbar
    android:id="@+id/rangeSeekbar7"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:position="right"/>
```                    
---
![alt tag](https://drive.google.com/uc?export=view&id=0B9bDENyIABT6RncwVndkSFFqMFE)

Right to Left position with drawable position update from code (rtl)
```groovy
<com.crystal.crystalrangeseekbar.widgets.CrystalSeekbar
    android:id="@+id/rangeSeekbar8"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:min_value="100"
    app:max_value="200"
    app:steps="5"
    app:bar_color="#F7BB88"
    app:bar_highlight_color="#E07416"
    app:left_thumb_image="@drawable/thumb"
    app:left_thumb_image_pressed="@drawable/thumb_pressed"
    app:data_type="_integer"/>
```                    
```java
// get seekbar from view
final CrystalSeekbar rangeSeekbar = (CrystalSeekbar) rootView.findViewById(R.id.rangeSeekbar8);

// change position left to right
rangeSeekbar.setPosition(CrystalSeekbar.Position.RIGHT).apply();
```
---
![alt tag](https://drive.google.com/uc?export=view&id=0B9bDENyIABT6eFZkcFZKbWUxY1E)

Create new seekbar from code and add to any view.
```java
// get seekbar from view
final CrystalSeekbar rangeSeekbar = new CrystalSeekbar(getActivity());

// get min and max text view
final TextView tvMin = (TextView) rootView.findViewById(R.id.textMin5);
final TextView tvMax = (TextView) rootView.findViewById(R.id.textMax5);

// set listener
rangeSeekbar.setOnSeekbarChangeListener(new OnSeekbarChangeListener() {
    @Override
    public void valueChanged(Number minValue) {
        tvMin.setText(String.valueOf(minValue));
    }
});

// get range seekbar container
RelativeLayout container = (RelativeLayout) rootView.findViewById(R.id.contRangeSeekbar5);
container.addView(rangeSeekbar);
```
---
![alt tag](https://drive.google.com/uc?export=view&id=0B9bDENyIABT6NloxcEJOVTJzQ00)

Styling with create custom widget
```java
public class MySeekbar extends CrystalSeekbar {

    public MySeekbar(Context context) {
        super(context);
    }

    public MySeekbar(Context context, AttributeSet attrs) {
        super(context, attrs);
    }

    public MySeekbar(Context context, AttributeSet attrs, int defStyleAttr) {
        super(context, attrs, defStyleAttr);
    }

    @Override
    protected float getMinValue(TypedArray typedArray) {
        return 5f;
    }

    @Override
    protected float getMaxValue(TypedArray typedArray) {
        return 90f;
    }

    @Override
    protected float getMinStartValue(TypedArray typedArray) {
        return 20f;
    }

    @Override
    protected int getBarColor(TypedArray typedArray) {
        return Color.parseColor("#A0E3F7");
    }

    @Override
    protected int getBarHighlightColor(TypedArray typedArray) {
        return Color.parseColor("#53C9ED");
    }

    @Override
    protected int getLeftThumbColor(TypedArray typedArray) {
        return Color.parseColor("#058EB7");
    }

    @Override
    protected int getLeftThumbColorPressed(TypedArray typedArray) {
        return Color.parseColor("#046887");
    }

    @Override
    protected Drawable getLeftDrawable(TypedArray typedArray) {
        return ContextCompat.getDrawable(getContext(), R.drawable.thumb);
    }

    @Override
    protected Drawable getLeftDrawablePressed(TypedArray typedArray) {
        return ContextCompat.getDrawable(getContext(), R.drawable.thumb_pressed);
    }
}
```

# Sample usage - Range Seekbar
![alt tag](https://drive.google.com/uc?export=view&id=0B9bDENyIABT6Q19QMzhoZzZubFE)

Default style using xml.
```groovy
<com.crystal.crystalrangeseekbar.widgets.CrystalRangeSeekbar
    android:id="@+id/rangeSeekbar1"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"/>
```
---
![alt tag](https://drive.google.com/uc?export=view&id=0B9bDENyIABT6UW04d01ORk1Ob0E)

Styling with bubble animation with drawable using custom widget `BubbleThumbRangeSeekbar`.
```groovy
<com.crystal.crystalrangeseekbar.widgets.BubbleThumbRangeSeekbar
    android:id="@+id/rangeSeekbar5"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:corner_radius="10"
    app:min_value="0"
    app:max_value="100"
    app:steps="5"
    app:bar_color="#F7BB88"
    app:bar_highlight_color="#E07416"
    app:left_thumb_image="@drawable/thumb"
    app:right_thumb_image="@drawable/thumb"
    app:left_thumb_image_pressed="@drawable/thumb_pressed"
    app:right_thumb_image_pressed="@drawable/thumb_pressed"
    app:data_type="_integer"/>
```
---
![alt tag](https://drive.google.com/uc?export=view&id=0B9bDENyIABT6bnZJWVZwUGV6TGc)

Set minimum range (gap).
```groovy
<com.crystal.crystalrangeseekbar.widgets.CrystalRangeSeekbar
    android:id="@+id/rangeSeekbar3"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:corner_radius="10"
    app:min_value="50"
    app:max_value="100"
    app:gap="20"
    app:bar_color="#8990C4"
    app:bar_highlight_color="#2434AD"
    app:left_thumb_color="#1A246D"
    app:right_thumb_color="#1A246D"
    app:left_thumb_color_pressed="#030B47"
    app:right_thumb_color_pressed="#030B47"
    app:data_type="_integer"/>
```
---
![alt tag](https://drive.google.com/uc?export=view&id=0B9bDENyIABT6eXRMQlkzNjA5cDg)

Set fix range (gap).
```groovy
<com.crystal.crystalrangeseekbar.widgets.CrystalRangeSeekbar
    android:id="@+id/rangeSeekbar4"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:corner_radius="10"
    app:min_value="0"
    app:max_value="100"
    app:fix_gap="30"
    app:bar_color="#EE88F7"
    app:bar_highlight_color="#D810EA"
    app:left_thumb_color="#8D0D99"
    app:right_thumb_color="#8D0D99"
    app:left_thumb_color_pressed="#56005E"
    app:right_thumb_color_pressed="#56005E"
    app:data_type="_integer"/>
```
---

__Available attributes__

+ ``popupLayout``: layout to be used, must include ``android:id/text1 TextView``
+ ``popupStyle``: can be ``fixed`` or ``follow``, default `follow`
+ ``popupAnimationStyle``: in/out animation, default `fade`
+ ``popupOffset``: distance from top/right of the widget to popup, default `0`
+ ``popupAlwaysShown``: do not dismiss popup after _onStopTrackingTouch_, default `false`
+ ``popupDraggable``: enables progress change by hint popup dragging, default `true`

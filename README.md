# RangeSeekBar

This is an initial version of a View for Android that tries to mimic the behavior of the JQueryUI Slider widget.

---
## Questions and ideas

https://groups.google.com/d/topic/android-developers/ZV5tAHnjl1A/discussion

---
## Usage with Eclipse

You can choose to use the RangeSeekBar as an included Android Library in Eclipse by doing the following:
1. Make a git clone of the project:
  `$ cd <my project dir>`
  `$ git clone git://github.com/Larpon/RangeSeekBar.git`

2. Make a new Android project in Eclipse from existing source:
  1. File -> New -> Project... -> Android -> Android Project
  2. Click "Next >"
  3. Tick the "Create project from existing source" radio button
  4. Untick "Use default location"
  5. Click the "Browse" button
  6. Navigate to <my project dir>/RangeSeekBar
  7. Click "Ok"

  Optionally change the "Project name" to anything you like.
  (this can be changed at any time with refactoring if desired)
  Click "Finish"
  The project should now be available in the Eclipse workspace tree with the name you entered.
  
3. Make sure the RangeSeekBar project is recognized as an Android Library:
  1. Right click the project in the tree
  2. Choose "Properties" -> Android
  3. Make sure the "Is Library" checkbox is ticked.
	
4. Now go to to your own project's properties:
  1. Right click your project in the tree
  2. Choose "Properties" -> "Android"
  3. Under "Library" click the "Add" button
  4. Choose the RangeSeekBar project

  The RangeSeekBar project should now be referenced in your own project.
  You can check it's referenced by looking at your project tree.

---
## Examples

Sparse usage examples are included in the git repository.
To see how it is used with XML see the res/layout/main.xml
A typical use from a Main activity would look like:

```
public class Main extends Activity {
	private static final String TAG = "Main";

	@Override
	public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        
        setContentView(R.layout.main);
        
        final RangeSeekBar rsb = (RangeSeekBar) findViewById(R.id.rangeSeekBarView1);
		rsb.setListener(new RangeSeekBarListener(){
			
			@Override
			public void onCreate(int index, float value) {
				// TODO Auto-generated method stub
			}
			
			@Override
			public void onSeek(int index, float value) {
				float f = 0.5f;
				float rounded = f * Math.round(value/f);
				((TextView) findViewById(R.id.hello)).setText("index: "+index+" val: "+rounded);
			}

			
		});
	}

}
```

to instantiate a RangeSeekBar from code without the use of XML do:
`RangeSeekBar rangeSeekBar = new RangeSeekBar(Context);`
or
`RangeSeekBar rangeSeekBar = new RangeSeekBar(Context,AttributeSet);`

Public methods include:

```
public void distributeThumbsEvenly()
public float getThumbValue(int index)
public void setThumbValue(int index, float value)

public interface RangeSeekBarListener {
    public void onCreate(int index, float value);
    public void onSeek(int index, float value);
}

public void setListener(RangeSeekBarListener listener)
public int getOrientation()
public void setOrientation(int orientation)
public float getThumbWidth()
public void setThumbWidth(float thumbWidth)
public float getThumbHeight()
public void setThumbHeight(float thumbHeight)
public boolean isLimitThumbRange()
public void setLimitThumbRange(boolean limitThumbRange)
public float getScaleRangeMin()
public void setScaleRangeMin(float scaleRangeMin)
public float getScaleRangeMax()
public void setScaleRangeMax(float scaleRangeMax)
public float getScaleStep()
public void setScaleStep(float scaleStep)
public Drawable getTrack()
public void setTrack(Drawable track)
public Drawable getRange()
public void setRange(Drawable range)
public Drawable getThumb()
public void setThumb(Drawable thumb)
```

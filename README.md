
# Ex.No:12 Design an application that draws basic graphical primitives on the screen.


## AIM:

To create and design an android application that draws basic graphical primitives on the screen using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as “graphical″ and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Draw basic object details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to create and design an android application that draws basic graphical primitives on the screen.
Developed by: Naveen Kumar E
Registeration Number : 212224230181
*/
```

activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp">

    <TextView
        android:id="@+id/title"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="Basic Graphical Primitives"
        android:textSize="24sp"
        android:textStyle="bold"
        android:gravity="center"
        android:padding="10dp"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <TextView
        android:id="@+id/description"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="Line, Circle, Rectangle, Oval and Triangle"
        android:textSize="16sp"
        android:gravity="center"
        android:padding="8dp"
        app:layout_constraintTop_toBottomOf="@id/title"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <FrameLayout
        android:id="@+id/drawingArea"
        android:layout_width="0dp"
        android:layout_height="0dp"
        android:background="#F1F1F1"
        app:layout_constraintTop_toBottomOf="@id/description"
        app:layout_constraintBottom_toTopOf="@id/drawButton"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <Button
        android:id="@+id/drawButton"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="Draw Shapes"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>

```
MainActivity.java
```java
package com.example.shapes;

import android.os.Bundle;
import android.graphics.Canvas;
import android.graphics.Paint;
import android.graphics.Color;
import android.graphics.Path;
import android.view.View;
import android.widget.Button;
import android.widget.FrameLayout;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    FrameLayout drawingArea;
    Button drawButton;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        drawingArea = findViewById(R.id.drawingArea);
        drawButton = findViewById(R.id.drawButton);

        drawingArea.addView(new ShapeView());

        drawButton.setOnClickListener(v -> {
            drawingArea.removeAllViews();
            drawingArea.addView(new ShapeView());
        });
    }

    class ShapeView extends View {

        Paint paint;

        ShapeView() {
            super(MainActivity.this);
            paint = new Paint();
            paint.setAntiAlias(true);
        }

        @Override
        protected void onDraw(Canvas canvas) {
            super.onDraw(canvas);

            float w = getWidth();
            float h = getHeight();

            paint.setTextSize(35);
            paint.setTextAlign(Paint.Align.CENTER);
            paint.setStrokeWidth(8);

            // Line
            paint.setColor(Color.BLUE);
            canvas.drawLine(40, 60, w - 40, 60, paint);

            paint.setColor(Color.BLACK);
            canvas.drawText("Line", w / 2, 110, paint);

            // Circle
            paint.setColor(Color.RED);
            canvas.drawCircle(w * 0.25f, h * 0.30f, 50, paint);

            paint.setColor(Color.BLACK);
            canvas.drawText("Circle", w * 0.25f, h * 0.30f + 90, paint);

            // Rectangle
            paint.setColor(Color.GREEN);
            canvas.drawRect(w * 0.60f, h * 0.20f,
                    w * 0.90f, h * 0.40f, paint);

            paint.setColor(Color.BLACK);
            canvas.drawText("Rectangle", w * 0.75f,
                    h * 0.40f + 45, paint);

            // Oval
            paint.setColor(Color.YELLOW);
            canvas.drawOval(w * 0.10f, h * 0.58f,
                    w * 0.45f, h * 0.72f, paint);

            paint.setColor(Color.BLACK);
            canvas.drawText("Oval", w * 0.275f,
                    h * 0.72f + 45, paint);

            // Triangle
            paint.setColor(Color.MAGENTA);

            Path path = new Path();
            path.moveTo(w * 0.75f, h * 0.55f);
            path.lineTo(w * 0.95f, h * 0.75f);
            path.lineTo(w * 0.55f, h * 0.75f);
            path.close();

            canvas.drawPath(path, paint);

            paint.setColor(Color.BLACK);
            canvas.drawText("Triangle", w * 0.75f,
                    h * 0.75f + 45, paint);
        }
    }
}
```
## OUTPUT

<img width="447" height="980" alt="image" src="https://github.com/user-attachments/assets/c081fe49-19b5-4a03-857d-f6c81a05cacf" />



## RESULT
Thus a Simple Android Application to create and design an android application that draws basic graphical primitives on the screen using Android Studio is developed and executed successfully.

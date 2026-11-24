## Ex.No:5 
Develop a simple calculator using android studio.
## AIM:
To develop a program to develop a simple calculator in Android Studio.

## EQUIPMENTS REQUIRED:
Android Studio(Min.required Artic Fox)

## ALGORITHM:
Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as calculator and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout using UI components in activity_main.xml.

Step 6: Display the calculator operation in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:

Program to print the text “calculator operation”.

Developed by: VISHWAJIH P

Registeration Number : 212225220122


## MainActivity.java
```

package com.example.calculator;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText editText;
    TextView resultText;

    double num1, num2;
    String operator = "";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editText = findViewById(R.id.editText2);
        resultText = findViewById(R.id.resultText);

        int[] numberIds = {
                R.id.num1, R.id.num2, R.id.num3,
                R.id.num4, R.id.num5, R.id.num6,
                R.id.num7, R.id.num8, R.id.num9,
                R.id.zero
        };

        for (int id : numberIds) {
            Button button = findViewById(id);

            button.setOnClickListener(v -> {
                editText.append(button.getText().toString());
            });
        }

        Button dot = findViewById(R.id.dot);

        dot.setOnClickListener(v -> {
            String value = editText.getText().toString();

            if (!value.contains(".")) {
                if (value.isEmpty()) {
                    editText.setText("0.");
                } else {
                    editText.append(".");
                }
            }
        });

        Button add = findViewById(R.id.add);
        Button sub = findViewById(R.id.sub);
        Button mul = findViewById(R.id.mul);
        Button div = findViewById(R.id.div);

        View.OnClickListener operationListener = v -> {
            String value = editText.getText().toString();

            if (!value.isEmpty()) {
                num1 = Double.parseDouble(value);

                Button b = (Button) v;
                operator = b.getText().toString();

                if (operator.equals("×")) {
                    operator = "*";
                }

                if (operator.equals("/")) {
                    operator = "/";
                }

                editText.setText("");
            }
        };

        add.setOnClickListener(operationListener);
        sub.setOnClickListener(operationListener);
        mul.setOnClickListener(operationListener);
        div.setOnClickListener(operationListener);

        Button clear = findViewById(R.id.clear_text);

        clear.setOnClickListener(v -> {
            editText.setText("");
            resultText.setText("Result: 0");
            num1 = 0;
            num2 = 0;
            operator = "";
        });

        Button submit = findViewById(R.id.submit);

        submit.setOnClickListener(v -> {
            String value = editText.getText().toString();

            if (value.isEmpty() || operator.isEmpty()) {
                Toast.makeText(this,
                        "Enter numbers and select an operator",
                        Toast.LENGTH_SHORT).show();
                return;
            }

            num2 = Double.parseDouble(value);

            double result = 0;

            switch (operator) {
                case "+":
                    result = num1 + num2;
                    break;

                case "-":
                    result = num1 - num2;
                    break;

                case "*":
                    result = num1 * num2;
                    break;

                case "/":
                    if (num2 == 0) {
                        resultText.setText("Result: Error");
                        return;
                    }
                    result = num1 / num2;
                    break;
            }

            resultText.setText("Result: " + result);
            editText.setText("");
            operator = "";
        });
    }
}

```

## Activitymain.XML

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="16dp"
    android:background="#FFFFFF">

    <EditText
        android:id="@+id/editText2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textSize="30sp"
        android:gravity="center"
        android:inputType="none"
        android:focusable="false"
        android:padding="15dp"/>

    <TextView
        android:id="@+id/resultText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textSize="24sp"
        android:gravity="center"
        android:padding="15dp"/>

    <TableLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:stretchColumns="*">

        <TableRow>
            <Button android:id="@+id/num1" android:text="1"/>
            <Button android:id="@+id/num2" android:text="2"/>
            <Button android:id="@+id/num3" android:text="3"/>
            <Button android:id="@+id/add" android:text="+"/>
        </TableRow>

        <TableRow>
            <Button android:id="@+id/num4" android:text="4"/>
            <Button android:id="@+id/num5" android:text="5"/>
            <Button android:id="@+id/num6" android:text="6"/>
            <Button android:id="@+id/sub" android:text="-"/>
        </TableRow>

        <TableRow>
            <Button android:id="@+id/num7" android:text="7"/>
            <Button android:id="@+id/num8" android:text="8"/>
            <Button android:id="@+id/num9" android:text="9"/>
            <Button android:id="@+id/mul" android:text="×"/>
        </TableRow>

        <TableRow>
            <Button android:id="@+id/dot" android:text="."/>
            <Button android:id="@+id/zero" android:text="0"/>
            <Button android:id="@+id/clear_text" android:text="CE"/>
            <Button android:id="@+id/div" android:text="/"/>
        </TableRow>

    </TableLayout>

    <Button
        android:id="@+id/submit"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="ENTER"
        android:layout_marginTop="20dp"/>

</LinearLayout>

```

## Output

<img width="1920" height="1080" alt="Screenshot (58)" src="https://github.com/user-attachments/assets/362d0956-997f-423d-a448-4eabe749a91a" />
<img width="1920" height="1080" alt="Screenshot (59)" src="https://github.com/user-attachments/assets/a7784892-4a71-492d-be59-ba781f410157" />


## Result:

Thus a Simple Android Application develop a program to create simple calculator in Android Studio is developed and executed successfully.

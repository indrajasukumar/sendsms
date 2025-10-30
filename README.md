
# Ex.No:3 Design an android application Send SMS using Intent.


## AIM:

To create and design an android application Send SMS using Intent using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as smsintent and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Send SMS and Display details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to create and design an android application Send SMS using Intent.
Developed by:INDRAJA S
Registeration Number :212222043003
*/
```
activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <EditText
        android:id="@+id/etNumber"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Phone Number"
        android:inputType="phone" />

    <EditText
        android:id="@+id/etMessage"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Message"
        android:inputType="textMultiLine"
        android:lines="4"
        android:gravity="top"
        android:scrollbars="vertical" />

    <Button
        android:id="@+id/btnSend"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Send SMS"
        android:layout_marginTop="20dp"/>
</LinearLayout>
```
MainActivity.java
```
package com.example.smsintent;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    EditText etNumber, etMessage;
    Button btnSend;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etNumber = findViewById(R.id.etNumber);
        etMessage = findViewById(R.id.etMessage);
        btnSend = findViewById(R.id.btnSend);

        btnSend.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String number = etNumber.getText().toString().trim();
                String message = etMessage.getText().toString().trim();

                if (number.isEmpty() || message.isEmpty()) {
                    Toast.makeText(MainActivity.this, "Enter number and message", Toast.LENGTH_SHORT).show();
                } else {
                    try {
                        // ✅ Correct URI for SMS apps
                        Uri uri = Uri.parse("smsto:" + number);
                        Intent intent = new Intent(Intent.ACTION_SENDTO, uri);
                        intent.putExtra("sms_body", message);

                        startActivity(intent);  // Opens default SMS app
                    } catch (Exception e) {
                        Toast.makeText(MainActivity.this, "No SMS app found!", Toast.LENGTH_SHORT).show();
                    }
                }
            }
        });
    }
}
```


## OUTPUT
![WhatsApp Image 2025-09-23 at 14 16 48_633e21e5](https://github.com/user-attachments/assets/11aa38b4-4f65-49f4-9420-373730614076)
![WhatsApp Image 2025-09-23 at 14 16 48_ec96940a](https://github.com/user-attachments/assets/9f59536a-6eee-48df-b01e-c92b105a9e31)
![WhatsApp Image 2025-09-23 at 14 17 00_986df579](https://github.com/user-attachments/assets/c89ebad8-ab6b-44cd-9417-35b21650f636)


## RESULT
Thus a Simple Android Application create and design an android application Send SMS using Intent using Android Studio is developed and executed successfully.

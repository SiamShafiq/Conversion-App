# Conversion-App
First little application experimenting with fields and texts.
package com.example.jarvis.converter;

import android.app.Activity;
import android.content.Context;
import android.content.DialogInterface;
import android.support.v7.app.ActionBarActivity;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.view.View.OnClickListener;
import android.view.View;
import android.widget.Toast;
import android.view.inputmethod.InputMethodManager;

public class MainActivity extends Activity
{

    @Override
    protected void onCreate(Bundle savedInstanceState) 
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);


        final EditText editText = (EditText) findViewById(R.id.editText);
        final EditText editText2 = (EditText) findViewById(R.id.editText2);


        Button button2 = (Button) findViewById(R.id.button2);
        button2.setOnClickListener(new View.OnClickListener()
        {
            @Override
            public void onClick (View arg0) 
            {
                editText.setText("");
                editText2.setText("");
            }
        });

        Button button = (Button) findViewById(R.id.button);
        button.setOnClickListener(new View.OnClickListener()


                {


                     @Override
                    public void onClick (View arg0)
                {

                      String check = editText.getText().toString();
                      String check2 = editText2.getText().toString();
                      InputMethodManager inputManager = (InputMethodManager)
                      getSystemService(Context.INPUT_METHOD_SERVICE);

                    inputManager.hideSoftInputFromWindow(getCurrentFocus().getWindowToken(),
                            InputMethodManager.HIDE_NOT_ALWAYS);

                    if (check.matches("") && check2.matches("") )
                    {
                        Toast.makeText(getApplicationContext(), "Please enter a value!", Toast.LENGTH_SHORT).show();
                    }
                    else if (check2.matches(""))
                    {

                        double centimeters = Double.valueOf(editText.getText().toString());
                        double inches = centimeters * 0.393701;

                        editText2.setText(String.valueOf(inches));
                    }
                    else if (check.matches(""))
                    {

                        double inches = Double.valueOf(editText2.getText().toString());
                        double centimeters = inches * 2.54;

                        editText.setText(String.valueOf(centimeters));
                    }
                }
        });



    }

}



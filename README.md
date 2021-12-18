# 11
можно звонить или писать кому-либо (правда мой телефон, почему-то, блочит звонки, но я не расстраиваюсь!)
```
rotected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Button mDialButton = (Button) findViewById(R.id.button);
        final EditText mPhoneNoEt = (EditText) findViewById(R.id.editTextTextPersonName);
        final EditText smsEdit = (EditText) findViewById(R.id.editTextTextPersonName2);

        mDialButton.setOnClickListener(new View.OnClickListener()
        {
            @Override
            public void onClick(View view)
            {
                String phoneNo = mPhoneNoEt.getText().toString();
                if(!TextUtils.isEmpty(phoneNo))
                {
                    String dial = "tel:" + phoneNo;
                    startActivity(new Intent(Intent.ACTION_CALL, Uri.parse(dial)));
                }
                else {
                    Toast.makeText(MainActivity.this, "Введите номер телефона", Toast.LENGTH_SHORT).show();
                }
            }
        });
    }

    public void onSms(View view)
    {
        EditText edit_Number=(EditText)findViewById(R.id.editTextTextPersonName);
        String phoneNo = edit_Number.getText().toString();
        EditText sms_edit=(EditText)findViewById(R.id.editTextTextPersonName2);
        String toSms="smsto:"+edit_Number.getText().toString();
        String messageText= sms_edit.getText().toString();
        Intent sms=new Intent(Intent.ACTION_SENDTO, Uri.parse(toSms));

        sms.putExtra("sms_body", messageText);
        startActivity(sms);
        SmsManager.getDefault().sendTextMessage(phoneNo, null, messageText.toString(), null, null);
    }
```
![image](https://user-images.githubusercontent.com/91714397/146626044-3c2aaa2d-b3cb-4000-8af4-187de7382b91.png)
![image](https://user-images.githubusercontent.com/91714397/146626049-760cd414-5017-464e-ae37-a107763a3116.png)
![image](https://user-images.githubusercontent.com/91714397/146626050-d0499019-8413-4a75-9456-0851506fbb57.png)



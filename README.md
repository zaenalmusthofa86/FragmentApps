# Study Activities and Fragments 

1. Declare them before running them in the manifest

```
<activity
     android:name=".FragmentActivity"
     android:label="@string/app_name"
     android:theme="@style/AppTheme.NoActionBar">
     <intent-filter>
         <action android:name="android.intent.action.MAIN" />

         <category android:name="android.intent.category.LAUNCHER" />
      </intent-filter>
</activity>
```

2. Reacting Activities

```
    @Override
    public void onViewCreated(View view, Bundle saveInstanceState) {
        super.onViewCreated(view, saveInstanceState);
        btnSwitch = (Button)getView().findViewById(R.id.btnSwitchOne);
        btnSwitch.setOnClickListener(new View.OnClickListener(){
            @TargetApi(Build.VERSION_CODES.HONEYCOMB)
            @Override
            public void onClick(View view) {
                if (dual) {
                    FragmentTransaction ft = getActivity().getFragmentManager().beginTransaction();
                    SecondFragment sf = (SecondFragment)getFragmentManager().findFragmentById(R.id.details);
                    if (sf == null){
                        sf = new SecondFragment();
                        ft.replace(R.id.details, sf);
                        ft.setTransition(FragmentTransaction.TRANSIT_FRAGMENT_FADE);
                        ft.commit();
                    }
                } else {
                    Intent i = new Intent();
                    i.setClass(getActivity(), SecondActivity.class);
                    startActivity(i);
                }
            }
        });
    }
````

3. Tampilan Menu Utama :

![img](https://github.com/zaenalmusthofa86/FragmentApps/blob/main/img/1.JPG)

4. Tampilan Setelah Menekan Tombol Button "Tampilkan Details!" :

![img](https://github.com/zaenalmusthofa86/FragmentApps/blob/main/img/2.JPG)

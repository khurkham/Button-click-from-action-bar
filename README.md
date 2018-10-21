# Launch-Facebook-App-on-Button-click-from-Any-Android-Application

ၶူတ်ႉဢၼ်ၼႆႉပုၼ်ႈတႃႇႁွင်ႉၸႂ်ႉ icon တီႈၼိူဝ် tab bar ၼၼ်ႉ  

public class MainActivity extends AppCompatActivity {

    
    private Button facebook;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
           super.onCreate(savedInstanceState);
           setContentView(R.layout.activity_main);

     

        facebook = (Button)findViewById(R.id.action_mail);
        facebook.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent facebookIntent = openFacebook(MainActivity.this);
                startActivity(facebookIntent);
            }
        });

    }


//facebook
    public static Intent openFacebook(Context context) {

        try {
            context.getPackageManager()
                    .getPackageInfo("com.facebook.katana", 0);
            return new Intent(Intent.ACTION_VIEW,
                    Uri.parse("fb://page/376227335860239")); //လႆၢႈ ID မၼ်းၵူၺ်း
        } catch (Exception e){

            return new Intent(Intent.ACTION_VIEW,
                    Uri.parse("https://www.facebook.com/karthikofficialpage"));  //လႆၢႈၸိုဝ်ႈၽဵတ်ႉႁဝ်းၵူၺ်း
        }


    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.menu_setting, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();
        
        ဢၼ်ၼႆႉပဵၼ်တႃႇသေး
        if (id == R.id.action_settings) {

            Intent sharingIntent = new Intent(android.content.Intent.ACTION_SEND);
            sharingIntent.setType("text/plain");
            String shareBodyText = "Check it out. Your message goes here";
            sharingIntent.putExtra(android.content.Intent.EXTRA_SUBJECT,"Subject here");
            sharingIntent.putExtra(android.content.Intent.EXTRA_TEXT, shareBodyText);
            startActivity(Intent.createChooser(sharingIntent, "Shearing Option"));
            return true;

        }
        
ဢၼ်ၼႆႉတႃႇႁွင်ႉၵႃႇတီႈ facebook
        if (id == R.id.action_mail) {
            //ပိုတ်ႇ mailtActivity

            return true;
        }

       
        return super.onOptionsItemSelected(item);
    }

  


//ဢၼ်ၼႆႉေပႃးေတဢွၵ်ႇဢႅပ်ႉမၼ်းေတထၢမ်ဝႃႈ ၸွင်ႇသူေတဢွၵ်ႇႁိုဝ်

    @Override
    public void onBackPressed() {
        AlertDialog.Builder builder = new AlertDialog.Builder(this)
                .setTitle("Attention!")
                .setMessage("Do you want to exit ?")
                .setPositiveButton("Yes", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialogInterface, int i) {
                        finish();
                    }
                })
                .setNegativeButton("No", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialogInterface, int i) {
                    }
                });
        AlertDialog dialog = builder.create();
        dialog.show();
    }




}

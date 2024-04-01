
# Rapport

**Skriv din rapport här!**

Till att börja med ändrade jag namn på appen i strings.xml. Se koden nedan.
```
<string name="app_name">MyApp</string>
```
Därefter möjliggjorde jag internetåterkomst i AndroidManifest.xml. Se koden nedan.
```
<uses-permission android:name="android.permission.INTERNET" />
```
Jag skapade ett WebView-element i activity_main.xml och raderade textView. Jag gav Web-View ID
my_webview. Se koden nedan.
 
```
    <WebView
        android:id="@+id/my_webview"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
```
Jag skapade en variabel "myWebView" i MainActivity.java som jag initierade i metoden
onCreate() genom att använda findViewById för att hämta den från activity_main.xml.
Se koden nedan.
```
    WebView myWebView;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Toolbar toolbar = findViewById(R.id.toolbar);
        setSupportActionBar(toolbar);

        myWebView = findViewById(R.id.my_webview);
```
Jag skapade ett nytt WebViewClient-objekt i MainActivity.java i onCreate()-metoden 
och importerade klassen WebViewClient. Därefter la jag till WebViewClient till myWebView.
Se koden nedan.
```
       myWebView = findViewById(R.id.my_webview);
       myWebView.setWebViewClient(new WebViewClient());
       myWebView.loadUrl("https://his.se");
```
Därefter la jag till möjligheten att köra Javascript genom att använda getSettings() och
setJavaScriptEnabled() i metoden onCreate(). Jag behövde importera klassen WebSettings för 
detta. Jag verifierade att detta fungerade och såg att rutan försvann att Javascript saknades
när jag uppdaterade appen. Se koden nedan.
```
       WebSettings myWebSettings = myWebView.getSettings();
       myWebSettings.setJavaScriptEnabled(true);
```
Sedan skapade jag en assets-mapp där jag skapade en html-fil och la in en rubrik samt en paragraf
i html-filen about.html.

I MainActivity.java i metoderna showExternalWebPage() och showInternalWebPage() la jag in en extern
URL, https://google.com, och min about.html-fil som intern webbsida. Se koden nedan.
```
    public void showExternalWebPage(){
        myWebView.loadUrl("https://google.com");
    }

    public void showInternalWebPage(){
        myWebView.loadUrl("file:///android_asset/about.html");
    }
```
För att kalla på metoderna när "External Web Page" och "Internal Web Page" klickas på i
dropdown-menyn ändrade jag i if-satserna i metoden onOptionsItemSelected() och la till 
showExternalWebPage() och showInternalWebPage(). Se koden nedan.
```
        if (id == R.id.action_external_web) {
            Log.d("==>","Will display external web page");
            showExternalWebPage();
            return true;
        }

        if (id == R.id.action_internal_web) {
            Log.d("==>","Will display internal web page");
            showInternalWebPage();
            return true;
        }
```

## Följande grundsyn gäller dugga-svar:

- Ett kortfattat svar är att föredra. Svar som är längre än en sida text (skärmdumpar och programkod exkluderat) är onödigt långt.
- Svaret skall ha minst en snutt programkod.
- Svaret skall inkludera en kort övergripande förklarande text som redogör för vad respektive snutt programkod gör eller som svarar på annan teorifråga.
- Svaret skall ha minst en skärmdump. Skärmdumpar skall illustrera exekvering av relevant programkod. Eventuell text i skärmdumpar måste vara läsbar.
- I de fall detta efterfrågas, dela upp delar av ditt svar i för- och nackdelar. Dina för- respektive nackdelar skall vara i form av punktlistor med kortare stycken (3-4 meningar).

Programkod ska se ut som exemplet nedan. Koden måste vara korrekt indenterad då den blir lättare att läsa vilket gör det lättare att hitta syntaktiska fel.

```
function errorCallback(error) {
    switch(error.code) {
        case error.PERMISSION_DENIED:
            // Geolocation API stöds inte, gör något
            break;
        case error.POSITION_UNAVAILABLE:
            // Misslyckat positionsanrop, gör något
            break;
        case error.UNKNOWN_ERROR:
            // Okänt fel, gör något
            break;
    }
}
```

Bilder läggs i samma mapp som markdown-filen.

![](android.png)

Läs gärna:

- Boulos, M.N.K., Warren, J., Gong, J. & Yue, P. (2010) Web GIS in practice VIII: HTML5 and the canvas element for interactive online mapping. International journal of health geographics 9, 14. Shin, Y. &
- Wunsche, B.C. (2013) A smartphone-based golf simulation exercise game for supporting arthritis patients. 2013 28th International Conference of Image and Vision Computing New Zealand (IVCNZ), IEEE, pp. 459–464.
- Wohlin, C., Runeson, P., Höst, M., Ohlsson, M.C., Regnell, B., Wesslén, A. (2012) Experimentation in Software Engineering, Berlin, Heidelberg: Springer Berlin Heidelberg.

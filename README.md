
# Rapport 2-webviews

## rename
- [x]    Rename your App. Hint: `res/values/strings.xml`

![image](https://user-images.githubusercontent.com/102797583/166688110-a097886d-9087-43b9-835d-6974b32697f6.png)


ändrat namnet på appen i strings.xml (app>res>values>strings.xml)

där appens namn har ändrats till Google knockoff
```
<resources>
    <string name="app_name">Google knockoff</string>
    <string name="action_external_web">External Web Page</string>
    <string name="action_internal_web">Internal Web Page</string>
</resources>
```
app_name har alltså ändrats!
action_external_web och internal web ändrar de 2st olika länkarnas namn.

## internet access
- [x]     Enable Internet access for your App. Hint: `AndroidManifest.xml`

För att kunna gå ut på internet så behöver vi först ge appen den tillgången.
För att göra detta används
```
    <uses-permission android:name="android.permission.INTERNET"/>
```
detta permissionet är i filen AndroidManifest.xml (app>manifest>AndroidManifest.xml),
där den är nestlat inuti manifest (dvs <manifest><uses-permision...../></manifest>)

## webview
- [x]   Create a WebView element in the layout file `content_main.xml` by replacing the existing `TextView
- [x]   Give the WebView an ID. Hint: `android:id="@+id/my_webview"`

för att skapa webviewn så används ett webview element som vi väljer ska  ta upp hela skärmen med hjälp av match-parent på både höjd och bredd.

```
    <WebView
        android:id="@+id/my_webview"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        tools:layout_editor_absoluteX="0dp"
        tools:layout_editor_absoluteY="0dp" />
```

för att kunna refferera till denna webviewn senare så ger vi den id = my_webview.

## variabel
- [x]   Create a private member variable called `myWebView` of the type `WebView` and instantiate it in `onCreate()`. Hint: `findViewById()`
- [x]   Locate the WebView element created in step 1 using the WebView ID
- [x]   Enable Javascript execution in your WebViewClient. Hint: `getSettings()` and `setJavaScriptEnabled()`

Först så initierar vi variabeln
```
WebView myWebView;
```
detta gör vi direkt i MainActivity classen då vi vill använda den i fler än 1 class.

för att kunna använda denna variablen så kopplar vi den till den webviewn vi skapat. 
```
        myWebView = findViewById(R.id.my_webview);
        myWebView.getSettings().setJavaScriptEnabled(true);
        myWebView.loadUrl("https://google.com");
        myWebView.setWebViewClient(new WebViewClient());
```
för att kunna få tillgång till internet så behöver vi också enabla javascript.

därefter öppnar vi en webviewclient och startar google då all denna kod körs i onCreate

- [x]   Add a html page as an asset.
- [x]   Implement `showExternalWebPage()` and `showInternalWebPage()`. Hint: `loadUrl()`.
- [x]   Call `showExternalWebPage()` and `showInternalWebPage()` when menu dropdown is clicked. Hint: `onOptionsItemSelected()`.

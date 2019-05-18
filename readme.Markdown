# 实验五
## **实验内容：**   
#### 本实验通过自定义WebView加载URL来验证隐式Intent的使用。
#### 实验包含两个应用： 
第一个应用：获取URL地址并启动隐式Intent的调用。  
第二个应用：自定义WebView来加载URL
## **主要代码：**  
#### Intent
```javascript
package com.example.intent_1;

import android.content.Intent;
import android.net.Uri;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {

    private Button btn;
    private EditText edit;
    private String urlconstraint="http://";
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.web);

        btn=findViewById(R.id.but);
        edit=findViewById(R.id.edit);
        btn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent intent=new Intent(Intent.ACTION_VIEW);
                intent.putExtra("url",urlconstraint+edit.getText().toString());
                startActivity(intent);
            }
        });
    }
}

``` 
#### WebView
```javascript
package com.example.webview;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.webkit.WebSettings;
import android.webkit.WebView;
import android.webkit.WebViewClient;

public class MainActivity extends AppCompatActivity {

    private String url="http://www.baidu.com";
    private WebView webView;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.webview);
        webView=(WebView)findViewById(R.id.webs);
        Bundle bundle=getIntent().getExtras();
        url=bundle.getString("url");
        WebSettings webSettings=webView.getSettings();
        webSettings.setSupportZoom(true);
        webSettings.setJavaScriptEnabled(true);
        webView.setWebViewClient(new WebViewClient());
        if(url!=null){
            webView.loadUrl(url);
        }
    }
}

```
## **实验截图：**
### 界面截图1
![Alt](https://github.com/CunmingChen/WebView-Intent/blob/master/Intent_1/pic1.png?raw=true#pic_center)
### 界面截图2 
![Alt](https://github.com/CunmingChen/WebView-Intent/blob/master/Intent_1/pic2.png?raw=true#pic_center)
### 界面截图3 
![Alt](https://github.com/CunmingChen/WebView-Intent/blob/master/Intent_1/pic3.png?raw=true#pic_center)  
 

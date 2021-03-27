- 👋 Hi, I’m @Jonata56
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

package telegra.ph;
 
import a.c.c;
import a.d.b.g;
import a.d.b.j;
import a.i.d;
import android.annotation.SuppressLint;
import android.content.Context;
import android.util.AttributeSet;
import android.webkit.WebSettings;
import java.io.BufferedReader;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.io.Reader;
import telegra.ph.b;
 
public final class Viewer extends im.delight.android.webview.a {
   public Viewer(Context var1, AttributeSet var2) {
      this(var1, var2, 0, 4, (g)null);
   }
 
   public Viewer(Context var1, AttributeSet var2, int var3) {
      j.b(var1, "context");
      super(var1, var2, var3);
      this.e();
   }
 
   // $FF: synthetic method
   public Viewer(Context var1, AttributeSet var2, int var3, int var4, g var5) {
      if((var4 & 2) != 0) {
         var2 = (AttributeSet)null;
      }
 
      if((var4 & 4) != 0) {
         var3 = 0;
      }
 
      this(var1, var2, var3);
   }
 
   private final void a(String var1, String var2) {
      StringBuilder var3 = new StringBuilder();
      var3.append("javascript:setAuthor(\'");
      var3.append(var1);
      var3.append("\',\'");
      var3.append(var2);
      var3.append("\');");
      this.loadUrl(var3.toString());
   }
 
   private final void setArticleTitle(String var1) {
      StringBuilder var2 = new StringBuilder();
      var2.append("javascript:setTitle(\'");
      var2.append(var1);
      var2.append("\');");
      this.loadUrl(var2.toString());
   }
 
   private final void setContent(String var1) {
      StringBuilder var2 = new StringBuilder();
      var2.append("javascript:setContent(\'");
      String var4;
      if(var1 != null) {
         var4 = a.i.g.a(var1, "\'", "\\\'", false, 4, (Object)null);
      } else {
         var4 = null;
      }
 
      var2.append(var4);
      var2.append("\');");
      this.loadUrl(var2.toString());
   }
 
   private final void setDescription(String var1) {
      StringBuilder var2 = new StringBuilder();
      var2.append("javascript:setDescription(\'");
      var2.append(a.i.g.a(var1, "\n", "<br>", false, 4, (Object)null));
      var2.append("\');");
      this.loadUrl(var2.toString());
   }
 
   private final void setViews(int var1) {
      StringBuilder var2 = new StringBuilder();
      var2.append("javascript:setViews(\'");
      var2.append(var1);
      var2.append("\');");
      this.loadUrl(var2.toString());
   }
 
   public final void a(b.b var1) {
      j.b(var1, "page");
      this.clearHistory();
      this.setArticleTitle(var1.c());
      this.a(var1.e(), var1.f());
      this.setViews(var1.h());
      if(var1.g() == null) {
         this.setDescription(var1.d());
      } else {
         this.setContent(var1.g());
      }
   }
 
   @SuppressLint({"SetJavaScriptEnabled", "AddJavascriptInterface"})
   public final void e() {
      WebSettings var1 = this.getSettings();
      j.a((Object)var1, (String)"settings");
      var1.setJavaScriptEnabled(true);
      WebSettings var2 = this.getSettings();
      j.a((Object)var2, (String)"settings");
      var2.setLoadWithOverviewMode(true);
      WebSettings var3 = this.getSettings();
      j.a((Object)var3, (String)"settings");
      var3.setUseWideViewPort(true);
      this.setOverScrollMode(2);
      this.setMixedContentAllowed(true);
      Context var4 = this.getContext();
      j.a((Object)var4, (String)"context");
      InputStream var5 = var4.getAssets().open("viewer.html");
      j.a((Object)var5, (String)"context.assets.open(\"viewer.html\")");
      Reader var6 = (Reader)(new InputStreamReader(var5, d.a));
      BufferedReader var7;
      if(var6 instanceof BufferedReader) {
         var7 = (BufferedReader)var6;
      } else {
         var7 = new BufferedReader(var6, 8192);
      }
 
      this.loadDataWithBaseURL("https://telegra.ph", c.a((Reader)var7), "text/html", "utf-8", (String)null);
   }
}

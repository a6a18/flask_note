# flask_note
My Flask Note

參考資料：[http://docs.jinkan.org/docs/flask/](http://docs.jinkan.org/docs/flask/)
### 調試模式

雖然`run()`方法適用於啟動本地的開發服務器，但是你每次修改代碼後都要手動重啟它。這樣並不夠優雅，而且Flask可以做到更好。如果你啟用了調試支持，服務器會在代碼修改後自動重新載入，並在發生錯誤時提供一個相當有用的調試器。

有兩種途徑來啟用調試模式。一種是直接在應用對像上設置:

    app.debug = True

    app.run()

另一種是作為run 方法的一個參數傳入:

    app.run(debug=True)

### 注意

但它依然允許執行任意代碼。這使它成為一個巨大的安全隱患，  因此它絕對不能用於`生產環境`。

----

## 路由

如果可以不訪問索引頁，而是直接訪問想要的那個頁面，他們多半會笑逐顏開而再度光顧。

如上所見，route()裝飾器把一個函數綁定到對應的URL上。

這裡是一些基本的例子:

    @app.route('/') 
    def index(): 
        return 'Index Page'
    
    @app.route('/hello') 
    def hello(): 
        return 'Hello World'

但是，不僅如此！你可以構造含有動態部分的URL，也可以在一個函數上附著多個規則。


## 變量規則
要給URL添加變量部分，你可以把這些特殊的字段標記為`<variable_name>`，這個部分將會作為命名參數傳遞到你的函數。規則可以用 `\<converter:variable_name\>`指定一個可選的轉換器。這裡有一些不錯的例子:
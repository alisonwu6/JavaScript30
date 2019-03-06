# 06 - Ajax Type Ahead

### JavaScipt 
* Web APIs
  * Fetch API()
    * 一個強制性的**取得資源的網址**參數
    * 回傳解析後的promise物件
    
* Promise：非同步的資料處理物件
    * 三種狀態
      * pending: 等待中的初始狀態
      * fulfilled: 正確完成
      * rejected: 已拒絕
    * 方法
      * then(): 在promise被完成或是被拒絕後立刻呼叫提供的方法
      ```
      fetch(url)
        .then(blob => blob.json())            // Response._proto_.json()
        .then(data => cities.push(...data));  // 用spread operator將資料推進cities
      ```

* 正規運算式：用來描述字元的範式(pattern of characters)
  * RegExp(pattern, flags)

* String物件
  * 方法
    * .match()：以一個正規運算式進行範式對比
    * .replace()：以一個正規運算式進行搜尋與取代作業


* 增加一個小功能
  * 當資料輸入完，但沒有任何成功配對的資料，則在li標籤內顯示「 👻 Wrong Typing? 」字樣作為提示
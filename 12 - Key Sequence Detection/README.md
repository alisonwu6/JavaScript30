# 12 - Key Sequence Detection

### 功能說明
* 在網頁上輸入Key Sequence(一串設定好的代碼)，就會跑出特效，就像[Konami Code](https://zh.wikipedia.org/wiki/%E7%A7%91%E4%B9%90%E7%BE%8E%E7%A7%98%E6%8A%80)。

* 目前設定的Key Sequence為"aha"，請打開網頁並輸入此字串即可產生特效。
### JavaScript
* splice(startIndex,deleteAmount)
  * startIndex：位置設定在pressed的開頭，`-secretCode.length - 1`
  * deleteAmount：
    * 當`pressed.length - secretCode.length`為負或零時不做任何刪減
    * 當`pressed.length - secretCode.length`為1，即刪除pressed的第一個索引值，讓pressed一直維持在secretCode.length

  ```
  pressed.splice(-secretCode.length - 1, pressed.length - secretCode.length);
  ```

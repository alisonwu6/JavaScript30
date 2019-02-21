# 03 - CSS Variables

### 功能說明
* 透過JavaScript操作CSS變數值

### HTML設定
*參考JavaScript大全 - 15.9 HTML表單*
  * input的*type*屬性值
    * range 可以變成左右移動的滑桿
    * color 可以選擇顏色
  * *name*為form屬性的特性名稱
  * 設定input的*min*值與*max*值，加上目前的預設值*value*

### CSS設定
  * CSS Variable
    * 設定方式 -> :root { --propertyName: value; }
    * 取用方式 -> selector { property: var(--propertyName); }

### JavaScript
  1. 監聽當input值改變(change事件)或滑鼠在事件上方移動(mousemove事件)
  2. **handleUpdate()**
      * suffix用來設定input值的字尾單位，Spacing與Blur皆需要px單位，所以在HTML行內設定data-sizing值為px;空值是給顏色使用，當此dataset沒值，及設定為空值。
      * document.documentElement參考至文件的根元素，指`<html>`元素
      * style.setProperty(propertyName, value)
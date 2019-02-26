# 14 - JavaScript References VS Copying

### 探討JavaScript何時使用reference機制以及如何複製物件及陣列

### JavaScript
* JavaScript的物件類型都是pass by reference，所以要學會複製所需要的物件再來進行操作。
  * 複製陣列的方式
    * iAmArray.slice();      - 回傳指定陣列的切片
    * [].concat(iAmArray);   - 串接陣列的元素，不會串接陣列。回傳新陣列
    * [...iAmArray];         - 使用ES6 Spread Operator複製
    * Array.from(iAmArray);  - 從類陣列（array-like）或是可迭代（iterable）物件建立一個新的 Array 實體

  * 複製物件的方式
    * 複製物件第一層內容
      * Object.assign({}, iAmObject, {add: value});
        * 第三引數可以增加或更新物件內容
    * 複製物件多層內容（clone deep）
      * JSON.parse(JSON.stringify(iAmArray));
        * JSON.stringify()：將物件轉為文字
        * JSON.parse()：將字串資料轉換成「JavaScript物件」

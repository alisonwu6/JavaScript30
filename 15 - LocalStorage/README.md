# 15 - LocalStorage

### 功能說明

* 透過localStorage來儲存使用者偏好，即使用者輸入的清單會保留下，不會因為更新或關閉視窗而消失。

### JavaScript - 客戶端儲存區
1. 本機端儲存(local storage)
  * lifetime：恆存，直到Web App被刪除，或是使用者要求瀏覽器刪除
  * scope：取決於來源。來源相同的所有文件會共享同一組localStroage資料
  * 用途：
    * 較長一段時間才需要變更（時程表、價目表），適合以離線方式儲存
    * 使用者可能會回訪且再次造訪（偏好、設定）
2. 連線期間儲存(session storage)
  * lifetime
    * 視窗被永久關閉時，資料將被刪除
    * 重起關閉分頁依然可以讀取資料
  * scope：取決於來源。受限於視窗，如兩個相同網站的分頁有各自的sessionStorage資料
  * 用途：
    * 經常性變更（是否登入、登入的位置資訊）
    * 個人資料且不允許裝置上的其他使用者瀏覽存取

### 功能邏輯說明
1. 當`addItems`表單`submit`後，啟動addItem函式
```
addItems.addEventListener('submit', addItem);
```
2. 
  * `e.preventDefault();` 防止預設的submit後更新頁面的動作
  * item被新增到items內後，使用populateList產生HTML畫面，並將輸入的資料儲存到本地端
  * LocalStorage.setItem(key,value)：用來儲存資料
```
function addItem(e) {
  e.preventDefault();
  const text = (this.querySelector('[name=item]')).value;
  const item = {
    text: text, // ES6 可將此行縮寫成 text,
    done: false
  }
  items.push(item);
  populateList(items, itemsList);
  localStorage.setItem('items', JSON.stringify(items));
  this.reset();
}
```
3. populateList函式創造HTML結構
  * `plates = []` 預設為空陣列
  * `platesList.innerHTML` 取代整個 `<ul class="plates">`的內容
  * map()輸出為陣列，透過join()將陣列轉換為接續的字串
```
function populateList(plates = [], platesList) {
  platesList.innerHTML = plates.map((plate, i) => {
    return `
      <li>
        <input type="checkbox" data-index=${i} id="item${i}" ${plate.done? 'checked' :''} />
        <label for="item${i}">${plate.text}</label>
      </li>
      `
  }).join('');
}
```
4. checkbox的切換與儲存在localStorage的設定
  * 此部分使用的**Event Delegation**(事件委派)
    * 將工作委派給祖先元件執行，不需要針對每一個子元件設置事件處理器，可提高效能與簡化程式碼
    * 此函式透過itemsList容器偵測子元件
  * 當.plates內的input被點擊，`items[index].done`真假值作切換
```
function toggleDone(e) {
  if (!e.target.matches('input')) return; // 保留input
  const el = e.target;
  const index = el.dataset.index;
  items[index].done = !items[index].done;
  localStorage.setItem('items', JSON.stringify(items));
  populateList(items, itemsList);
}

itemsList.addEventListener('click', toggleDone);
```
5. 當頁面載入將執行`populateList(items, itemsList);`，查看items是否有本地端儲存資料可取用，沒有就使用空陣列
```
const items = JSON.parse(localStorage.getItem('items')) || []; 
populateList(items, itemsList);
```
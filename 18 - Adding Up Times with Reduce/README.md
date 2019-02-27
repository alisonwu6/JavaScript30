# 18 - Adding Up Times with Reduce

### 功能說明
* 將HTML內的**data-time**時間加總後在console內顯示時分秒

### JavaScript
* 將取得的NodeList轉成Array
```
const timeNodes = Array.from(document.querySelectorAll('[data-time]'));
```
* 取得總秒數
  1. 第一個map：取得所有的data-time陣列資料
  2. 第二個map：將時間用split切成陣列，再透過第三個map將陣列值變成數字，最後將時間都轉成秒數
  3. 最後用reduce將所有秒數加總
```
const seconds = timeNodes
  .map(node => node.dataset.time)
  .map(timeCode => {
    const [mins, secs] = timeCode.split(":").map(parseFloat);
    return (mins * 60) + secs;
    })
  .reduce((total, vidSeconds) => total + vidSeconds);
```
* 將秒數變成時分秒
1. Math.floor：無條件捨去
2. %：用來取得餘數
```
let secondsLeft = seconds;
const hours = Math.floor(secondsLeft / 3600);
secondsLeft = secondsLeft % 3600;
const mins = Math.floor(secondsLeft / 60);
secondsLeft = secondsLeft % 60;
```
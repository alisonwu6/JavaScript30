# 09 - Dev Tools Domination

### 介紹console物件的除錯方法

* Regular
  ```
  console.log('hello');
  ```
* Interpolated：%s插入第二引數的字串
  ```
  console.log('Hello I am a %s', 'engineer');
  ```
* Styled：%c增加樣式
  ```
  console.log('%cChange style', 'color: green');
  ```
* warning：警示符號
  ```
  console.warn('OH NO!');
  ```
* Error：錯誤符號
  ```
  console.error('Error!');
  ```
* Info：資訊符號
  ```
  console.info('information');
  ```
* Testing：如果第一參數(測試結果)出現falsy值，就顯示第二參數的訊息內容。
  ```
  const p = document.querySelector('p');
  console.assert(p.classList.contains('ouch'), "That's wrong!");
  ```
* clearing：清除此行程式碼之前的console結果
  ```
  console.clear();
  ```
* Viewing DOM Elements：顯示指定的JavaScript物件
  ```
  console.dir(object);
  ```
* Grouping together：可將迭代的console值群組化，可使用group或groupCollapsed做開頭，結尾加上groupEnd
  ```
    dogs.forEach(dog => {
      // console.group(`${dog.name}`)
      console.groupCollapsed()(`${dog.name}`);
      console.log(`${dog.name}`);
      console.log(`This is ${dog.name}`);
      console.log(`${dog.name} is ${dog.age} years old`);
      console.log(`${dog.name} is ${dog.age * 7} dog years old`);
      console.groupEnd()(`${dog.name}`)
    })
  ```
* counting：可計算特定字串被呼叫幾次
  ```
  console.count('Wes');
  console.count('Wes');
  console.count('Steve');
  ```
* timing：計算console.time到console.timeEnd所需時間
  ```  
  console.time('fetching data');
  fetch('https://api.github.com/users/wesbos')
    .then(data => data.json())
    .then(data => {
      console.timeEnd('fetching data');
      // console.log(data);
    })
  ```
* table：把陣列以表格方式輸出
  ```
  console.table(dogs);
  ```
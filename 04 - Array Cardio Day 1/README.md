# 04 - Array Cardio Day 1

## 操作Array的.filter(),.map(),.sort(),.reduce()方法

### Array.prototype.filter(predicate)：回傳通過predicate測試的陣列元素，此為新陣列。
  * Filter the list of inventors for those who were born in the 1500's
  ```
  const fifteen = inventors.filter(inventor => (inventor.year >= 1500 && inventor.year < 1600));
  console.table(fifteen);  //可在console用table方式查看
  ```
### Array.prototype.map()：從舊的陣列元素計算出新的陣列元素
  * Give us an array of the inventors' first and last names
  ```
  const fullNames = inventors.map(inventor => `${inventor.first} ${inventor.last}`);
  ```
### Array.prototype.sort()：(in-place algorithm) 回傳排序後的原陣列
  * 引數
    * 不帶引數：按字母順序，暫時轉換成字串來做比較; 數字，即比較最大位數的數值大小
    * array.sort(a,b)
      * return a-b;  // 依據次序回傳 < 0, 0, > 0，由小到大
      * return b-a;  // 由大到小
  * Sort the inventors by birthdate, oldest to youngest，依據year由小到大
  ```
  const ordered = inventors.sort((a, b) => a.year > b.year ? 1 : -1);  
  ```
  * Sort the inventors by years lived，依據年齡，由大到小
  ```
  const oldest = inventors.sort((a, b) => {
    const lastInventor = a.passed - a.year;
    const nextInventor = b.passed - b.year;
    return lastInventor > nextInventor ? -1 : 1;
  })
  ```
  * Sort the people alphabetically by last name
    * 使用解構賦值語法
    * 用split()方法將string拆成array
  ```
  const alpha = people.sort((lastOne, nextOne) => {
    const [aLast, aFirst] = lastOne.split(', ');   // 解構賦值語法
    const [bLast, bFirst] = nextOne.split(', ');   // 依據","作為斷點
    return aLast > bLast ? 1 : -1;
  });
  ```
### Array.prototype.reduce()：從陣列元素計算出一個值
  * How many years did all the inventors live?
  ```
  const totalYears = inventors.reduce((total, inventor) => {
      return total + (inventor.passed - inventor.year);
    }, 0)   // 初始值
  ```
  * Sum up the instances of each of these
  ```
  const data = ['car', 'car', 'truck', 'truck', 'bike', 'walk', 'car', 'van', 'bike', 'walk', 'car', 'van', 'car',
    'truck'
  ];

  const transportation = data.reduce((obj, item) => {
    if (!obj[item]) {
      obj[item] = 0;
    }
    obj[item]++
    return obj;
  }, {});
  ```
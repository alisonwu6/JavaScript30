### 07 - Array Cardio Day 2

### 功能說明
* 使用Array的.some(),.every(),.find(),.findIndex(),.splice(),.slice方法

### Array.prototype.some()：測試陣列中是否至少有一個元素對一個predicate而言為true
  * 題目：is at least one person 19 or older?
    ```
    const isAdult = people.some(person => (new Date()).getFullYear() - person.year >= 19);
    ```
### Array.prototype.every()：測試一個predicate是不是對每一個陣列元素而言都為true
  * 題目：is everyone 19 or older?
    ```
    const allAdults = people.every(person => (new Date()).getFullYear() - person.year >= 19);
    ```

### Array.prototype.find()：回傳第一個滿足所提供之測試函式的元素值。否則回傳 undefined。
  * 題目：find the comment with the ID of 823423
    ```
    const comment = comments.find(comment => comment.id === 823423);
    ```
### Array.prototype.findIndex()：找到第一個符合敘述的元素
### Array.prototype.splice(include,deleteAmount,"addElement","addElement1"):插入、刪除、取代陣列元素
  * 題目：delete the comment with the ID of 823423
    ```
    const index = comments.findIndex(comment => comment.id === 823423);
    comments.splice(index, 1);
    ```
### Array.prototype.slice(include, exclude):回傳陣列的某一段子陣列
  * 題目：delete the comment with the ID of 823423
    ```
    const index = comments.findIndex(comment => comment.id === 823423);
    const newComments = [
      ...comments.slice(0, index),
      ...comments.slice(index + 1)
    ];
    ```


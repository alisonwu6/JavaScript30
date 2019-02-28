# 26 - Stripe Follow Along Nav

### 功能說明
* 

### JavaScript
* 使用**arrow function**可以繼承來自**parent function**的this值

* dropdown元素的寬高與位置設定
```
const dropdown = this.querySelector('.dropdown');
const dropdownCoords = dropdown.getBoundingClientRect();
const navCoords = nav.getBoundingClientRect();

const coords = {
  height: dropdownCoords.height,
  width: dropdownCoords.width,
  top: dropdownCoords.top - navCoords.top,
  left: dropdownCoords.left - navCoords.left
}
background.style.setProperty('width', `${coords.width}px`);
background.style.setProperty('height', `${coords.height}px`);
background.style.setProperty('transform', `translate(${coords.left}px, ${coords.top}px)`);
```


# 01 - JavaScript Drum Kit

### HTML設定
*參考JavaScript大全 - 15.4.3 Dataset屬性*
  * Dataset屬性：以”data-“開頭的屬性都會被視為合法的屬性
	  * 後續能用**data-key的值**與**鍵盤事件的e.keyCode**連結彼此

### JavaScript
1. “keydown” 後執行**playSound()**
	* 使用常數取audio tag `audio[data-key="${e.keyCode}"]`
	* 使用常數取.key tag `div[data-key="${e.keyCode}"]`
		* 非以上特定的keyCode外就直接跳出，避免回傳錯誤
		* target.classList.add("playing"); 加上css樣式
		* 讓keydown與聲音同步，設定每次按下時將audio.currentTime重置為0
	* console.dir(any object);  可透過此console查看audio特性或元素

2. 透過forEach()檢視每一個.key
	* NodeList可直接使用forEach()，建議可用console.log()查看NodeList的_proto_即可看到可以使用的方法
	* ”transitionend” 事件會在CSS transition結束後觸發
	
3. **removeTransition()** 移除.playing樣式
	* 針對單一個css屬性名稱做移除，因此排除propertyName !== ‘transform’
	* target.classList.remove("playing"); 移除css樣式






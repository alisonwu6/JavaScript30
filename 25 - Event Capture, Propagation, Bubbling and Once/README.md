# 25 - Event Capture, Propagation, Bubbling and Once

### 功能說明
* 探討事件的**捕獲**或**冒泡**的機制

### JavaScript
* addEventListener的第三個參數:
  * false(預設值)：冒泡機制(Bubbling)
  * true：捕獲機制(Capturing)
  * `once: true`：設定元素只能被觸發一次

* event.stopPropagation()：阻擋事件冒泡傳遞 
｀
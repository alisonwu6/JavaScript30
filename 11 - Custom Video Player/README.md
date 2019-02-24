# 11 - Custom Video Player

### HTML5 video
* 控制媒體播放的方法：
  * play()
  * pause()

* 透過addEventListener註冊媒體事件：
  * play：以調用play()方法，與autoplay屬性同等效果
  * pause：pause()方法被呼叫
  * timeupdate：currentTime特性已改變

### JavaScript
* 利用**三元運算子**，如果viedo.paused為真，使用video.play()；否則使用video.pause()
  ```
  function togglePlay() {
    video[video.paused ? 'play' : 'pause']();
  }
  ```
* 當this.paused為true，icon為'►';當this.paused為false，icon為'||'。
  ```
  function updateButton() {
    const icon = this.paused ? '►' : '||';
    toggle.textContent = icon;
  }
  ```
* 透過html內的data-skip="-10"與data-skip="25"，改變currentTime，並轉成浮點數
  ```
  function skip() {
    video.currentTime += parseFloat(this.dataset.skip); // to real number
  }
  ```
* 此部分已經在HTML內定義好min(允許的最小值)、max(允許的最大值)、step(區間值)、value(預設值)
  ```
  function handleRangeUpdate() {
    video[this.name] = this.value;
  }
  ```
* 處理影片進度條的樣式：取得進度條寬度的百分比，調整css的flex-basis值
  ```
  function handleProgress() {
    const percent = (video.currentTime / video.duration) * 100;
    progressBar.style.flexBasis = `${percent}%`;
  }
  ```
* 將currentTime的值改成scrubTime的值，即可在影片進度條上調整影片時間
  ```
  function scrub(e) {
    const scrubTime = (e.offsetX / progress.offsetWidth) * video.duration;
    video.currentTime = scrubTime;
  }
  ```
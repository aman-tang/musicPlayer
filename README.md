## 音乐播放器
### 功能：
1. 播放/暂停
2. 上一首/下一首
3. 音乐播放时间
4. 进度条
5. 播放列表

### 1.  API
#### 1. audioObject
创建或者获取的 audio 对象，可通过以下两种方式得到：
- **方法一：**
```
<audio id="music" src="http://cloud.hunger-valley.com/music/玫瑰.mp3">你的浏览器不支持喔！</audio>
<script>
var audioObject = document.querySelector('#music')
</script>
```
- **方法二：**
```
var audioObject = new Audio('http://cloud.hunger-valley.com/music/玫瑰.mp3')
```

#### 2. audioObject.play()
开始播放

#### 3. audioObject.pause()
暂停播放

#### 4. audioObject.autoplay()
设置或者获取自动播放状态：
```
audioObject.autoPlay = true  //设置为自动播放，下次更换 audioObject.src 后会自动播放音乐
audioObject.autoPlay = false //设置不自动播放
console.log(audioObject.autoPlay)
```

#### 5. audioObject.src
设置或者获取音乐地址：
```
audioObject.src = "http://cloud.hunger-valley.com/music/ifyou.mp3"
console.log(audioObject.src)
```

#### 6. audioObject.volume
设置或者获取音量，最大值为 1，0 为静音：
```
audioObject.volume = 0.5
audioObject.volume = 1
console.log(audioObject.volume)
```

#### 7. audioObject.loop
设置或者获取循环状态：
```
audioObject.loop = true
console.log(audioObject.loop)
```

#### 8. audioObject.duration
获取音乐长度，单位为秒：
```
console.log(audioObject.duration)
```

#### 9. audioObject.currentTime
设置或者获取播放时间：
```
console.log(audioObject.currentTime)
```

#### 10. audioObject.ended
判断音乐是否播放完毕，只读属性。

### 2. 事件
#### 1. playing
当音乐开始播放，暂停后重新开始播放，设置 currenTime 后开始播放时触发：
```
audioObject.addEventListener('playing', function(){
  console.log('playing')
})
```

#### 2. pause
当音乐暂停时和结束时触发：
```
audioObject.addEventListener('pause', function(){
  console.log('pause')
})
```

#### 3. ended
当音乐结束时触发：
```
audioObject.addEventListener('ended', function(){
  console.log('ended')
})
```

#### 4. timeupdate
当 currentTime 更新时会触发 timeupdate 事件，这个事件的触发频率由系统决定，但是会保证每秒触发 4-66 次（前提是每次事件处理不会超过250ms）：
```
//如下代码设置 每1秒左右执行一次
audioObject.shouldUpdate = true
audioObject.ontimeupdate = function(){
  var _this = this
  if(_this.shouldUpdate) {
     //do something
     console.log('update')
     _this.shouldUpdate = false
    setTimeout(function(){
      _this.shouldUpdate = true
    }, 1000)
  }
}
```

#### 5. volumechange
当音量改变时触发：
```
audioObject.onvolumechange = function(){
  console.log('volumechage')
})
```


<!--
 * @Author: be_loving@163.com 
 * @Date: 2024-10-22 18:49:23
 * @LastEditors: be_loving@163.com 
 * @LastEditTime: 2024-10-29 09:17:05
 * @FilePath: /vue3-wave-audio-player/README.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
# Vue 3 wave-audio-player

![Image demo](https://github.com/futuremeng/vue3-wave-audio-player/raw/master/preview.png)

## NPM install

``` sh
npm i @futuremeng/vue3-wave-audio-player
```

### Import ans use

``` html
<template>
  <div style="max-width: 250px">
    <Vue3WaveAudioPlayer
    :wave-width="250"
    :wave-height="40"
    wave-type="mirror"
    src="/samples/file.mp3"
    :index-self="0"
    :index-sync="index"
    @on-play="index = 0"
    title="第一交响曲"
    :wave-animation="false"
    :current-time-visible="false"
    :duration-time-visible="false"
    />  
    <!-- optional wave_options -->
    <Vue3WaveAudioPlayer
    :wave-width="250"
    :wave-height="40"
    :wave-options='{"samples":50}' 
    src="/samples/file.mp3"
    :load-audio-onmount="false"
    :index-self="1"
    :index-sync="index"
    @on-play="index = 1"
    title="第二交响曲"
    :wave-animation="false"
    :current-time-visible="false"
    :duration-time-visible="false"
    />  
    <Vue3WaveAudioPlayer
    :wave-width="250"
    :wave-height="40"
    :wave-options='{"samples":40,"type":"steps","width":192,"height":40}'
    src="/samples/file.mp3"
    :index-self="2"
    :index-sync="index"
    @on-play="index = 2"
    title="第三交响曲"
    :wave-animation="false"
    :current-time-visible="false"
    :duration-time-visible="false"
    />   
  </div>
</template>
<script>
import Vue3WaveAudioPlayer from 'vue3-wave-audio-player'

export default {
  name: 'App',
  components: {
    Vue3WaveAudioPlayer
  },
  data() {
    return {
      index: 0
    }
  }
}
</script>
```

### Attributes

Name | Required | Type | Description
--- | --- | --- | ---
src | True | audio file | Source path to audio file
title | False | String | Title of the player
wave-width | True | Integer | Width of the Waves. (Not responsive, Also remember that the buttons and the timing strings will take extra ~250px. For example, if(container === 500px) => wave-width = 500 - 250 = 250  )
wave-height | True | Integer | Height of the waves (Not Responsive)
wave-type | False | String | Type of wave. (Not working yet)
wave-options | False | Object | Set settings for the waves (Not working yet)
load-audio-onmount | False | Boolean | Load the path and audio data on mounted
disable-seeking | False | Boolean | Disable time seeking
current-time-visible | False | Boolean | Show current time
duration-time-visible | False | Boolean | Show duration time
index-self | False | Integer | Index of the player (for multiple players)
index-sync | False | Integer | Index of the playing player to sync with (for multiple players)
disable-seeking | False | Boolean | Disable seeking
load-audio-onmount | False | Boolean | Load the path and audio data on mounted

### Events

I have added all the events that html has in the audio tag with a "on-" prefix.
Additional events:

Name | Required | Type | Return | Description
--- | --- | --- | --- | ---  
tried_to_seek | False | Func  | Boolean | Triggered when user try to seek time
on-play | False | Func  | Boolean | Triggered when user click on play button

``` html
// Example 
<Vue3WaveAudioPlayer
:wave-width="250"
:wave-height="40"
src="/samples/file.mp3"

@on-error="onError"
@on-ended="customCallback" // ... many more
/> 
```

Check [MDN Doc](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio) for all the events.

### Report bug or Suggestion

please send a mail at <futuremeng@gmail.com> or <imdarif122@mail.com> or <contact@arifdev.com>.
You can also open any issue in the [GitHub](https://github.com/futuremeng/vue3-wave-audio-player) page. Thanks for using this package.

### Inspired by

[wave-path-audio-player](https://www.npmjs.com/package/wave-audio-path-player) package
[waveform-path](https://jerosoler.github.io/waveform-path) package

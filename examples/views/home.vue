<!--
 * @Author: be_loving@163.com 
 * @Date: 2024-10-23 13:32:11
 * @LastEditors: be_loving@163.com 
 * @LastEditTime: 2024-10-23 14:46:23
 * @FilePath: /vue3-wave-audio-player/examples/views/home.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<template>
    <div style="max-width: 250px">
  
      <Vue3WaveAudioPlayer
      :wave_width="250"
      :wave_height="40"
      wave_type="mirror"
      src="http://m701.music.126.net/20241023150909/9e1d0da9dc65beec4c626fee14b65686/jdymusic/obj/wo3DlMOGwrbDjj7DisKw/11780012672/f264/9861/56fc/bba3a062ee035638eb2f424bebba5ed9.mp3"
      :disable_seeking="true"
      @tried_to_seek="tried_to_seek"
      />  
      
      <!-- optional wave_options -->
      <Vue3WaveAudioPlayer
      :wave_width="250"
      :wave_height="40"
      :wave_options='{"samples":50}' 
      src="http://m701.music.126.net/20241023150909/9e1d0da9dc65beec4c626fee14b65686/jdymusic/obj/wo3DlMOGwrbDjj7DisKw/11780012672/f264/9861/56fc/bba3a062ee035638eb2f424bebba5ed9.mp3"
      :load_audio_onmount="false"
      />  
      <Vue3WaveAudioPlayer
      @tried_to_seek="tried_to_seek"
      :wave_width="250"
      :wave_height="40"
      :wave_options='{"samples":40,"type":"steps","width":192,"height":40}'
      src="http://m701.music.126.net/20241023150909/9e1d0da9dc65beec4c626fee14b65686/jdymusic/obj/wo3DlMOGwrbDjj7DisKw/11780012672/f264/9861/56fc/bba3a062ee035638eb2f424bebba5ed9.mp3"
      />  
      <Vue3WaveAudioPlayer
      :wave_width="250"
      :wave_height="40"
      :wave_options="example_options"
      src="http://m701.music.126.net/20241023150909/9e1d0da9dc65beec4c626fee14b65686/jdymusic/obj/wo3DlMOGwrbDjj7DisKw/11780012672/f264/9861/56fc/bba3a062ee035638eb2f424bebba5ed9.mp3"
      />  
    </div>
  </template>
  
  <script>
  import Vue3WaveAudioPlayer from '../../packages/index.vue'
  
  export default {
    components: {
      Vue3WaveAudioPlayer
    },
    data () {
      return {
        example_options: {
          'samples':50,'type':'steps',
          'paths': [
            {'d':'V','sy':0,'x':0,'ey':100},
            {'d':'A','sx':0,'sy':100,'ex':100,'ey':100,'rx':10,'ry':10,'angle':180,'arc':1,'sweep':1},
            {'d':'V','sy':0,'x':100,'ey':100}
          ]
        }
      }
    },
    methods: {
      onError (e) {
        console.log(e)
      },
      tried_to_seek (didSkip) {
        if(didSkip)
          console.log('Player skipped')
        else
          console.log('Player skip blocked')
      }
    }
  }
  </script>
  
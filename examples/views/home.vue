<!--
 * @Author: be_loving@163.com 
 * @Date: 2024-10-23 13:32:11
 * @LastEditors: be_loving@163.com 
 * @LastEditTime: 2024-10-28 13:45:21
 * @FilePath: /vue3-wave-audio-player/examples/views/home.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<template>
  <div style="max-width: 250px">
    <Vue3WaveAudioPlayer
      :wave-width="250"
      :wave-height="40"
      wave-type="mirror"
      src="https://one-ywcbs-static.oss-cn-beijing.aliyuncs.com/abc.mp3"
      :disable-seeking="true"
      @tried_to_seek="tried_to_seek"
    />

    <!-- optional wave-options -->
    <Vue3WaveAudioPlayer
      :wave-width="250"
      :wave-height="40"
      :wave-options="{ samples: 50 }"
      src="https://one-ywcbs-static.oss-cn-beijing.aliyuncs.com/abc.mp3"
      :load-audio-onmount="false"
    />
    <Vue3WaveAudioPlayer
      @tried_to_seek="tried_to_seek"
      :wave-width="250"
      :wave-height="40"
      :wave-options="{ samples: 40, type: 'steps', width: 192, height: 40 }"
      src="https://one-ywcbs-static.oss-cn-beijing.aliyuncs.com/abc.mp3"
    />
    <Vue3WaveAudioPlayer
      :wave-width="250"
      :wave-height="40"
      :wave-options="example_options"
      src="https://one-ywcbs-static.oss-cn-beijing.aliyuncs.com/abc.mp3"
    />
  </div>
</template>

<script>
import Vue3WaveAudioPlayer from '../../packages/index.vue'

export default {
  name: 'HomePage',
  components: {
    Vue3WaveAudioPlayer,
  },
  data() {
    return {
      example_options: {
        samples: 50,
        type: 'steps',
        paths: [
          { d: 'V', sy: 0, x: 0, ey: 100 },
          {
            d: 'A',
            sx: 0,
            sy: 100,
            ex: 100,
            ey: 100,
            rx: 10,
            ry: 10,
            angle: 180,
            arc: 1,
            sweep: 1,
          },
          { d: 'V', sy: 0, x: 100, ey: 100 },
        ],
      },
    }
  },
  methods: {
    onError(e) {
      console.log(e)
    },
    tried_to_seek(didSkip) {
      if (didSkip) console.log('Player skipped')
      else console.log('Player skip blocked')
    },
  },
}
</script>

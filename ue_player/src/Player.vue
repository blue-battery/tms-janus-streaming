<template>
  <div id="player">
    <div v-if="source==='test'">
      <playtest :duration="duration" />
    </div>
    <div v-else-if="source==='video'">
      <playvideo :file="file" :seek="seek" />
    </div>
    <div v-else-if="source==='audio'">
      <playaudio :file="file" :seek="seek" />
    </div>
    <div v-else>
      <div>无法识别的类型</div>
    </div>
  </div>
</template>

<script>
import queryString from 'query-string'
import Playvideo from './components/Playvideo.vue'
import Playaudio from './components/Playaudio.vue'
import Playtest from './components/Playtest.vue'

function setPlayerParameters(vm, params) {
  switch (params.source) {
    case 'test':
      vm.duration = parseInt(params.duration) || 10
      break
    case 'video':
    case 'audio':
      vm.file = params.file
      vm.seek = params.seek
      break
  }
  vm.source = params.source
}

export default {
  name: 'Player',
  components: {
    Playtest,
    Playvideo,
    Playaudio
  },
  data() {
    return {
      source: 'test',
      duration: 10,
      file: '',
      seek: ''
    }
  },
  created() {
    const query = queryString.parse(location.search)
    if (query.source) {
      setPlayerParameters(this, query)
    }
  }
}
</script>

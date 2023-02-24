<template>
  <div class="home">
    <MatchHistory />
  </div>
</template>

<script>
// @ is an alias to /src
import MatchHistory from '@/components/MatchHistory.vue'

export default {
  name: 'HomeView',
  components: {
    MatchHistory
  }
}
</script>

<template>
  <MustacheEditor />
</template>

<script lang="ts">
import Vue from 'vue'
import MustacheEditor from '~/components/organism/mustacheEditor.vue'

export default Vue.extend({
  name: 'IndexPage',
  components: { MustacheEditor },
})
</script>

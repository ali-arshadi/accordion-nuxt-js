<template>
  <div class="accordion-wrapper">
    <Accordion />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  components: {
    Accordion: () => import('@/components/modules/accordion.vue'),
  },
})
</script>

<style lang="scss" scoped></style>

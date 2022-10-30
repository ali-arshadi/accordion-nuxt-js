<template>
  <div class="page-wrapper">
    <div class="accordion-component-wrapper">
      <Accordion :accordionData="accordion" />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  data() {
    return {
      accordion: [
        {
          id: '1234sdlkfj1',
          title: 'this is test data',
          description: 'this is test description',
        },
        {
          id: 'alskdfjk14512k4lj',
          title: 'this is test data',
          description: 'this is test description',
        },
        {
          id: '2103948akldfsj',
          title: 'this is test data',
          description: 'this is test description',
        },
      ],
    };
  },
  components: {
    Accordion: () => import('@/components/modules/accordion.vue'),
  },
});
</script>

<style lang="scss" scoped>
.page-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.accordion-component-wrapper {
  width: 50%;
  margin-top: 100px;
}
</style>

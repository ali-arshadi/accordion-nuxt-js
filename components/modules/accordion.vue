<template>
  <div class="accordion-container-wrapper">
    <div
      class="accordion-wrapper"
      v-for="(accordion, index) in accordionData"
      :key="accordion.id"
    >
      <div class="accordion-title-wrapper" @click="toggleAccordion(index)">
        <p>{{ accordion.title }}</p>
      </div>
      <div :class="['accordion-description-wrapper']">
        <p>{{ accordion.description }}</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
export default Vue.extend({
  props: ['accordionData'],
  data() {
    return {
      isOpen: false as boolean,
    };
  },
  methods: {
    toggleAccordion(index: number) {
      const elementInfo = document.querySelectorAll(
        '.accordion-description-wrapper'
      )[index] as HTMLElement;

      const elementStyle = getComputedStyle(elementInfo);

      const elementDisplay = elementStyle.display;

      if (elementDisplay == 'none') {
        elementInfo.style.display = 'block';
      } else {
        elementInfo.style.display = 'none';
      }
    },
  },
});
</script>

<style lang="scss" scoped>
.accordion-container-wrapper {
  width: 100%;
}
.accordion-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
.accordion-title-wrapper {
  align-self: flex-start;
  background-color: rgb(171, 162, 255);
  width: 100%;
  padding: 10px;
}
.accordion-description-wrapper {
  align-self: flex-start;
  width: 100%;
  background-color: rgb(224, 240, 168);
  padding: 10px;
  display: none;
}
</style>

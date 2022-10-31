<template>
  <div class="accordion-container-wrapper">
    <div
      :class="['accordion-wrapper', active === index ? 'active' : '']"
      v-for="(accordion, index) in accordionData"
      :key="accordion.id"
      @click="toggleAccordion"
    >
      <p class="accordion-title-wrapper">{{ accordion.title }}</p>
      <p class="accordion-description-wrapper">{{ accordion.description }}</p>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
export default Vue.extend({
  props: ['accordionData'],
  data() {
    return {
      active: null as any,
      isOpen: false as boolean,
    };
  },
  methods: {
    toggleAccordion(e: any) {
      //* variables
      const parentElement = e.target.parentElement;

      const descriptionElement = parentElement.querySelector(
        '.accordion-description-wrapper'
      );

      const descriptionElementMaxHeight = descriptionElement.scrollHeight;

      const allItems = document.querySelectorAll('.accordion-wrapper');

      //*check element have active class or not
      if (parentElement.classList.contains('active')) {
        //* remove active class and max height from item
        parentElement.classList.remove('active');
        descriptionElement.style.maxHeight = null;
      } else {
        //* remove active class and max height from all items
        allItems.forEach((element: any) => {
          element.classList.remove('active');
          element.querySelector(
            '.accordion-description-wrapper'
          ).style.maxHeight = null;
        });
        //* add active class and max height for clicked item
        parentElement.classList.add('active');
        descriptionElement.style.maxHeight = `${
          descriptionElementMaxHeight + 40
        }px`;
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
  position: relative;
  &:after {
    content: '';
    width: 10px;
    height: 2px;
    position: absolute;
    top: 14px;
    right: 14px;
    background-color: black;
  }
  &:before {
    content: '';
    transition: all linear 0.2s;
    width: 10px;
    height: 2px;
    position: absolute;
    top: 14px;
    right: 14px;
    transform: rotate(90deg);
    background-color: black;
  }
  .accordion-title-wrapper {
    align-self: flex-start;
    background-color: rgb(171, 162, 255);
    width: 100%;
    padding: 10px;
    cursor: pointer;
  }
  .accordion-description-wrapper {
    align-self: flex-start;
    width: 100%;
    background-color: rgb(224, 240, 168);
    transition: 0.3s all linear;
    max-height: 0;
    overflow: hidden;
  }
  &.active {
    .accordion-description-wrapper {
      padding: 10px;
    }
    &:before {
      transform: rotate(180deg);
    }
  }
}
</style>

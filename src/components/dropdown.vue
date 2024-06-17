<script setup lang="ts">
import { computed, ref } from 'vue'
// const props = defineProps({
//   bgcolor: {
//     type: String,
//     required: false,
//     default: 'primary'
//   },
//   inputID: {
//     type: String,
//     required: true
//   },
//   TargetNumber: {
//     type: Number,
//     required: false
//   },
//   StrTargetNumber: {
//     type: String,
//     required: false
//   }
// })

// const emits = defineEmits<{
//   (e: 'change-BPM', id: string): void
// }>()

// const BPMEmit = () => {
//   emits('change-BPM', props.inputID)
// }

// //css style
// const inputBgColor = ref(
//   computed(() => {
//     if (props.bgcolor) {
//       return props.bgcolor
//     }
//     return 'primary'
//   })
// )
</script>

<template>
  <div class="dropdown">
    <div class="dropdown-select">
      <span class="selectitem">selected item</span>
      <i class="icon">push</i>
    </div>
    <div class="dropdown-list">
      <div class="dropdown-list__item">pepsi</div>
      <div class="dropdown-list__item">coca</div>
      <div class="dropdown-list__item">monster</div>
    </div>
  </div>
</template>

<style scoped>
.selectitem {
  border-bottom: 3px solid black;
}
.dropdown {
  position: relative;
  width: 30rem;
}

.dropdown:hover .dropdown-list {
  opacity: 1;
  visibility: visible;
}

.dropdown-select {
  padding: 1.5rem;
  border-radius: 4px;
  background-color: aqua;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 1.6rem;
  cursor: pointer;
}

.dropdown-list {
  border-radius: 4px;
  background-color: green;
  position: relative;
  width: 110%;
  /* top: 110%;
  left: 0;
  right: 0;
  opacity: 0; */
  visibility: hidden;
  transition:
    opacity 0.2s linear,
    visibility 0.2s linear;
}

.dropdown-list__item {
  padding: 1rem;
  font-size: 1.4rem;
}
</style>

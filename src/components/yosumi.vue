<script setup lang="ts">
import { computed, ref } from 'vue'
import { renderToWebStream } from 'vue/server-renderer'
const props = defineProps({
  bgcolor: {
    type: String,
    required: false,
    default: 'primary'
  },
  inputID: {
    type: String,
    required: true
  },
  TargetNumber: {
    type: Number,
    required: false
  },
  StrTargetNumber: {
    type: String,
    required: false
  }
})

const emits = defineEmits<{
  (e: 'change-BPM', id: string): void
}>()

const BPMEmit = () => {
  emits('change-BPM', props.inputID)
}

//css style
const inputBgColor = ref(
  computed(() => {
    if (props.bgcolor) {
      return props.bgcolor
    }
    return 'primary'
  })
)
</script>

<template>
  <div class="wrapper">
    <input
      @keydown.enter="BPMEmit"
      onclick="this.select()"
      :value="props.StrTargetNumber"
      class="numeric"
      :id="props.inputID"
    />
  </div>
  <p>{{ props.TargetNumber }}</p>
</template>

<style scoped>
.wrapper {
  text-align: center;
  width: 60px; /* need */
  margin: 12px 0px 12px 30px;
  height: 18px;
  font-size: 13px; /* need */
  position: relative;
  background-color: v-bind(inputBgColor);
  border: 1px solid v-bind(inputBgColor);
  &.wrapper:focus-within {
    border: solid 1px rgb(169, 232, 44);
  }
}
.wrapper::before,
.wrapper::after {
  position: absolute;
  content: '';
  display: block;
  background-color: v-bind(inputBgColor);
}
.wrapper::before {
  top: -1px;
  bottom: -1px;
  left: 3px;
  right: 3px;
}
.wrapper::after {
  top: 3px;
  bottom: 3px;
  left: -1px;
  right: -1px;
}
.wrapper input {
  position: relative;
  width: calc(100% - 6px);
  font-size: calc(100% - 1px);
  border: none;
  padding-top: -1px;
  margin-bottom: 1px;
  border-bottom: 1px solid black;
  background-color: v-bind(inputBgColor);
  text-align: center;
  outline: none;
  z-index: 1;
}
.wrapper input::selection {
  background: yellow;
}

/* script内でcssの要素を変更したい場合はquerySelector */
</style>

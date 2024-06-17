<script setup lang="ts">
import { ref } from 'vue'
import Yosumi from './components/yosumi.vue'
import Dropdown from './components/dropdown.vue'

//For BPMcounter
const BPMcounter = ref(120.0)
const FixedBPMcounter = ref(BPMcounter.value.toFixed(1))

let toRenewBPM: number

const decimalDetect = (id: string) => {
  ;(document.getElementById(id) as HTMLInputElement).blur()
  if (!Number.isNaN((toRenewBPM = +(document.getElementById(id) as HTMLInputElement).value))) {
    BPMcounter.value = toRenewBPM
  }
  FixedBPMcounter.value = BPMcounter.value.toFixed(1)
  ;(document.getElementById(id) as HTMLInputElement).value = FixedBPMcounter.value
}

//For MIDIchannel Setting
const MIDIchannel = ref(1)
const strMIDIchannel = ref(MIDIchannel.value.toString())
let toRenewMIDI: number

const intDetect = (id: string) => {
  ;(document.getElementById(id) as HTMLInputElement).blur()
  if (Number.isInteger((toRenewMIDI = +(document.getElementById(id) as HTMLInputElement).value))) {
    MIDIchannel.value = toRenewMIDI
  }
  strMIDIchannel.value = MIDIchannel.value.toString()
  ;(document.getElementById(id) as HTMLInputElement).value = strMIDIchannel.value
}

let decimalPattern = /^\d+\.\d*$/
</script>

<template>
  <div class="app">
    <div class="text-input" id="text-input1">
      <p>{{ BPMcounter.toFixed(1) }}</p>
      <Yosumi
        bgcolor="darkturquoise"
        id="yosumi1"
        inputID="yosumiInput1"
        :TargetNumber="BPMcounter"
        :StrTargetNumber="FixedBPMcounter"
        @change-BPM="decimalDetect"
      />
    </div>
    <div class="text-input" id="text-input2">
      <p>{{ MIDIchannel }}</p>
      <Yosumi
        bgcolor="green"
        id="yosumi2"
        inputID="yosumiInput2"
        :TargetNumber="MIDIchannel"
        :StrTargetNumber="strMIDIchannel"
        @change-BPM="intDetect"
      />
    </div>
    <div class="select-opt" id="select-opt1">
      <select id="select1">
        <option>1</option>
        <option>2</option>
        <option>3</option>
      </select>
      <img src="./img/test.png" />
    </div>
    <div class="dropdown-vue">
      <Dropdown />
    </div>
  </div>
  <!-- <Yosumi bgcolor="gray" id="yosumi3" inputID="yosumiInput3" /> -->
</template>

<style scoped>
/* https://ginneko-atelier.com/blogs/entry393/ */
.app {
  /* display: flex; */
  flex-wrap: wrap;
  width: 600px;
  height: 1000px;
  background-color: aquamarine;
}
.text-input {
  display: flex;
  flex-wrap: wrap;
  font-size: 14px;
  width: 500px;
  height: 40px;
  background-color: darkturquoise;
}
</style>

<script setup>
import { ref } from 'vue'


const display = ref('')


const displayNumber = (x) => {
  display.value += x
}

const clearNumber = () => {
  display.value = ''
}

const displayResult = () => {
      try {
        display.value = eval(display.value)
        if (Number.isInteger(display.value) == false){
          display.value = Number(display.value).toFixed(5)
        }
      } catch (error) {
        display.value = 'Error'
      }
    }


</script>


<template>
  <div class='calculator flex flex-col items-center py-12 '>
  
     
      <input class="display-numbers rounded bg-lime-400 text-2xl text-right w-80" type="text" v-model="display" readonly>

   
    <div class="button-numbers rounded grid grid-cols-4 gap-2 bg-slate-500 text-white px-4 w-80 h-96">
      <button class="w-12 h-12" @click="clearNumber()">C</button>
      <div class="grid grid-cols-subgrid gap-4 col-span-3">
        <button class="col-start-3" @click="displayNumber('/')">/</button>
      </div>
      <button class="w-12 h-12" @click="displayNumber('7')">7</button>
      <button class="w-12 h-12" @click="displayNumber('8')">8</button>
      <button class="w-12 h-12" @click="displayNumber('9')">9</button>
      <button class="w-12 h-12" @click="displayNumber('*')">x</button>
      <button class="w-12 h-12" @click="displayNumber('4')">4</button>
      <button class="w-12 h-12" @click="displayNumber('5')">5</button>
      <button class="w-12 h-12" @click="displayNumber('6')">6</button>
      <button class="w-12 h-12" @click="displayNumber('-')">-</button>
      <button class="w-12 h-12" @click="displayNumber('1')">1</button>
      <button class="w-12 h-12" @click="displayNumber('2')">2</button>
      <button class="w-12 h-12" @click="displayNumber('3')">3</button>
      <button class="w-12 h-12" @click="displayNumber('+')">+</button>
      <button class="w-12 h-12" @click="displayNumber('0')">0</button>
      <div class="grid grid-cols-subgrid gap-4 col-span-2">
        <button class="col-start-3" @click="displayNumber('.')">.</button>
      </div>
      <button class="w-12 h-12" @click="displayResult()">=</button>
    </div>
    
  </div>
</template>

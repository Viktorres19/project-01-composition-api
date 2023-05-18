<template>
  <div class="home">

    <h2>{{ appTitle }}</h2>

    <h3>{{ counterData.title }}:</h3>
    <div>
      <button @click="decreaseCounter(1)">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter(1)">+</button>
    </div>
    <p>This counter is {{ oddOrEven }}</p>
    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterData.title" type="text" v-autofocus>
    </div>
  </div>
</template>

<script setup>
import {reactive, computed, watch, onMounted } from 'vue'
import {vAutofocus} from '@/directives/vAutofocus'

const appTitle = 'My Ok Counter App'

onMounted(() => {
  console.log('Do stuff related to App Title')
})

const counterData = reactive({
  count: 0,
  title: 'My counter'
})

watch(() => counterData.count, (newCount) => {
  if (newCount === 20) {
    alert('Way to go! You made it to 20!!')
  }
})

const oddOrEven = computed(() => {
  if (counterData.count % 2 === 0) return 'even'
  return 'odd'
})

const increaseCounter = amount => {
  counterData.count += amount
}

const decreaseCounter = amount => {
  counterData.count -= amount
}

onMounted(() => {
  console.log('Do stuff related to Counter')
})

/*Directives*/
/*const vAutofocus = {
  mounted: (el) => {
    el.focus()
  }
}*/

/* onBeforeUpdate(() => {
  console.log('onBeforeUpdate')
})
onUpdated(() => {
  console.log('onUpdated')
}) */

/* onBeforeMount(() => {
  console.log('onBeforeMount')
})
onMounted(() => {
  console.log('onMounted')
})
onBeforeUnmount(() => {
  console.log('onBeforeUnmount')
})
onUnmounted(() => {
  console.log('onUnmounted')
})
onActivated(() => {
  console.log('onActivated')
})
onDeactivated(() => {
  console.log('onDeactivated')
}) */
</script>

<style>
.home {
  text-align: center;
  padding: 20px;
}
.btn, .counter {
  font-size: 40px;
  margin: 10px;
}
.edit {

}
</style>

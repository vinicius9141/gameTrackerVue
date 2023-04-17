
<template>
  <Header />

  <div class="container flex wrap gap justify-center">
    <Card v-for="item in data" :key="item" :item='item' />
  </div>
</template>

<style scoped>

</style>

<script setup>
// import Card from './components/Card.vue';
import Header from './components/Header.vue';
import { ref, onMounted, defineAsyncComponent } from 'vue';

const data = ref([{name: ''}])
const Card = defineAsyncComponent(()=>import ('./components/Card.vue'))

  onMounted(async ()=>{
    const response = await fetch('https://www.cheapshark.com/api/1.0/deals?pageNumber=0&pageSize=12&storeID=1&onSale=1&AAA=1')
    const res = await response.json()
    data.value = res
    console.log(res[0].thumb)
  })


</script>

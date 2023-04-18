
<template>
  <Header />

  <div class="container flex wrap gap justify-center">
    <div class="navigation-area ">
      <p class="offer">Ofertas</p>
      <div class="buttons-area">
        <input class="shadow" type="text" placeholder="Procurar" v-model="search" @keydown="$event=>filtered($event)">
        <div>
          <span class="order-by shadow">Ordenar por:</span>
          <select class="select shadow" name="select" @change="$event=>selecao($event)">
            <option value="discount" selected>% de Desconto</option>
            <option value="normalPrice">Maior Preço</option>
            <option value="salePrice">Menor Preço</option>
            <option value="title">Titulo</option>
          </select>
        </div>
        
      </div>
    </div>
    <Card v-for="item in data" :key="item" :item='item' />
  </div>
  <div class="flex align-center justify-center">
    <Button />
  </div>
  <Footer />
</template>


<script setup>
import Header from './components/Header.vue';
import Button from './components/Button.vue';
import Footer from './components/Footer.vue';
import { ref, onMounted, defineAsyncComponent } from 'vue';

const data = ref([{ name: '' }])
const dataServe = ref([{ name: '' }])
const Card = defineAsyncComponent(() => import('./components/Card.vue'))

onMounted(async () => {
  const response = await fetch('https://www.cheapshark.com/api/1.0/deals?pageNumber=0&pageSize=33&storeID=1&onSale=1&AAA=1')
  const res = await response.json()
  const resMap = res.map(game => {
      const subPrice = game.normalPrice - game.salePrice
      const discount = ((subPrice * 100) / game.normalPrice).toFixed(0).replace(".", ",")
      return {...game , discount}
  })
  dataServe.value = resMap
  data.value = resMap

})

let timeout
function filtered(e){
  clearTimeout(timeout)
  timeout = setTimeout(()=>{
   data.value = dataServe.value.filter(game => game?.title.toLowerCase().includes(e.target.value.toLowerCase()))
  }, 1000)
}

function selecao(e){
  data.value = dataServe.value.sort((a , b)=> a[e.target.value].localeCompare(b[e.target.value]) )
}
</script>

<style scoped>
  .navigation-area{
    width: 100%;
  }

  .offer{
    font-size: 3.6rem;
    font-weight: 300;
    color:#fff;
    margin-top: 4.5rem;
  }
@media (max-width: 768px){
  .offer{
    display: flex;
    justify-content: center;
  }
}
  .buttons-area{
    width: 100%;
    display: flex;
    justify-content: space-between;
    margin-top: 2.2rem;
  }
  @media (max-width: 768px){
  .buttons-area {
  padding: 0 2rem;
  }
}

  .buttons-area > input{
    width: 38rem;
    height: 5rem;
    border-radius: var(--radius);
    border: none;
    background: var(--blue);
    padding: 1.5rem ;
    color: #fff;
    font-size: 1.8rem;
    font-weight: 100;
  }
  @media (max-width: 768px){
  .buttons-area > input{
    width: 20rem;
    height: 5rem;
    font-size: 1.4rem;
    margin-top: 2.2rem;
  }
}
  .buttons-area > input::placeholder{
    font-size: 1.8rem;
    font-weight: 100;
    color: #ffffff70;
  }

  .select{
    width: 18rem;
    height: 5rem;
    background: var(--blue);
    color: #ffffff70;;
    border-radius: var(--radius);
    font-size: 1.8rem;
    font-weight: 100;
    padding: 1.3rem;
    cursor: pointer;;
  }
@media (max-width: 768px){
  .select{
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 1.4rem;
    width: 14rem;
    height: 5rem;
  }
}
  .order-by{
    color: #fff;
    font-size: 1.8rem;
    font-weight: 700;
    margin-right: 2rem;
  }


</style>


<script setup>

//   const item = {
//     "internalName": "SHADOWTACTICSBLADESOFTHESHOGUN",
//     "title": "Shadow Tactics: Blades of the Shogun",
//     "metacriticLink": "\/game\/pc\/shadow-tactics-blades-of-the-shogun",
//     "dealID": "j2lexFQ%2Fx%2FOeqECYZgxWgBxj7YX3hcQs0N3Y8mn8kHk%3D",
//     "storeID": "1",
//     "gameID": "158443",
//     "salePrice": "3.99",
//     "normalPrice": "39.99",
//     "isOnSale": "1",
//     "savings": "90.022506",
//     "metacriticScore": "85",
//     "steamRatingText": "Overwhelmingly Positive",
//     "steamRatingPercent": "96",
//     "steamRatingCount": "26908",
//     "steamAppID": "418240",
//     "releaseDate": 1480982400,
//     "lastChange": 1681594022,
//     "dealRating": "9.5",
//     "thumb": "https:\/\/cdn.cloudflare.steamstatic.com\/steam\/apps\/418240\/capsule_sm_120.jpg?t=1674570965"
// }


  const props  = defineProps({item:null})
 

  const { thumb, title, normalPrice, salePrice, discount } = props.item

  


  if(discount <= 0){
    discount = 'Gratis'
  }
  
</script>

<template>
  <article class="card">
    <div class="card-img">
      <img :src= 'thumb'  alt="">
    </div>

    <div class="card-details">
      <div class="card-footer">
        <h1>{{ title }}</h1>

        <div class="card-items-footer">
          <button>Detalhes</button>
          <div class="flex">
           <div class="card-price">
             <span class="old-price">$ {{ normalPrice?.replace('.' , ',') }}</span>
              <span class="new-price">$ {{ salePrice?.replace('.' , ',') }}</span>
           </div>
            <div class="discount">
              -{{ discount }}%
            </div>
          </div>
        </div>
      </div>
    </div>
  </article>
</template>

<style scoped>
@import '../styles/variables.css';
 
.card{
    /* background:coral; */
    width: 38rem;
    height: 25.1rem;
    border-radius: var(--radius);
    overflow: hidden;
    background: var(--blue);

  }

   .card-image, img{
    width: 100%;
  }
  .card-details{
    height: 10.4rem;
  }

.card-footer{
  padding: .7rem 1.6rem 0;
}
  .card-footer h1{
    color: #fff;
    font-size: 2.4rem;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
    font-weight: 300;
    margin-bottom: 1.4rem;
  }
  .card-items-footer{
    display: flex;
    align-items: center;
    justify-content: space-between;
    color: #fff;
  }

  .card-items-footer > button{
    width: 11.6rem;
    height: 3.9rem;
    color: #fff;
    border-radius: var(--radius);
    border: none;
    background: var(--pink);
    font-weight: 700;
    font-size: 1.8rem;
    text-transform: uppercase;
  }

  .card-price{  
    display: flex;
    flex-direction: column;
    text-align: center;
  }
  .old-price{
    color: #ffffff57;
    text-decoration: line-through;
    font-weight: 100;
    font-size: 1.2rem
  }

  .new-price{
    font-size: 1.8rem;
  }

  .discount{
    display: flex;
    align-items: center;
    justify-content: center;
    width: 8.4rem;
    height: 3.9rem;
    border-radius: var(--radius);
    background: var(--green);
    text-transform: uppercase;
    font-weight: 700;
    font-size: 1.8rem;
    color: #fff;
    margin-left: 1.0rem;
  }
</style>
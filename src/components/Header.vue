<script setup>

  const logo = './src/assets/img/logo-tracker.png'

</script>


<template>
  <section class="flex align-center">
      <nav class="nav-bar container">
        <img :src="logo" >
        <h1>Game <span>Tracker</span></h1>
    </nav>
  </section>
</template>

<style scoped>
@import '../styles/variables.css';

section {
  background: var(--blue);
}
.nav-bar {
  width: 100%;
  display: flex;
  align-items: center;
  height: 5rem;
  background: var(--blue);
  font-size: 2.4rem;
  color: #fff;
}

@media (max-width: 768px){
  .nav-bar{
    justify-content: center;
  }
}
.nav-bar img{
  margin-right: 1.134rem;
}
.nav-bar > h1 {
  font-weight: 300;
}

.nav-bar , span{
  font-weight: 700;
}
</style>
<script setup>

  const logo = '../../src/assets/img/logo-tracker.png'
  const textFooter = '© 2021, Game Tracker Inc. Todos os direitos reservados. Nulla facilisi. Etiam sagittis congue tempor. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Suspendisse eu velit et ante luctus egestas. Aenean sed nisi tellus. Duis non ornare libero. Quisque suscipit maximus nisi, in gravida felis. Cras ornare mauris ac nisi congue, ut condimentum sem tincidunt. Phasellus semper tellus malesuada turpis gravida cursus. Duis nec eleifend nunc, vitae finibus elit. Aliquam eget diam vitae purus suscipit viverra.'
</script>

<template>
  <footer class="footer flex align-center justify-center ">
    <div class="container flex align-center justify-center flex-coll">
      <img class="img-footer" :src="logo">

      <p class="text-footer">{{ textFooter }}</p>

      <div class="links-footer">
        <ul class="flex">
          <li>Termos de Serviço</li>
          <li>Policita de Privacidade</li>
          <li>Trabalhe Conosco</li>
          <li>Contato</li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<style scoped>
@import '../styles/variables.css';

.footer{
  width: 100%;
  min-height: 31.1rem;
  background: var(--blue);
  color: #ffffff57;
  font-size: 1.4rem;
}
@media (max-width: 768px){
  .footer{
    padding: 1rem;
   
  }
}

@media (max-width: 768px){
  .text-footer{
    padding: 1rem;
    margin-bottom: 2rem;
  }
}

.img-footer{
  margin-bottom: 3.28rem;
}

.links-footer{
  width: 100%;
}
.links-footer > ul {
  list-style: none;
  margin-top: 2rem;
  color: #fff;
}

@media (max-width: 768px){
  .links-footer > ul{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}
.links-footer > ul > li {
 margin-right: 4.6rem;
}

@media (max-width: 768px){
  .links-footer > ul > li {
    margin-bottom: 2rem;
  }
}
</style>
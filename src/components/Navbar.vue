<template>
  <nav>
      <router-link to="/">
      <img src="@/assets/images/logo_potter.png" alt="Harrypotter">
      <img src="@/assets/images/HarryPotter.png" alt="HarryPotter">
      </router-link>
  </nav>
</template>

<script>
export default {
    name:'Navbar'
}
</script>

<style>
nav{
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 50px;
    background: #20232A;
    color: #61DAFB;
    width: 100vw;
    text-transform: uppercase;
}

nav img{
    margin: 10px 0;
    height: 40px;
    
}

@media screen and (min-width:540px){
    nav img{
    margin: 10px 0;
    height: 60px;
}
    
}
</style>
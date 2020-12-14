<template>
  <div id="app">
    <div id="nav">
      <Navbar/>
    </div>
    <router-view/>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar'
export default {
  name: 'Home',
  components: {
    Navbar
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  box-shadow: 0 2px 4px rgba(0, 0, 0, .1),0 8px 16px rgba(0, 0, 0, .1);
  background-color: #F0F2F5;
  min-height: 100vh;
}

*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

h1{
  text-transform: uppercase;
}

.mt-5{
  margin-top: 2rem;
}

.list {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: flex-start;
  min-width: 100%;
  padding: 10px;
}

.card {
  max-width: 100vw;
  flex: 0 0 calc(100% - 20px);  
  border: 1px solid rgb(226, 224, 224);
  background-color: #ffffff;
  padding: 3px;
  margin: 10px 10px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1), 0 8px 16px rgba(0, 0, 0, 0.1);
}

@media screen and (min-width:540px){
.card{
  max-width: 50vw;
  flex: 0 0 calc(50% - 20px);  
  border-radius: 4px;
}
}

@media screen and (min-width:768px){
  .card{
    max-width: 25vw;
    flex: 0 0 calc(25% - 20px);
    margin: 25px 10px;
    
    min-height: 200px;
    
  }
}

.card img {
  width: 100%;
  border-radius: 4px;
}

h2{
  text-transform: uppercase;
}

</style>



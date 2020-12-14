<template>
  <div >
    <div id="house">
      <div class="head mt-5">
        <h1>{{ house }}</h1>
        <div class="buscador">
          <label>Buscar personaje: </label>
          <input
            type="text"
            v-model="search"
            name="search"
            placeholder="Nombre o apellido..."
            autocomplete="off"
          />
        </div>
      </div>
      <div class="list">
        <div class="card animate__animated animate__fadeIn " v-for="item in filtered" :key="item.id">
          <img :src="item.image" alt="ShieldHouse" />
            <h2 class="mt-5">{{item.name}}</h2>
          <h3 >Blood purity:</h3>
          <span>{{ item.ancestry }}</span>
        </div>
      </div>
      <div v-if="filtered.length===0">
          <h2>No se econtraron personajes</h2>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      house: "",
      search: "",
      members: [],
      filtered: [],
      itemsSearch:['name']
    };
  },
  mounted() {
    this.house = this.$route.params.nameHouse;
    this.getMembers();
  },
  methods: {
    async getMembers() {
      try {
        const res = await axios.get(
          `http://hp-api.herokuapp.com/api/characters/house/${this.house}`
        );
        this.members = res.data;
        this.filtered = this.members;
      } catch (error) {
        console.log(error);
      }
    }
  },
watch: {
        search: function(val, oldVal) {
                this.filtered=this.members.filter(member=>
                    member.name.toUpperCase().includes(this.search.toUpperCase())  
                    //incluir los demas criterios de busqueda aqui
                    //por ejemplo para filtrar tambien por blood
                    // || member.ancestry.includes(this.search)
                    )
            }
            
        }
};
</script>

<style scoped>
#house {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

input {
  width: 230px;
  height: 40px;
  border: 2px solid rgb(233, 229, 229);
  font-size: 1.5rem;
  border-radius: 4px;
  -webkit-transition: width 0.4s ease-in-out;
  transition: width 0.4s ease-in-out;
}

.head {
  display: flex;
  justify-content: space-between;
  margin: 30px 20px;
  flex-wrap: wrap;
}

.buscador {
  font-size: 1.5rem;
}
</style>

<template>
  <div id="home">
    <div class="list">
      <div
        :class="{ 'animate__rotateOut': selected === item.id,'animate__fadeOutDown': selected && selected !== item.id, 'card animate__animated animate__fadeIn':true}"
        v-for="item in houses"
        :key="item.name"
        @click="handleSelect(item)"
      >
        <img :src="getPic(item.img)" alt="ShieldHouse" />
        <h2 class="mt-5">{{item.name}}</h2>
        <h3>Members: {{item.members}}</h3>
      </div>
    </div>
  </div>
</template>

<script>
const imgGrifindor = "logo_gryffindor";
const imgHufflepuff = "logo_hufflepuf";
const imgSlytherin = "logo_slytherin";
const imgRavenclaw = "logo_ravenclaw";

import axios from 'axios'
export default {
  name: "Home",
  data() {
    return {
      selected: null,
      houses: [
        { id: 1, name: "gryffindor", img: imgGrifindor,members:0 },
        { id: 2, name: "hufflepuff", img: imgHufflepuff,members:0 },
        { id: 3, name: "slytherin", img: imgSlytherin,members:0 },
        { id: 4, name: "ravenclaw", img: imgRavenclaw,members:0 },
      ],
    };
  },
  mounted() {
    this.countMembers();
  },
  methods: {
    getPic(pic) {
      return require("../assets/images/" + pic + ".png");
    },
    handleSelect(item) {
      this.selected=item.id;
      setTimeout(() => {
        this.$router.push(`/house/${item.name}`)
      }, 1000);
    },
    countMembers(){
      this.houses.map(async house=>{
        const res=await axios.get(`http://hp-api.herokuapp.com/api/characters/house/${house.name}`)
        house.members=res.data.length
      })
    }
  },
};
</script>

<style scoped>

.card:hover {
  transform: scale(1.05);
  cursor: pointer;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3), 0 8px 16px rgba(0, 0, 0, 0.3);
}


</style>

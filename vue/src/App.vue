<template>
  <div class="main-container">
    <MyHeader appName="Top Football Players"/> 
  <PlayersList :players=players />
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import PlayersList from './components/PlayersList.vue'


export default{
  name: 'App',

  components:{
    MyHeader,
    PlayersList
  },
  data(){
    return {
      players: []
    }
  },
  methods:{
    async fetchAllPlayers(){
      const res = await fetch('https://top-football-players-node.onrender.com/api');
      const data = await res.json()
      console.log(data.players)
      return data.players
    }
  },
  async created(){
      this.players = await this.fetchAllPlayers();
  }
}
</script>


<style>


@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Montserrat', sans-serif;
}
.main-container {
    background-color: #b1e8b6;
    color: black;
    padding: 1em;
    text-align: auto;
    width: 80%;
     margin: auto;
}
@media screen and (max-width: 476px) {
  .main-container {
        width: 100%;
    }
}
</style>

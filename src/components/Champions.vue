<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    NameChampData:
    <h6>{{ champion }}</h6>
    Data
    <div v-for="champion in champions" :key="champion.id">
      <h3>Name: {{ champion.name }}</h3>
      <h4>Attack Damage: {{ champion.attackDamage }}</h4>
      <hr>
    </div>
    <button @click="getChampions"> Get Champions </button>
     <button @click="getChampionByName"> Get Ashe </button>
    <hr>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Champions',
  data() {
    return {
      msg: 'Champs Elysee',
      champions: [],
      champion: {},
    };
  },

  methods : {
    async getChampions() {
      try {
        const res = await axios.post(
          'http://localhost:4000/graphql', {
            query: `{
              getChampions {
                name
                attackDamage
              }
            }`
        })
        this.champions = res.data.data.getChampions
      } catch (e) {
        console.log("err", e);
      }
    },
    async getChampionByName() {
      try {
        const res = await axios.post(
          'http://localhost:4000/graphql', {
            query: `{
              query getChampionByName($championName: String!) {
                getChampionByName(name: $championName)  {
                  name
                  attackDamage
                }
              }
            }`,
            variables: {
              championName: 'Ashe'
            }
        })
        log
        this.champion = res.data.data.getChampionByName
      } catch (e) {
        console.log("err", e);
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

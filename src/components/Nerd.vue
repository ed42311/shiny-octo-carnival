<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div v-for="member in team" :key="member.id">
      {{ `${member.name} is the ${member.title}` }}
    </div>
  </div>
</template>

<script>
const team = [
  {
    id: 1,
    name: 'johnny',
    title: 'duder',
  },
  {
    id: 2,
    name: 'suzie',
    title: 'master ninja',
  },
  {
    id: 3,
    name: 'bobbie',
    title: 'medic',
  },
];
export default {
  name: 'Nerd',
  data() {
    return {
      msg: 'Welcome Team!',
      team: team,
    };
  },
};
</script>

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

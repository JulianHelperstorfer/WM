<template>
  <!--<div id="Spielplan">
    <div v-for="groups in data">
      <div v-for="group in groups" class="group">
        {{ group.group }}
        {{ group.members }}
      </div>
    </div>
  </div>-->
  <div v-if="ready">
    <Header />

    <div v-if="error">
      {{ error }}
    </div>
    <div v-if="loading">
      <span>Loading...</span>
    </div>
    <div class="Gruppe">
      <h2>Teams:</h2>
      <div v-for="country in data.flags">
        <img :src="country.link" alt="flag" />
        {{ country.country }}
      </div>
      <h2>Gruppen:</h2>
      <div v-for="group in data.groups">
        <div class="groups">
          <h2>{{ group.group }}</h2>
          <div v-for="member in group.members" class="match">
            <span class="date">{{ member.date }} / {{ member.time }}</span>
            <br />
            {{ member.teams[0].team1 }} - {{ member.teams[1].team2 }} ({{
              member.teams[2].goals_team1
            }}
            : {{ member.teams[3].goals_team2 }})
          </div>
          <br />
        </div>
      </div>
    </div>

    <Footer />
  </div>
</template>

<script>
import { useFetch } from '../composable/UseFetch.js';
import Header from '../components/Header.vue';
import Footer from '../components/Footer.vue';

const prev = 0;
export default {
  name: 'Main',
  components: {
    Header,
    Footer,
  },
  async setup() {
    const { error, loading, ready, data } = useFetch(
      'https://raw.githubusercontent.com/htlWels/WM/main/spielplan.json',
      {}
    );

    function check(userId) {}

    console.log(data);

    return {
      data,
      error,
      loading,
      ready,
      prev,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
.group {
  border: 1px solid;
}
.groups {
  border: 2px solid black;
  margin: 2px;
}
.match {
  border: 1px solid black;
  margin: 2px;
}
.date {
  font-weight: bold;
}
</style>

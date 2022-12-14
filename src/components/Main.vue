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
      <!--<h2>Teams:</h2>
      <div v-for="country in data.flags">
        <img :src="country.link" alt="flag" />
        {{ country.country }}
      </div>-->
      <h2 id="title">Gruppen:</h2>
      <div v-for="group in data.groups">
        <div class="groups">
          <h2>{{ group.group }}</h2>
          <div v-for="member in group.members" class="match">
            <div class="date">{{ member.date }} / {{ member.time }}</div>
            <br />
            <div v-for="flag in data.flags">
              <div v-if="flag.country == member.teams[0].team1.toLowerCase()">
                <img :src="flag.link" alt="flag" class="teamOneImg" />
              </div>
            </div>
            <div class="teams">
              {{ member.teams[0].team1 }} - {{ member.teams[1].team2 }}
            </div>
            <div v-for="flag in data.flags">
              <div v-if="flag.country == member.teams[1].team2.toLowerCase()">
                <img :src="flag.link" alt="flag" class="teamTwoImg" />
              </div>
            </div>
            <div class="score">
              ({{ member.teams[2].goals_team1 }} :
              {{ member.teams[3].goals_team2 }})
            </div>
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
#title {
  color: #009900;
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
  width: 40%;
  margin: auto;
  background: url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTiRyiJi5dW2B5-64N5RFLvLTSCI_oPnLQySHreAwld918XLwmx30rrjzZSnpofnGhUTrw&usqp=CAU');
}
.match {
  border: 1px solid black;
  margin: 2px;
  text-align: center;
}
.date {
  font-weight: bold;
  width: 50%;
  margin: auto;
  padding-bottom: 5px;
  margin-top: 5px;
  margin-bottom: 0px;
  height: 8px;
}
.teamOneImg {
  float: left;
  position: relative;
  top: -5px; /* Move the element up by 20 pixels */
  margin-left: 10px;
}
.teamTwoImg {
  float: right;
  position: relative;
  top: -23px; /* Move the element up by 20 pixels */
  margin-right: 10px;
}
.teams {
  width: 50%;
  margin: auto;
}
.score {
  width: 50%;
  margin: auto;
}
</style>

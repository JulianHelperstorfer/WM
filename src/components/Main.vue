<template>
  <!--<div id="Spielplan">
    <div v-for="groups in data">
      <div v-for="group in groups" class="group">
        {{ group.group }}
        {{ group.members }}
      </div>
    </div>
  </div>-->

  <div v-for="(item, index) in data.flags" :key="index">
    {{ item }}
  </div>
</template>

<script>
import { useFetch } from '../composable/UseFetch.js';

const prev = 0;
export default {
  name: 'Main',
  async setup() {
    const { data, error, loading } = await useFetch(
      'https://raw.githubusercontent.com/htlWels/WM/main/spielplan.json',
      {'content-type': 'application/json'}
    );

    function check(userId) {}

    console.log(data);

    return {
      data,
      error,
      loading,
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
</style>

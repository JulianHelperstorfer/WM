<template>
  <div id="Spielplan">
    <tr v-for="groups in data">
      <td>{{ data.groups[0] }}</td>
    </tr>
  </div>
</template>

<script>
import { useFetch } from '../composable/UseFetch.js';

const prev = 0;
export default {
  name: 'Main',
  setup() {
    const { data, error, loading } = useFetch(
      'https://raw.githubusercontent.com/htlWels/WM/main/spielplan.json',
      {}
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
</style>

<template>
  <v-container fluid>
      <v-layout column align-center>
        <calculator/>
      </v-layout>
  </v-container>
</template>

<script>
import Calculator from "./Calculator";
export default {
  name: "MainLayout",
  props: {
    msg: String
  },
  components: {
    Calculator
  }
};
</script>

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

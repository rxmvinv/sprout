<template>
  <div class="final-result">
    K: {{result}}
  </div>
</template>

<script>
export default {
  name: 'FinalResult',
  props: {
    finalSolution: Number,
  },
  computed: {
    result: function () {
      return this.finalSolution;
    }
  },
  watch: {
    result: function () {
      console.log(this.result);
    },
    finalSolution: function () {
      console.log(this.finalSolution);
    }
  }
}
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

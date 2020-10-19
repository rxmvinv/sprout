<template>
  <div class="final-result" v-bind:class="{ active: result > 0 }">
    <label>K:</label>
    <div>{{result}}</div>
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
.final-result {
  color: #fff;
  display: flex;
  align-items: center;
}
label {
  margin-right: 4%;
  pointer-events: none;
  transition: .5s;
  user-select: none;
}
.final-result.active label {
  color: #03e9f4;
  font-size: 12px;
}
</style>

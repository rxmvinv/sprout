<template>
  <div class="decimal-field">
    D: 
    <input
      type="number" 
      step="0.01" 
      v-model="decimal" 
      v-on:change="$emit('insert-decimal', decimal)" 
    />
  </div>
</template>

<script>
export default {
  name: 'DecimalField',
  props: {
    decimalValue: Number
  },
  data () {
    return {
      decimal: 0.0,
      currentValue: this.decimalValue
    }
  },
  //float number validation goes here
}
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
.decimal-field {
  display: flex;
  justify-content: space-evenly;
  width: 50%;
  margin: auto;
  align-items: center;
  margin-bottom: 5%;
}
</style>

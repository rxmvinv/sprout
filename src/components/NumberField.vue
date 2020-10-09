<template>
  <div class="number-field">
    {{name}}: 
    <input 
      type="number" 
      step="1"
      min="0"
      pattern="[0-9]{10}"
      v-model="number" 
      v-on:change="$emit('insert-number', {id, number})" 
    />
  </div>
</template>

<script>
export default {
  name: 'NumberField',
  props: {
    val: Number,
    id: String,
    name: String
  },
  data () {
    return {
      number: 0,
      currentValue: this.val
    }
  }
  //Number validation on input goes here
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
.number-field {
  display: flex;
  justify-content: space-evenly;
  width: 50%;
  margin: auto;
  align-items: center;
  margin-bottom: 5%;m: 5%;
}
</style>

<template>
  <div class="number-field">
    <input 
      type="number" 
      step="1"
      min="0"
      pattern="[0-9]{10}"
      v-model="number" 
      v-bind:class="{ active: number > 0 }"
      v-on:change="$emit('insert-number', {id, number})"
    />
    <label>{{name}}: </label> 
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
.number-field {
  /*display: flex;
  justify-content: space-evenly;
  width: 50%;
  margin: auto;
  align-items: center;
  margin-bottom: 5%;*/
  position: relative;
  overflow: hidden;
}
input {
  width: 100%;
  margin-right: -15%;
  padding: 10px 0;
  font-size: 16px;
  color: #fff;
  margin-bottom: 30px;
  border: none;
  border-bottom: 1px solid #fff;
  outline: none;
  background: transparent;
}
label {
  position: absolute;
  top: 0px;
  left: 0;
  padding: 10px 0;
  font-size: 16px;
  color: #fff;
  pointer-events: none;
  user-select: none;
  transition: .5s;
}
input:focus ~ label,
input.active ~ label {
  left: 0;
  color: #03e9f4;
  font-size: 12px;
}
</style>

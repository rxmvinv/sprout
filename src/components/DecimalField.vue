<template>
  <div class="decimal-field">
    <input
      type="number" 
      step="0.01" 
      v-model="decimal" 
      v-bind:class="{ active: decimal > 0 }"
      v-on:change="$emit('insert-decimal', decimal)" 
    />
    <label>D: </label>
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
.decimal-field {
  position: relative;
  overflow: hidden;
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

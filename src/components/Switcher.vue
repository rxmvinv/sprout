<template>
  <div class="switcher-wrapper">
    {{name}}:
    <div 
      class="switcher" 
      v-bind:class="{ active: active }"
      v-on:click="$emit('switch-action', id)"
    >
      <div class="switcher-pin"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Switcher',
  props: {
    id: Number,
    active: Boolean,
    name: String
  },
  data () {
    return {
      isActive: this.active
    }
  }
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
.switcher-wrapper {
  display: flex;
  justify-content: space-evenly;
  width: 50%;
  margin: auto;
  align-items: center;
  margin-bottom: 5%;
}
.switcher {
  display: flex;
  background: lightgreen;
  border: 3px solid darkgreen;
  border-radius: 12px;
  position: relative;
  height: 20px;
  width: 100px;
}

.switcher-pin {
  display: flex;
  position: absolute;
  height: 100%;
  background: green;
  border-radius: 12px;
  width: 50%;
  -webkit-animation: switchTransitionLeft 0.3s ease-in-out forwards;
  animation: switchTransitionLeft 0.3s ease-in-out forwards;
}

@keyframes switchTransitionRight {
  0% { left: 0; background: lightsteelblue; }
  100% { left: 50%; background: green; }
}

@-webkit-keyframes switchTransitionRight {
  0% { left: 0; background: lightsteelblue; }
  100% { left: 50%; background: green; }
}

@keyframes switchTransitionLeft {
  0% { left: 50%; background: green; }
  100% { left: 0; background: lightsteelblue;  }
}

@-webkit-keyframes switchTransitionLeft {
  0% { left: 50%; background: green; }
  100% { left: 0; background: lightsteelblue; }
}

.active .switcher-pin {
  -webkit-animation: switchTransitionRight 0.3s ease-in-out forwards;
  animation: switchTransitionRight 0.3s ease-in-out forwards;
}

</style>

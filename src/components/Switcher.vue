<template>
  <div class="switcher-wrapper">
    <div 
      class="switcher" 
      v-bind:class="{ active: active }"
      v-on:click="$emit('switch-action', id)"
    >
      <div class="switcher-pin"></div>
    </div>
    <label>{{name}}:</label>
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
  flex-direction: row-reverse;
  justify-content: space-between;
  width: 100%;
  margin: auto;
  align-items: center;
  margin-bottom: 5%;
  color: #fff;
}
.switcher {
  display: flex;
  background: transparent;
  border: 3px solid #03e9f4;
  border-radius: 12px;
  position: relative;
  height: 20px;
  width: 100px;
  margin: auto;
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
  0% { left: 0; background: #03e9f4; box-shadow: none; }
  100% { 
    left: 50%; 
    background: #03e9f4;
    color: #fff;
    box-shadow: 0 0 5px #03e9f4,
                0 0 25px #03e9f4,
                0 0 50px #03e9f4,
                0 0 100px #03e9f4; 
  }
}

@-webkit-keyframes switchTransitionRight {
  0% { left: 0; background: #03e9f4; box-shadow: none; }
  100% { 
    left: 50%; 
    background: #03e9f4;
    color: #fff;
    box-shadow: 0 0 5px #03e9f4,
                0 0 25px #03e9f4,
                0 0 50px #03e9f4,
                0 0 100px #03e9f4; 
  }
}

@keyframes switchTransitionLeft {
  0% { 
    left: 50%; 
    background: #03e9f4;
    color: #fff;
    box-shadow: 0 0 5px #03e9f4,
                0 0 25px #03e9f4,
                0 0 50px #03e9f4,
                0 0 100px #03e9f4; 
  }
  100% { left: 0; background: #03e9f4; box-shadow: none;  }
}

@-webkit-keyframes switchTransitionLeft {
  0% { 
    left: 50%; 
    background: #03e9f4;
    color: #fff;
    box-shadow: 0 0 5px #03e9f4,
                0 0 25px #03e9f4,
                0 0 50px #03e9f4,
                0 0 100px #03e9f4; 
  }
  100% { left: 0; background: #03e9f4; box-shadow: none; }
}

.active .switcher-pin {
  -webkit-animation: switchTransitionRight 0.3s ease-in-out forwards;
  animation: switchTransitionRight 0.3s ease-in-out forwards;
}

label {
  font-size: 16px;
  color: #fff;
  pointer-events: none;
  user-select: none;
  transition: .5s;
}

.switcher.active ~ label {
  color: #03e9f4;
  font-size: 12px;
}
</style>

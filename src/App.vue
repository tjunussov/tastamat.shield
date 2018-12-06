<template>
  <div id="app">
    <div class="notprint hint">
       132mm X 218mm
       <button @click="num++">Add</button>
       <button @click="remove">Remove</button>
       <button @click="outline=!outline">Outline</button>
       <button @click="compact=!compact">Compact</button>
       <button @click="index=!index">Index</button>
    </div>
    <Shield v-bind:class="{'outline':outline,compact,index}" v-for="i in num" :no="i" :key="i"/>
  </div>
</template>

<script>
import Shield from './components/Shield'

export default {
  name: 'App',
   data () {
    return {
      num: 1,
      outline:true,
      index:false,
      compact:false
    }
  },
  methods:{
    remove(){
      if(this.num > 1) this.num--
    }
  },
  components: {
    Shield
  }
}
</script>

<style>

@page {
  size: 'A4';
  margin: 0;
  /*size: landscape;*/
}

@font-face {
  font-family: 'NSP';
  src: url('/static/font/subset-NeoSansPro-Bold.woff2') format('woff2');
  font-weight: bold;
  font-style: normal;
}


@font-face {
  font-family: 'NSP';
  src: url('/static/font/subset-NeoSansPro-Regular.woff2') format('woff2');
  font-weight: normal;
  font-style: normal;
}


#app {
  font-family: 'NSP', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #000;
}

@media print{
   .notprint {
       display:none;
   }
}

.hint {
  position: absolute;
  top:1rem;
  right: 1rem;
}

.hint button {
  border:1px solid #ccc;
  width: 5rem;
  font-family: inherit;
}


</style>

<template>
  <div class="shield" :no="no">
    <img class="logo" src="static/logo.svg"/>
    <div class="qr"><qr :value="name" prefix="WWW.2QR.KZ/"/></div>
    <div class="label">
      <input type="text" autofocus="autofocus" maxlength="9" v-model="name"/>
    </div>
    <input class="address"  maxlength="30" v-model="address"/>
    <div class="copyright">Подробная информация на сайте 
      <b>tastamat.kz/{{name}}</b>
      <br>©2018 Все права защищены ТОО TOOLPAR
    </div>
  </div>
</template>

<script>

import QR from '@/components/QR2'

export default {
  name: 'Shield',
  props:['no'],
  watch:{
    name(val){
      if(val) this.name = val.toUpperCase();
    }
  },
  data () {
    return {
      name: 'ESENTAI',
      address: 'БЦ Аффари, ул. Мамбетова 24'
    }
  },
  components: {
    qr:QR
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .shield {
    width: 132mm;
    /*height: 214mm;*/
    max-height: 218mm;
    margin:1rem; 
    padding: 2.7rem 4.5rem;
    box-sizing: border-box;
    text-align: center;
    border:1px dotted transparent;
    border-radius: 1.5rem;
    font-family: inherit;
    display: inline-block;
    page-break-before:always;
    position: relative;
   
  }

  .shield.outline {
     border-color:#ccc;
  }

/*  .shield:before {
    content:'';
    background: url('/static/sample.png') no-repeat;
    background-size: cover;
    position: absolute;
    left:0;
    top:0;
    bottom: 0;
    right: 0;
    z-index: 100;
    opacity: 0.5;
  }

*/


@media print{
  .shield { margin: 0; }

  .shield:after {
       display:none;
  }
}

  .shield:after {
    content:attr(no);
    position: absolute;
    left: 1rem;
    font-size: 2em;
    top:1em;
    color: #ccc;
  }

  .logo {
    width: 23em;
    margin-bottom: 2rem;
  }


  .shield.outline .qr {
    border-top-color:#ccc;
    border-bottom-color:#ccc;
  }

  .shield.compact .qr {
    padding: 0.2rem 0 !important;
  }

  .qr {
    width: 20.5rem;
    margin: 0 auto;
    padding: 2rem 0;
    border-top:1px dashed transparent;
    border-bottom:1px dashed transparent;
  }

  .label {
    margin-top: 2rem;
    background-color: #00afef;
    border-radius: 1.5rem;
    box-sizing: border-box;
    padding:0.3rem;
    position: relative;
  }

  .label *  {
    font:bold 4.2rem 'NSP';
    text-align: center;
    vertical-align: text-top;
    color: #fff;
    width: 100%;
    border:none;
    letter-spacing: -1px;
    outline: none;
    background-color: transparent;
  }

  .address {
    margin:1.2rem -2rem 0 -2rem;
    font-size: 1.7rem;
    font-weight: bold;
    font-family: inherit;
    padding: 0;
    width: 110%;
    text-align: inherit;
    letter-spacing: -1px;
    border:none;
  }

  .copyright {
    font-size: 0.6rem; 
    margin-top:1.2rem;
    text-align: left;
    line-height: 0.9rem;
  }

  .copyright b {
    text-decoration: underline;
  }
/*
  .label,.address,.copyright  {
    outline:1px solid #ccc;
  }*/

</style>

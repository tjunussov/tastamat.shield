<template>
<div v-html="dots"></div>
</template>

<script>
import QRCode from 'qrcode'

export default {
  name: 'QR',
  props:{
    value:{
      required:true,
    },
    fill:{
      default:"#ffffff"
    },
    prefix:{
      required:false
    }
  },
  computed:{
    length(){
      return this.dots.length
    }
  },
  data () {
    return {
      dots:null
    }
  },
  watch:{
    value(){
      this.encode()
    }
  },
  mounted(){
    // console.log('mouted qr',this.value);
    if(this.value) this.encode()
  },
  methods:{
    encode(){
      QRCode.toString((this.prefix?this.prefix:'')+String(this.value),{ 
        version: 1,
        errorCorrectionLevel: 'M',
        // maskPattern:null, // auto,
        margin:0,
      },(err,txt)=>{
        this.dots = txt;
      });
    }
  }
}


</script>
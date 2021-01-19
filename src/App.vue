<template>
  <div id="app">
    App.vue我现在有{{total}}
  <hr>
  <!-- <Child :money="total"  v-on:updata:money='total=$event'/> -->
  <Child :money.sync="total"/>
  </div>
</template>

<script>
import Child from './child.vue'

export default {
 data(){
   return {total:10000}
 },
 components:{Child}
}

</script>

<style >
  #app{
    border: 3px solid red;
    padding: 10px;
  }
</style>

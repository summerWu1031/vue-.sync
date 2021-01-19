## Vue 中的 .sync 修饰符有什么用
* vue 修饰符sync的功能是：当一个子组件改变了一个 prop 的值时，这个变化也会同步到父组件中所绑定。
* .sync其实是个语法糖
* * $emit('update:money',money-100)触发update:money事件和并把money-100参数传给$event
* * v-on:updata:money='total=$event' ,$event会接受$emit传过来的参数
* * 
   ```
  <Child :money.sync="total"/>等价于
  <Child:money="total"v-on:updata:money='total=$event'/> 
   ```

```vue
<template>
    <div class="child">
        {{money}}
        <button @click="$emit('update:money',money-100)">
            <span>花钱</span>
        </button>
    </div>
</template>

<script>
export default {
    props:["money"]
}
</script>
```
<br>

```vue
<template>
  <div id="app">
    App.vue我现在有{{total}}
  <hr>
  <!-- <Child :money="total"  v-on:updata:money='total=$event'/> 等价于下一行代码-->
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
```
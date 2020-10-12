<template>
 <div>
  {{state.list.b.b1}}
  <button @click="handleAdd">按钮</button>
 </div>

</template>

<script>
import { readonly,shallowReadonly,isReadonly } from 'vue'
export default {
  name: 'App',
  setup() {
    // let state = readonly({
    //   list:{
    //     a:'1111',
    //     b:{
    //       b1:"2222",
    //       c:{
    //         c2:"3333"
    //       }
    //     }
    //   }
    // })
    let state = shallowReadonly({
      list:{
        a:'1111',
        b:{
          b1:"2222",
          c:{
            c2:"3333"
          }
        }
      }
    })
    function handleAdd() {
      state.list= '3333333333'
         console.log(state)
    }
    return {state,handleAdd}
  }
}
</script>


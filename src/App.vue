<template>
 <div>
  <!-- {{state.name}} -->
  <button @click="handleAdd">按钮</button>
 </div>

</template>

<script>

export default {
  name: 'App',
  setup() {
    let obj = {
      name:"1111",
      age:19,
      info:{
        bb:"55555"
      }
    }
  
     let state = _shallowReadonly(obj)
    function  handleAdd(){
     state.name = '222'
    //  state.info.bb = '123123'
    }
    return {state,handleAdd}
  }
}

function _shallowReadonly(obj){
  return new Proxy(obj,{
    get(obj,prop){
      return obj[prop]
    },
    set(obj,prop,value){
      console.warn("不能修改")
      return true
        // obj[prop] = value 
        // console.log("更新ui界面")
        // console.log(obj)
        // return true
    }
  })
}

</script>




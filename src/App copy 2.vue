<template>
 <div>
  {{state.name}}
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
    // let state = _shallowreactive(obj)
    // function  handleAdd(){
    //   state.name ='fghhrt'
    //   state.info.bb ='bdfgsfsd'
    // }
     let state = _shallowref(obj)
    function  handleAdd(){
     state.value = '222'
    }
    return {state,handleAdd}
  }
}

function _shallowreactive(obj){
  return new Proxy(obj,{
    get(obj,prop){
      return obj[prop]
    },
    set(obj,prop,value){
        obj[prop] = value 
        console.log("更新ui界面")
        console.log(obj)
        return true
    }
  })
}

function _shallowref(val) {
  return  _shallowreactive({value:val})
}
</script>




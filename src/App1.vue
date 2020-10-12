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
    let state = _reactive(obj)
    function  handleAdd(){
      state.name = '444444'
     state.info.bb = '222'
    }
    return {state,handleAdd}
  }
}

function _reactive(obj){
   if(typeof obj === 'object'){
     if(obj instanceof Array){
      //  如果是数组，取出遍历
       obj.forEach((item,index)=>{
        //   如果数组里面的值是还是对此安好
         if(typeof item === 'object'){
           obj[index] = _reactive(item)
         }
       })
     }else{
       // 如果是对象
       for(let key in obj){
         let item = obj[key]
          if(typeof item === 'object'){
           obj[key] = _reactive(item)
         }
       }
     }

   }else{
     console.warn("不是对象")
   }



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

</script>




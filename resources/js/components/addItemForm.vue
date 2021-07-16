<template>
  <div class="addItem">
      <input type="text" class="input" placeholder="Add Todo" v-model="item.name">
      <button class="addButton">
          <font-awesome-icon icon="plus" class="plus"  @click="additem"/>
      </button>
  </div>
</template>

<script>
export default {
    data: function(){
        return{
            item:{
                name:""
            }
        }
    },
    methods:{
        additem(){
            if(this.item.name !== ''){
                axios.post('api/todo/store',{
                    todo: this.item.name
                }).then(response => {
                    if(response.status >= 200 && response.status <300){
                        this.item.name=null
                    }
                })
            }
        }
    }
}
</script>

<style>
    .additem{
        display: flex;
        justify-content: center;
        align-items: center;
        margin-bottom: 25px;
    }
    .input{
        border-style: solid;
        border-color: blue;
        border-bottom-right-radius: 4px;
        border-top-right-radius: 4px;
        border-width: 1px;
        outline: none;
        padding: 5px;
        height: 30px;
        width: 100%;
    }
    .addButton{
        height: 42px;
        width: 42px;
        border-style: solid;
        border-color:blue;
        border-bottom-right-radius: 4px;
        border-top-right-radius: 4px;
        border-width: 1px;
        background-color:white ;
    }
    .plus{
        font-size:20px;
        color:blue;
    }
</style>
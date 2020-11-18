<template>
  <section>
    <transition-group name="list" tag="ul">
      <li v-for="(todoItem , index) in propsdata" :key="todoItem" class="shadow">
        <i class="checkBtn fas fa-check" aria-hidden="true"></i>
        {{ todoItem }}
        <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
          <i class="far fa-trash-alt" aria-hidden="true"></i>
        </span>
      </li>
    </transition-group>
  </section>
</template>

<script>
  export default{

    props: ['propsdata'],
    methods:{
      removeTodo(todoItem,index){
        console.log(todoItem,index);
        //localStorage.removeItem(todoItem);
        //this.todoItems.splice(index,1);
        this.$emit('removeTodo',todoItem,index);
      }
    }
    /* App.vue 로 이동
    data(){
      return {
        todoItems : []
      }
    },
    created(){
      // life cycle 생성 시점에 localStorage가 0이 아닐때 todoTiems(배열)에 data push
      if(localStorage.length > 0){
        for(var i = 0 ; i < localStorage.length; i++){
          // index 순서대로 data push
          this.todoItems.push(localStorage.key(i));
        }
      }
    }
    */
    
  
  }

  

</script>

<style scoped>
  ul {
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
  }

  li{
    display: flex;
    min-height: 50px;
    height:50px;
    line-height: 50px;
    margin:0.5rem 0;
    padding:0 0.9rem;
    background: white;
    border-radius: 5px;
  }

  .checkBtn{
    line-height: 45px;
    color : #62acde;
    margin-right: 5px;
  }

  .removeBtn{
    margin-left: auto;
    color:#de4343;
  }

  .list-enter-active, .list-leave-active{
    transition: all 1s;
  }

  .list-enter, .list-leave-to {
    opacity: 0;
    transform: translate(30px);
  }

</style>

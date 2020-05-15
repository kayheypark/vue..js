<template>
  <div id="app">
    <!-- 컴포넌트이름 -->
  <TodoHeader></TodoHeader>
  <TodoInput v-on:addTodoE="addTodoA"></TodoInput>
  <TodoList v-bind:propsdata="todoItems" v-on:removeTodoE="removeTodoA"></TodoList>
  <TodoFooter v-on:removeAllE="clearAllA"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'
//import 컴포넌트내용객체 from
export default {
  name: 'app',
  data () {
    return {
      todoItems:[]
    }
  },

  methods:{
    addTodoA(todoItem){
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    removeTodoA(todoItem, index){
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    clearAllA(){
      localStorage.clear();
      this.todoItems=[];

    }

  },

  created(){
    if(localStorage.length>0){
        for(var i=0;i<localStorage.length;i++){
            this.todoItems.push(localStorage.key(i));
        }
    }

},

  components:{
    'TodoHeader':TodoHeader,
    'TodoInput':TodoInput,
    'TodoList':TodoList,
    'TodoFooter':TodoFooter
    //'컴포넌트 이름':컴포넌트 내용객체
  }
}
</script>


<style>
body {text-align: center; background: #f6f6f6;}
input {border-style: groove; width: 200px;}
button {border-style: groove;}
.shadow {box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);}
</style>

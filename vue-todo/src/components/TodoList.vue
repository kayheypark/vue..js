<template>
<section>
    <ul>
        <li v-for="(todoItem,index) in propsdata" v-bind:key="todoItem"> <!-- :key  =  v-bind:key -->
        <span class="checkBtn" type="button">
        <i class="fas fa-check"></i>
        </span>
        {{ todoItem }}
        <span class="removeBtn" type="button" @click="removeTodo(todoItem,index)">
            <i class="fas fa-trash-alt"></i>
        </span>
        </li>
    </ul>
</section>
</template>

<script>
export default {
    props:['propsdata'], // props속성:['속성이름']

    methods:{
        removeTodo(todoItem,index){
           // console.log(todoItem,index);
           this.$emit('removeTodoE', todoItem, index);
            //localStorage.removeItem(todoItem);
            //this.todoItems.splice(index,1); // .splice()배열의 특정 인덱스에서 부여한 숫자만큼의 인덱스를 삭제
        }
    }
}
</script>

<style scoped>
ul {list-style: none; padding-left:0;  margin-top: 0; text-align:center;}
li {display: flex; min-height: 50px; height: 50px; line-height: 50px;
    margin:0.5rem; padding: 0 0.9rem;background: #fff; border-radius: 5px;}
.checkBtn {line-height: 45px; color: #62acde; margin-right: 5px;}
.removeBtn {margin-left: auto; color: #de4343;}
</style>
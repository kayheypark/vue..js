<template>
<div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" placeholder="할일을 입력하세요!" v-on:keypress.enter="addTodo" />
    <span class="addContanier" v-on:click="addTodo">
        <i class="fas fa-plus-square"></i>
    </span>
</div>
</template>

<script>
export default {
    data(){
        return{
            newTodoItem:''
        }
    },
    methods:{
        addTodo(){
            if(this.newTodoItem !== ""){
                 var value = this.newTodoItem && this.newTodoItem.trim();
                //localStorage.setItem(value, value);
                this.$emit('addTodoE',value);
                //부모한테 이벤트 전달 this.$emit('이벤트 이름','전달하는 값')
                this.clearInput(); //디자인 패턴:단일 책임 원칙-함수 하나가 기능만 담당하도록 설게하는 재향 프그래밍의 디자인

            }
        },
        clearInput(){
            this.newTodoItem="";
        }
    }
}
</script>

<style scoped>
input:focus{outline: none;}
div.inputBox{background: #fff; height: 50px; line-height: 50px; border-radius: 5px;}
div.inputBox input {border-style: none; font-size: 0.9rem;}
span.addContanier {float: right; background: linear-gradient(to right, #6478fb, #8763fb);
                    display: inline-block; width: 3rem; border-radius: 0 5px 5px 0;}
span.addContanier i {color: #fff;}
</style>
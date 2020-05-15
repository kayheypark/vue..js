<template>
<div class="clearAllContainer">
    <span class="clearAllBtn" @click="clearTodoA">Clear All</span>
</div>
</template>

<script>
export default {
        methods:{
            clearTodoA (){
                //localStorage.clear();
                this.$emit('removeAllE');
            }
        }
}
</script>

<style scoped>
div.clearAllContainer {width: 8.5rem; height:50px; line-height: 50px; background: #fff;
                        border-radius: 5px; margin: 0 auto;}
span.clearAllBtn {color:#e20303; display: block;}
</style>
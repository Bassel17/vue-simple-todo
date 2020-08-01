<template>
    <div>
        <input type="text" v-model="title" name="title"/>
        <button @click="addTodo">add</button>
    </div>
</template>

<script>
export default {
    name:"AddTodo",
    data(){
        return {
            title:""
        }
    },
    methods:{
        addTodo(){
            this.$emit('add-todo',this.title);
            this.title="";
        }
    }
}
</script>

<style scoped>
    div{
        display:flex;
    }

    input{
        padding:1em;
        width: 100%;
    }

    button{
        width: 4em;
    }
</style>
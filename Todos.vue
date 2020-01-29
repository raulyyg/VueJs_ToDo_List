<!--Raul Garcia-->
<!-- Credit: Traversy Media: Vue JS Crash Course-->

<template>
<!--Root element --> 
    <div>
        <!--vfor directive call fist todo whatever but will pass second todo for the props
        that it pertains in..... eslint err: needs unique key use vbind
        with unique value and unique id-->
        <div v-bind:key="todo.id" v-for="todo in todos"> 
           <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
           <!--for each iteration we have access to the indiviudal todo
           and we're passing it into the todo item-->
        </div>
    </div>
</template>

<script>

import TodoItem from './TodoItem.vue';

export default {
    //component name
    name: "Todos",
    components: {
        TodoItem
    },
    props: ["todos"] //access on template, from array
}
</script>  

<style scoped>

</style>



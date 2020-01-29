<!--Raul Garcia-->
<!-- Credit: Traversy Media: Vue JS Crash Course-->

<template>
<!-- bind class on a condition for line trhough for css "is-completed" class -->
    <div class ="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p>
            <!-- Add event... v-on directive for method mark complete-->
            <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed">
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" class="del">x</button>
            </p>
    </div>
</template>

<script>
export default { 
    name: "TodoItem",
    props: ["todo"],
    methods: {
        //this fires off checkbox as complete
        markComplete() {   //from v-on directive
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
    .todo-item {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }
    .is-complete {
        text-decoration: line-through;
    }

    .del {
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>
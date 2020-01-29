<!--Raul Garcia-->
<!-- Credit: Traversy Media: Vue JS Crash Course-->

<template>
    <div>
        <form @submi.prevent="addTodo"> 
            <input type="text" v-model="title" name= "title" placeholder="Add
            Todo...">
            <input type="Submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
//import uuid from 'uuid';
export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo() {
           // e.preventDefault(); //stop default behavior and emit behavior and call func
            const newTodo = {
               // id: uuid.v4(),
                title: this.title,
                completed: false
            }
            //Send up to parent
            this.$emit('add-todo', newTodo);

            this.title = '';
        }
    }
}

</script>

<style  scoped>

    form{
        display: flex;
    }

    input[type="text"]{
        flex: 10;
        padding: 5px;
    }

    input[type="submit"]{
        flex: 2;
    }

</style>

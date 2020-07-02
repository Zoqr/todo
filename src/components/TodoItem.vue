<template>
    <li>
        <span v-bind:class="{done: todo.completed}">

            <input  type="checkbox" v-on:change="todo.completed = !todo.completed">
            <span class="fake"></span>
            <span v-if="!editable" @click.passive="show">{{todo.title}}</span>
            <input type="text" v-if="editable" v-model="todo.title" @keypress.enter="hide" @blur="hide">

          </span>
        <button class="remove"
                v-on:click="$emit('remove-todo', todo.id)"
        >&#10006;
        </button>

    </li>
</template>

<script>
    export default {
        props: {
            todo: {
                type: Object,
                required: true
            }

        },
        data() {
            return {
                editable: false
            }
        },
        methods: {
            show() {
                console.log(true)
                this.editable = true;
            },
            hide() {
                console.log(false)
                this.editable = false;
            },

        },

        name: "TodoItem"
    }
</script>

<style scoped>
    li {
        display: flex;
        justify-content: space-between;
        padding: 10px;
        width: 655px;
        border-color: transparent;
        border-radius: 2px;

    }
    li:active {
        border-bottom: 2px solid blue;
    }

    .remove {
        background: #ffffff;
        color: red;
        border-radius: 50%;
        font-weight: bold;
        border-color: transparent;
        margin-right: 10px;


    }

    input {
        margin-right: 1rem;
        border-color: #8E8A8A;
    }

    /*.done {*/
    /*    text-decoration: line-through;*/
    /*}*/
     input[type=checkbox] {
         display: inline-block;
         width: 1.2em;
         height: 1.2em;
         margin-right: 10px;

    }









</style>
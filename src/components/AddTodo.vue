<template>
    <form @submit.prevent="onSubmit">

        <fieldset>
            <legend align="left">task</legend>
            <input type="text" v-model="title">
        </fieldset>

        <button type="=submit">ADD</button>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                title: ''
            }
        },
        methods: {
            onSubmit() {
                console.log(this.title)
                if (this.title.trim()) {
                    const newTodo = {
                        id: Date.now(),
                        title: this.title,
                        completed: false
                    }
                    this.$emit('add-todo', newTodo)
                    this.title = ''
                }

            }
        },
        name: "AddTodo"
    }
</script>

<style scoped>
    form {
        display: flex;

    }
    input {
        width: 537px;
        height: 40px;
        border-color: transparent;
    }


    button {
        margin-left: 10px;
        width: 110px;
        background-color: white;
        color: #7CFC00;
        border: 2px solid #7CFC00;
        border-radius: 4px;
        transition-duration: 0.4s;
    }
    button:hover {
        background-color: #7CFC00;
        color: white;
    }
    legend {
        margin: 0;
        padding: 0;
    }

</style>
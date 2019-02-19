<template>
    <div ref='main' id='main'>
        <div id="headText">
            <h1>{{ titleText }}</h1>
        </div>
        <DataInput @commitTodoItem='pushTodoItem'></DataInput>
        <Todo :todoList='todoList' @todoToDoneEmit='pushDoneItem'></Todo>
        <Done :doneList='doneList' @doneEmit='donePop'></Done>
    </div>
</template>

<script>
    import DataInput from './DataInput'
    import Todo from './Todo'
    import Done from './Done'

    export default {
        name: "Main",
        data: function () {
            return {
                'titleText': "TodoList",
                'todoList': [],
                'doneList': []
            }
        },
        methods: {
            pushTodoItem: function (v) {
                this.todoList.push(v);
            },
            pushDoneItem: function (v, k) {
                this.todoList.splice(k, 1);
                this.doneList.push({
                    'id': v.id,
                    'info': v.info
                });
            },
            donePop: function (k) {
                this.doneList.splice(k, 1);
            }
        },
        components: {
            DataInput,
            Todo,
            Done
        }
    }
</script>

<style scoped>
    #main {
        text-align: left;
    }
</style>
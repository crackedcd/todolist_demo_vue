<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
    <div ref='main' id='main'>
        <Title titleContent="whiteBus">
            <!--            https://cn.vuejs.org/v2/guide/components-slots.html-->
            <template v-slot:w="wProps">{{ wProps.wSlot }}</template>
        </Title>
        <Title titleContent="blackBus">
            <template v-slot:b="bProps">{{ bProps.bSlot }}</template>
        </Title>

        <div id="headText">
            <h1>{{ titleText }}</h1>
        </div>

        <div id="onceTitle">
            <Once :btnType="btnType"></Once>
            <button @click="changeOnceTitle">change</button>
        </div>

        <DataInput @commitTodoItem='pushTodoItem'></DataInput>
        <Todo :todoList='todoList' @todoToDoneEmit='pushDoneItem'></Todo>
        <Done :doneList='doneList' @doneEmit='donePop'></Done>

    </div>
</template>

<script>
    import Title from './Title'
    import DataInput from './DataInput'
    import Todo from './Todo'
    import Done from './Done'
    import Once from './Once'

    export default {
        name: "Main",
        data: function () {
            return {
                'titleText': "TodoList",
                'todoList': [],
                'doneList': [],
                'btnType': ''
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
            },
            changeOnceTitle: function () {
                this.btnType = this.btnType === 'white' ? 'black' : 'white';
                console.log(this.btnType);
            }
        },
        components: {
            Title,
            DataInput,
            Todo,
            Done,
            Once
        }
    }
</script>

<style scoped>
    #main {
        text-align: left;
    }
</style>
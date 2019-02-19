<template xmlns:v-for="http://www.w3.org/1999/xhtml">
    <div id="todoList">
        <div id="todoListHeadText">
            {{ todoTitleText }}
        </div>
        <div id="todoListBody">
            <ul>
                <li v-for='(v, k) of this.todoList'
                    :key='v.id'
                    @click='todoClick(v, k)'
                >
                    {{ v.info }}
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Todo",
        props: [
            'todoList'
        ],
        data: function () {
            return {
                'todoTitleText': 'TodoList',
                'm': this.todoList
            }
        },
        methods: {
            todoClick: function (v, k) {
                this.$emit('todoToDoneEmit', v, k);
            }
        },
        template: {}
    }
</script>

<style scoped>

</style>
<template>
    <div id='dataInput'>
        <p>
        <input type="text" v-model="inputVal" placeholder="add todo item"/>
        <button v-on:click="btnClick">commit</button>
        </p>
    </div>
</template>

<script>
    export default {
        name: "DataInput",
        data: function () {
            return {
                'inputVal': ''
            }
        },
        methods: {
            btnClick: function () {
                this.$emit('commitTodoItem', {
                    'id': Math.random().toString(36).substr(2),
                    'info': this.inputVal
                });
                this.inputVal = '';
            }
        }
    }
</script>

<style scoped>

</style>
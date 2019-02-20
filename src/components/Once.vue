<template>
    <div id="changeText">
<!--        用v-once, 只生成一次, 不销毁, 放在内存里-->
        <div v-once v-if="type === 'white'">This is white</div>
        <div v-once v-if="type === 'black'">This is black</div>
    </div>
</template>

<script>

    export default {
        name: "Once",
        props: ['btnType'],
        computed: {
            'type': function () {
                return this.btnType;
            }
        },
        methods: {
        }
    }
</script>

<style scoped>

</style>